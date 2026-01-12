# GitHub Workflow Configuration

This repository uses a simplified GitHub Actions workflow to build Docker images.

## Active Workflow

**File:** `.github/workflows/build-docker.yml`

### What it does:
- Triggers on every push to the `main` branch
- Builds a Docker image for **x86/amd64 architecture only**
- Pushes to **GitHub Container Registry** (ghcr.io)
- Tags the image as `latest`

### Image location:
After a successful build, your Docker image will be available at:
```
ghcr.io/<your-username>/ezbookkeeping:latest
```

To pull and run:
```bash
docker pull ghcr.io/<your-username>/ezbookkeeping:latest
docker run -d -p 8080:8080 ghcr.io/<your-username>/ezbookkeeping:latest
```

### Requirements:
- No additional secrets needed (uses built-in `GITHUB_TOKEN`)
- No repository variables needed (uses `github.repository` and `github.actor`)
- GitHub Actions must be enabled in your repository settings

## Disabled Workflows

The following original workflow files have been disabled (renamed with `.disabled` extension):
- `build-snapshot.yml.disabled` - Was for snapshot builds with multi-arch support
- `build-release.yml.disabled` - Was for release builds with ARM support
- `build-non-main-branch.yml.disabled` - Was for non-main branch builds

These files are kept for reference but won't run. You can delete them if not needed.

## Notes:
- This simplified workflow doesn't build ARM images
- No Docker Hub publishing (only GitHub Container Registry)
- No Windows package builds
- No release publishing to GitHub Releases
