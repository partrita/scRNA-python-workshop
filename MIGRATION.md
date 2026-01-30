# Jupyter Book Migration Guide

## What Changed

This repository has been upgraded from **Jupyter Book 0.6.2** (Jekyll-based) to **Jupyter Book 1.x** (Sphinx-based).

## Major Changes

### 1. **Build System**
- **Old**: Jekyll + Ruby
- **New**: Sphinx + Python only
- **Benefit**: No more Ruby dependencies, faster builds, better Python integration

### 2. **Configuration Files**

#### `_config.yml`
- Completely rewritten to use Jupyter Book 1.x format
- Now uses Sphinx configuration structure
- Added modern features like MyST parser extensions
- Repository and launch button configurations updated

#### `_toc.yml`
- Migrated from `_data/toc.yml` to root `_toc.yml`
- Changed from Jekyll format to `jb-book` format
- Uses `parts` and `chapters` structure instead of headers

### 3. **Build Output**
- **Old**: `_site/` directory (Jekyll output)
- **New**: `_build/html/` directory (Sphinx output)

### 4. **Templates**
- **Old**: Custom Jinja2 templates in `scripts/templates/`
- **New**: Uses built-in Sphinx/PyData theme
- Custom templates are no longer needed (Sphinx handles this better)

### 5. **GitHub Actions Workflow**

**Old workflow** (`deploy.yml`):
```yaml
- Install Python 3.7
- Install jupyter-book==0.6.2
- Build with jupyter-book
- Install Ruby 2.6
- Build with Jekyll
- Deploy _site/
```

**New workflow**:
```yaml
- Install Python 3.11
- Install latest jupyter-book
- Build with jupyter-book (outputs to _build/html)
- Deploy _build/html/
```

### 6. **Removed Dependencies**
- ❌ Ruby (no longer needed)
- ❌ Jekyll (replaced by Sphinx)
- ❌ Gemfile/Gemfile.lock (Ruby dependencies)
- ❌ Custom Jinja2 templates (built-in theme is better)

## Benefits of Upgrading

1. **✅ Modern Python Support**: Works with Python 3.9, 3.10, 3.11+
2. **✅ Better Performance**: Faster builds, better caching
3. **✅ Active Maintenance**: Jupyter Book 1.x is actively developed
4. **✅ Security**: Up-to-date dependencies
5. **✅ Better Features**: 
   - MyST Markdown with more features
   - Better theming with PyData Sphinx Theme
   - Improved navigation
   - Better mobile support
   - Enhanced search functionality

## Local Development

### Building the book locally:

```bash
# Install jupyter-book
pip install -U jupyter-book

# Build the book
jupyter-book build .

# View the output
# Open _build/html/index.html in your browser
```

### Clean build:

```bash
jupyter-book clean .
jupyter-book build .
```

## Troubleshooting

### Issue: "File not found" errors
- Check that all files referenced in `_toc.yml` exist in the `content/` directory
- Ensure file paths are relative to the repository root

### Issue: Build fails with template errors
- The old custom templates are no longer used
- Modern Jupyter Book uses Sphinx themes - no custom templates needed

### Issue: Styling looks different
- This is expected! The new theme is PyData Sphinx Theme
- You can customize it in `_config.yml` under the `html:` section

## Migration Checklist

- [x] Created new `_toc.yml` in root directory
- [x] Updated `_config.yml` to Jupyter Book 1.x format
- [x] Updated GitHub Actions workflow
- [x] Removed Ruby/Jekyll dependencies
- [x] Updated `.gitignore` for new build directory
- [x] Added `.nojekyll` file for GitHub Pages

## Next Steps

1. **Test the build**: Push changes and check GitHub Actions
2. **Review the output**: Check the deployed site on GitHub Pages
3. **Customize theme**: Adjust `_config.yml` if you want different colors/styling
4. **Update README**: Update any build instructions in README.md

## Resources

- [Jupyter Book Documentation](https://jupyterbook.org/)
- [MyST Markdown Guide](https://myst-parser.readthedocs.io/)
- [PyData Sphinx Theme](https://pydata-sphinx-theme.readthedocs.io/)
