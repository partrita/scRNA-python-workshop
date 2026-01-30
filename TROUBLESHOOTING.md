# GitHub Pages 404 Fix

## Problem
After deploying to GitHub Pages, the site showed a 404 error because Jupyter Book couldn't find the source files.

## Root Cause
The `_toc.yml` file was referencing files without the `content/` directory prefix. Since all source files are in the `content/` directory, Jupyter Book couldn't locate them during the build process.

## Solution Applied

### 1. Updated `_toc.yml`
Changed all file paths to include the `content/` prefix:

**Before:**
```yaml
root: intro/about
parts:
  - caption: Introduction
    chapters:
    - file: intro/about
```

**After:**
```yaml
root: content/intro/about
parts:
  - caption: Introduction
    chapters:
    - file: content/intro/about
```

### 2. Updated GitHub Actions Workflow
Added step to copy `.nojekyll` file to build output:

```yaml
- name: Build the book
  run: |
    jupyter-book build .
    cp .nojekyll _build/html/
```

This ensures GitHub Pages doesn't try to process the Sphinx-generated HTML with Jekyll.

## Verification

After pushing these changes:
1. GitHub Actions will rebuild the site
2. The build should complete successfully
3. The site should be accessible at your GitHub Pages URL
4. The homepage should show "About the course" content

## If Still Getting 404

Check the following:

1. **GitHub Pages Settings**:
   - Go to repository Settings → Pages
   - Ensure "Source" is set to "gh-pages" branch and "/ (root)" folder
   - The workflow automatically creates/updates the `gh-pages` branch

2. **Build Logs**:
   - Check the Actions tab in your repository
   - Look for any errors in the "Build the book" step
   - Ensure all files in `_toc.yml` exist in the `content/` directory

3. **File Paths**:
   - All paths in `_toc.yml` must match actual file locations
   - Files can be `.md` or `.ipynb`
   - Don't include file extensions in `_toc.yml`

## Common Issues

### Issue: "File not found" during build
- **Cause**: Path in `_toc.yml` doesn't match actual file location
- **Fix**: Verify file exists and path is correct (include `content/` prefix)

### Issue: Site loads but shows wrong content
- **Cause**: `root:` in `_toc.yml` points to wrong file
- **Fix**: Ensure `root: content/intro/about` is correct

### Issue: Images or assets not loading
- **Cause**: Relative paths in notebooks/markdown may be incorrect
- **Fix**: Use paths relative to the file location, not the repository root
