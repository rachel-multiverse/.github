# Rachel Multiverse CI/CD Usage Guide

## How the Build System Works

### 1. Automatic Builds (On Push)

Whenever you push changes to any platform repository, the workflow automatically triggers:

```bash
# Example: Working on the NES platform
cd ~/Projects/rachel-nes
# Make your changes to rachel.asm
git add .
git commit -m "Improve sprite rendering"
git push

# The workflow automatically:
# 1. Detects the push
# 2. Sets up NES toolchain (cc65)
# 3. Builds the ROM
# 4. Uploads rachel.nes as artifact
# 5. Creates build report
```

### 2. Manual Builds (Workflow Dispatch)

You can manually trigger builds from GitHub's web interface:

1. Go to the organization `.github` repository
2. Click "Actions" tab
3. Select "Build Rachel Multiverse"
4. Click "Run workflow"
5. Choose platforms:
   - Leave as "all" to build everything
   - Or specify: "dos,c64,gameboy"

### 3. Downloading Build Artifacts

After builds complete:

```bash
# Using GitHub CLI
gh run download --repo rachel-multiverse/.github

# Or from the web:
# 1. Go to Actions tab
# 2. Click on the workflow run
# 3. Scroll to "Artifacts"
# 4. Download the platform you want
```

### 4. Local Development with Docker

For consistent local builds matching CI:

```bash
# Clone the Docker configs
git clone https://github.com/rachel-multiverse/.github
cd .github/docker

# Build a toolchain container
docker build -t rachel-6502 base-6502/
docker build -t rachel-nes toolchain-nes/

# Use it to build locally
docker run -v ~/Projects/rachel-nes:/workspace rachel-nes make

# Or interactively for development
docker run -it -v ~/Projects/rachel-nes:/workspace rachel-nes bash
```

### 5. Creating a New Platform

When adding platform #10 (NES):

```bash
# 1. Create the repository
gh repo create rachel-multiverse/rachel-nes --public \
  --description "Rachel for NES/Famicom - Platform #010"

# 2. Clone and set up
git clone https://github.com/rachel-multiverse/rachel-nes
cd rachel-nes

# 3. Copy core rules
cp ../rachel-core/rules.c .
cp ../rachel-core/rules.h .

# 4. Create platform files
cat > Makefile << 'EOF'
# NES Makefile
CC65 = cc65
CA65 = ca65
LD65 = ld65

rachel.nes: rachel.o
	ld65 -C nes.cfg -o rachel.nes rachel.o nes.lib

rachel.o: rachel.s
	ca65 rachel.s -o rachel.o

rachel.s: rachel.c
	cc65 -t nes rachel.c -o rachel.s

clean:
	rm -f *.o *.s rachel.nes

test: rachel.nes
	fceux rachel.nes
EOF

# 5. Implement the platform
vim rachel.c  # or rachel.asm for assembly

# 6. Test locally
make

# 7. Push to trigger CI build
git add .
git commit -m "Initial NES implementation - Platform #010"
git push

# 8. Update organization README
cd ../.github
vim profile/README.md  # Add NES to platform list
git commit -am "Add NES as Platform #010"
git push
```

### 6. Batch Operations

Build multiple platforms at once:

```bash
# Create a script for batch operations
cat > build-all.sh << 'EOF'
#!/bin/bash
PLATFORMS="dos c64 gameboy apple2 spectrum ti83"

for platform in $PLATFORMS; do
  echo "Building rachel-$platform..."
  cd ~/Projects/rachel-$platform
  git pull
  make clean
  make
  echo "✓ $platform complete"
done
EOF

chmod +x build-all.sh
./build-all.sh
```

### 7. Testing Builds

Each platform can include test targets:

```bash
# In each platform's Makefile
test: rachel.rom
	# Platform-specific emulator test
	emulator rachel.rom --autorun --exit-after 30

# Then in CI or locally:
make test
```

### 8. Release Process

When ready to create a release with all platforms:

```bash
# Tag the release
cd ~/Projects/.github
git tag v1.0.0 -m "Rachel Multiverse v1.0.0 - 50 platforms"
git push --tags

# The workflow can auto-create releases
# Or manually:
gh release create v1.0.0 \
  --title "Rachel Multiverse v1.0.0" \
  --notes "50 platforms complete!" \
  rachel-dos/*.exe \
  rachel-c64/*.prg \
  rachel-gameboy/*.gb \
  # ... etc
```

