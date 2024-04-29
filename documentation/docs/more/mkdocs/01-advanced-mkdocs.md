# Mkdocs

### Installation
```
$ pip install mkdocs
$ mkdocs new my-project
$ cd my-project
$ mkdocs serve
```
### Theming our documentation
```
site_name: MkLorum
site_url: https://example.com/
nav:
  - Home: index.md
  - About: about.md
theme: readthedocs
```

### Building the site

```
$ mkdocs build
```

### Deploying your docs
```
my-project/
    mkdocs.yml
    docs/
orgname.github.io/

$ cd ../orgname.github.io/
$ mkdocs gh-deploy --config-file ../my-project/mkdocs.yml --remote-branch master
```

### Material theme
```
# Installing theme only
$ pip install mkdocs-material

# Next, install the theme and its dependencies with:
$ pip install -e mkdocs-material

# mkdocs.yml
theme:
  name: material

# glightbox
$ pip install mkdocs-glightbox

# Add plugin in your mkdocs.yml
plugins:
   - glightbox
```

---

### Reference
- [mkdocs official site](https://www.mkdocs.org/getting-started/)
- [mkdocs material theme](https://squidfunk.github.io/mkdocs-material/getting-started/)
- [mkdocs-glightbox](https://github.com/blueswen/mkdocs-glightbox)