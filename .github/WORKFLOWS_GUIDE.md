# GitHub Actions Workflows

This repository uses two separate workflows for CI/CD:

## 1. Build and Test Workflow (`build.yml`)

**Triggers on:**
- Every push to `master`, `main`, or `develop` branches
- Every pull request to `master` or `main`
- Manual trigger from GitHub UI

**What it does:**
- ✅ Validates your code compiles
- ✅ Runs tests (if any)
- ✅ Creates a test package (not published)
- ✅ Uploads artifacts for inspection
- ✅ Provides quick feedback on code changes

**Purpose:** Continuous integration - ensures your code is always in a buildable state.

## 2. Publish to NuGet Workflow (`publish-nuget.yml`)

**Triggers on:**
- Push of version tags matching `v*.*.*` (e.g., v1.0.0, v1.2.3)
- Manual trigger from GitHub UI

**What it does:**
- ✅ Builds the release package
- ✅ Publishes to NuGet.org
- ✅ Creates symbol packages (.snupkg) for debugging
- ✅ Uploads artifacts to GitHub

**Purpose:** Continuous deployment - publishes releases to NuGet.org.

---

## How to Use

### Daily Development Workflow

1. **Make code changes** and commit:
   ```bash
   git add .
   git commit -m "Add new feature"
   git push origin master
   ```

2. **Build workflow runs automatically** ✅
   - Check status at: https://github.com/johnnyvz/UtilityLib/actions
   - Green checkmark = build passed
   - Red X = build failed, needs fixing

### Publishing a New Release

1. **Update version** in `UtilityLib/UtilityLib.csproj`:
   ```xml
   <Version>1.0.1</Version>
   ```

2. **Commit and push**:
   ```bash
   git add .
   git commit -m "Bump version to 1.0.1"
   git push origin master
   ```

3. **Create and push a version tag**:
   ```bash
   git tag v1.0.1
   git push origin v1.0.1
   ```

4. **Publish workflow runs automatically** 🚀
   - Watch at: https://github.com/johnnyvz/UtilityLib/actions
   - Package appears on NuGet.org within 5-10 minutes

---

## Manual Triggers

Both workflows support manual triggering:

1. Go to https://github.com/johnnyvz/UtilityLib/actions
2. Select the workflow (Build or Publish)
3. Click **"Run workflow"** dropdown
4. Select branch and click **"Run workflow"**

---

## Benefits of This Setup

✅ **Fast Feedback** - Know immediately if your changes break the build
✅ **Separate Concerns** - Building and publishing are independent
✅ **Safe Publishing** - Only tagged releases go to NuGet.org
✅ **PR Validation** - Pull requests are automatically tested
✅ **Version Control** - Git tags track which code version is published
✅ **Rollback Ready** - Can always republish from any tag

---

## Workflow Status Badges

Add these to your README.md to show build status:

```markdown
[![Build](https://github.com/johnnyvz/UtilityLib/actions/workflows/build.yml/badge.svg)](https://github.com/johnnyvz/UtilityLib/actions/workflows/build.yml)
[![Publish](https://github.com/johnnyvz/UtilityLib/actions/workflows/publish-nuget.yml/badge.svg)](https://github.com/johnnyvz/UtilityLib/actions/workflows/publish-nuget.yml)
[![NuGet](https://img.shields.io/nuget/v/DeeZyn.UtilityLib.svg)](https://www.nuget.org/packages/DeeZyn.UtilityLib/)
```

---

## Troubleshooting

### Build workflow fails
- Check the Actions tab for error logs
- Fix the issues and push again
- The workflow will run automatically on the new push

### Publish workflow fails
- Ensure `NUGET_API_KEY` secret is set correctly
- Verify the API key hasn't expired on NuGet.org
- Check that the version number hasn't been published already
- Ensure your email is verified on NuGet.org

### Need to update API key
1. Go to https://github.com/johnnyvz/UtilityLib/settings/secrets/actions
2. Click `NUGET_API_KEY`
3. Click **Update** and paste the new key