### 9. Platform Status Dashboard

Check build status across all platforms:

```bash
# Quick status check
gh run list --repo rachel-multiverse/.github --limit 10

# Detailed platform status
for repo in $(gh repo list rachel-multiverse --limit 100 --json name -q '.[].name'); do
  echo -n "$repo: "
  gh run list --repo rachel-multiverse/$repo --limit 1 --json status -q '.[0].status'
done
```

### 10. DevContainer Usage

For VS Code users with Docker:

```bash
# Open any platform in a devcontainer
cd ~/Projects/rachel-nes
code .

# VS Code will prompt: "Reopen in Container"
# Click yes - it will:
# 1. Build the container with all tools
# 2. Mount your code
# 3. Install relevant extensions
# 4. Give you a terminal with everything ready
```

## Common Workflows

### Adding a New Platform to CI

1. Edit `.github/workflows/build-multiverse.yml`
2. Add to the matrix:
   ```yaml
   matrix:
     repo: [
       # ... existing platforms
       rachel-nes,  # Add new platform
     ]
   ```
3. Add build setup in the case statement
4. Commit and push

### Debugging Failed Builds

```bash
# Check workflow logs
gh run view --repo rachel-multiverse/.github

# Re-run with debug logging
gh workflow run build-multiverse.yml \
  -f platforms="problem-platform" \
  -f debug=true

# Or reproduce locally with same container
docker run -it rachel-multiverse/toolchain-platform bash
# Then manually run the build commands
```

### Cross-Platform Testing

```bash
# Test save file compatibility
make -C rachel-dos save-test.sav
make -C rachel-c64 load-test SAVE=../rachel-dos/save-test.sav
make -C rachel-gameboy verify-save SAVE=../rachel-dos/save-test.sav
```

## Build Optimization Tips

1. **Parallel Builds**: CI runs up to 20 platforms simultaneously
2. **Caching**: Docker layers are cached between builds
3. **Artifacts**: Only final binaries are saved (not intermediate files)
4. **Conditional Builds**: Only builds platforms with changes

## Monitoring & Metrics

```bash
# Build time analysis
gh run list --repo rachel-multiverse/.github --json durationMs,name \
  | jq '.[] | "\(.name): \(.durationMs/1000)s"'

# Success rate
gh run list --limit 100 --json conclusion \
  | jq '[.[] | select(.conclusion=="success")] | length'

# Artifact sizes
gh run download --repo rachel-multiverse/.github --pattern '*'
du -sh rachel-*
```

## Troubleshooting

### "No toolchain for platform"
- The Docker container might not exist yet
- Create it in `docker/toolchain-PLATFORM/`

### "Build succeeds locally but fails in CI"
- Check for missing dependencies in workflow
- Ensure all files are committed
- Verify paths are relative, not absolute

### "Artifacts not uploading"
- Check the artifact path patterns in workflow
- Ensure binary has expected extension
- Verify build actually creates output file

## The Full Development Cycle

```bash
# 1. Morning: Pull latest changes
cd ~/Projects
for dir in rachel-*/; do
  (cd $dir && git pull)
done

# 2. Pick a platform to work on
cd rachel-nes

# 3. Develop with live testing
make && fceux rachel.nes

# 4. Commit and push
git add .
git commit -m "Add power-up animations"
git push

# 5. CI builds automatically
# Watch the build: gh run watch

# 6. Download artifacts from other platforms
gh run download

# 7. Test cross-platform compatibility
for rom in artifacts/*/rachel.*; do
  echo "Testing $rom"
  # Run appropriate emulator
done

# 8. Celebrate! 
echo "🎮 Platform complete!"
```

## Advanced: Custom GitHub Actions

Create platform-specific actions:

```yaml
# .github/actions/setup-6502/action.yml
name: Setup 6502 Toolchain
description: Install cc65 and related tools
runs:
  using: composite
  steps:
    - run: |
        git clone https://github.com/cc65/cc65.git
        cd cc65 && make && sudo make install
      shell: bash
```

Then use in workflows:
```yaml
- uses: ./.github/actions/setup-6502
```

---

*"CI/CD: Because building for 200 platforms manually would take 200 lifetimes."*