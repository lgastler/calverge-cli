# v1.0 Release Setup Summary

## ✅ Completed Changes

### 1. Updated GitHub Workflow

- ✅ Fixed references from Things2Calendar to calverge
- ✅ Updated binary names and paths
- ✅ Added Homebrew formula auto-update using `mislav/bump-homebrew-formula-action@v3`
- ✅ Fixed archive creation and checksum calculation
- ✅ Updated release notes template

### 2. Updated README.md

- ✅ Added comprehensive installation instructions
- ✅ Added Homebrew installation section
- ✅ Added direct download section with curl commands
- ✅ Fixed manual installation instructions
- ✅ Removed Things app references from requirements

### 3. Updated CalvergeCLI.swift

- ✅ Version remains at 0.0.1 (changesets will update it automatically)

### 4. Created Release Changeset

- ✅ Created `.changeset/initial-release.md` for v1.0.0 major release
- ✅ Verified changesets detects the pending major version bump

### 5. Project Structure

- ✅ Verified entitlements file is correct
- ✅ Verified project builds successfully (debug and release)
- ✅ Created CHANGELOG.md placeholder (changesets will populate it)
- ✅ Tested version output shows 0.0.1 (will be updated by changesets)

## 🔧 Required Manual Actions

### 1. Setup GitHub Secret for Homebrew Updates

1. **Create Personal Access Token:**

   - Go to GitHub → Settings → Developer settings → Personal access tokens → Tokens (classic)
   - Click "Generate new token (classic)"
   - Name: "Calverge Homebrew Formula Updates"
   - **Required Scopes:**
     - `public_repo` (to access and modify your public homebrew-tap repository)
     - `workflow` (if your tap repository has GitHub Actions workflows)
   - **Note:** The token needs write access to `lgastler/homebrew-tap` repository
   - Set expiration (recommend 1 year or "No expiration" for automation)
   - Copy the generated token

2. **Add Secret to Repository:**
   - Go to calverge-cli repository → Settings → Secrets and variables → Actions
   - Click "New repository secret"
   - Name: `HOMEBREW_TAP_TOKEN`
   - Value: Paste the personal access token
   - Click "Add secret"

### 2. Verify Homebrew Tap Repository

- Ensure `https://github.com/lgastler/homebrew-tap` exists
- The workflow will automatically create/update `Formula/calverge.rb`

### 3. Trigger the Release

After setting up the secret, push your changes:

```bash
# Commit all the changes
git add -A
git commit -m "feat: prepare v1.0.0 release with automated homebrew updates"
git push origin main
```

## 🚀 Release Process

1. **Push Changes:**

   ```bash
   git add -A
   git commit -m "feat: prepare v1.0.0 release with automated homebrew updates"
   git push origin main
   ```

2. **Automatic Version PR Creation:**

   - Changesets will detect the changeset and create a "Version Packages" PR
   - This PR will update `package.json`, `CHANGELOG.md`, and `Sources/CalvergeCLI.swift`
   - Review and merge the PR

3. **Automatic Release:**

   - Merging the version PR creates a git tag (v1.0.0)
   - Tag creation triggers the build workflow
   - Binary is built, signed, and uploaded to releases
   - Homebrew formula is automatically updated

4. **Installation Methods Available:**
   - `brew install lgastler/tap/calverge`
   - Direct download from GitHub releases
   - Manual build from source

## 📋 Release Checklist

- ✅ GitHub workflow updated with Homebrew automation
- ✅ README.md updated with installation instructions
- ✅ Version remains at 0.0.1 (changesets handles versioning)
- ✅ Changeset created for v1.0.0
- ✅ Project builds successfully
- ✅ Entitlements file is correct
- ⏳ Set up HOMEBREW_TAP_TOKEN secret
- ⏳ Verify homebrew-tap repository exists
- ⏳ Push changes to trigger release process

## 🎯 Next Steps

1. Set up the `HOMEBREW_TAP_TOKEN` secret (instructions above)
2. Push the changes to main branch
3. Merge the version PR when it appears
4. Verify the release is created and Homebrew formula is updated
5. Test installation via Homebrew: `brew install lgastler/tap/calverge`

Everything is ready for a smooth v1.0 release! 🚀
