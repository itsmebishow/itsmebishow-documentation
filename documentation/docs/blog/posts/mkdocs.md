---
drafts: false
tags: [mkdocs, doc]
comments: true
date: 2024-05-05
authors:
  - bishow
---


# Mkdoc

<!-- more -->

---


## Core

For full documentation visit [mkdocs.org](https://www.mkdocs.org).

### Commands

* `mkdocs new [dir-name]` - Create a new project.
* `mkdocs serve` - Start the live-reloading docs server.
* `mkdocs build` - Build the documentation site.
* `mkdocs -h` - Print help message and exit.

### Project layout

    mkdocs.yml    # The configuration file.
    docs/
        index.md  # The documentation homepage.
        ...       # Other markdown pages, images and other files.


---

### Deploying your docs

!!! success "Deploying"

    ```
    my-project/
        mkdocs.yml
        docs/
    orgname.github.io/

    $ cd ../orgname.github.io/
    $ mkdocs gh-deploy --config-file ../<your-repo>/mkdocs.yml --remote-branch <master>
    ```

### Plugins Used

1. [MkDocs](https://www.mkdocs.org/)
2. [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/getting-started/)
3. [MkDocs GLightbox](https://github.com/blueswen/mkdocs-glightbox)
4. [MkDocs Video](https://pypi.org/project/mkdocs-video/)

### Suggestion

- [best MkDocs plugins](https://chrieke.medium.com/the-best-mkdocs-plugins-and-customizations-fc820eb19759)
- [Uick Guide: setup essentials](https://squidfunk.github.io/mkdocs-material/setup/adding-a-git-repository/)

- Admonition
- [Admonitions](https://squidfunk.github.io/mkdocs-material/reference/admonitions/)
- [Admonitions 2](https://squidfunk.github.io/mkdocs-material/setup/extensions/python-markdown/#admonition)

---


## Basic

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

## Advanced Mkdocs

### Configure Pages and Navigation

```
// A minimal navigation configuration could look like this:

nav:
  - 'index.md'
  - 'about.md'
```

```
// override the title in the nav setting add a title right before the filename

nav:
  - Home: 'index.md'
  - About: 'about.md'
```

```
// Navigation sub-sections can be created by listing related pages together under a section title

nav:
  - Home: 'index.md'
  - 'User Guide':
    - 'Writing your docs': 'writing-your-docs.md'
    - 'Styling your docs': 'styling-your-docs.md'
  - About:
    - 'License': 'license.md'
    - 'Release Notes': 'release-notes.md'
```

### [Formatting](https://squidfunk.github.io/mkdocs-material/reference/formatting/)

Add the following lines to `mkdocs.yml`:

```bash
# Configuration

markdown_extensions:
  - pymdownx.critic
  - pymdownx.caret
  - pymdownx.keys
  - pymdownx.mark
  - pymdownx.tilde
```

### Highlighting Text

When Critic is enabled, Critic Markup can be used, which adds the ability to highlight suggested changes, as well as add inline comments to a document:

```bash
# Text with highlighting
- ==This was marked==
- ^^This was inserted^^
- ~~This was deleted~~

# {== Long Highlight ==}

# Sub- and superscripts
- H~2~O
- A^T^A

# Keyboard keys
++ctrl+alt+del++
```

### [Lists](https://squidfunk.github.io/mkdocs-material/reference/lists/)

```bash
# Configuration

markdown_extensions:
  - def_list
  - pymdownx.tasklist:
      custom_checkbox: true
```

When Tasklist is enabled, unordered list items can be prefixed with `[ ]` to render an unchecked checkbox or `[x]` to render a checked checkbox, allowing for the definition of task lists:

```bash
# Definition list
`Lorem ipsum dolor sit amet`

:   Sed sagittis eleifend rutrum. Donec vitae suscipit est. Nullam tempus
    tellus non sem sollicitudin, quis rutrum leo facilisis.

# TaskList
- [x] Lorem ipsum dolor sit amet, consectetur adipiscing elit
- [ ] Vestibulum convallis sit amet nisi a tincidunt
    * [x] In hac habitasse platea dictumst
    * [x] In scelerisque nibh non dolor mollis congue sed et metus
    * [ ] Praesent sed risus massa
- [ ] Aenean pretium efficitur erat, donec pharetra, ligula non scelerisque
```

---

## Reference
- [mkdocs official site](https://www.mkdocs.org/getting-started/)
- [mkdocs material theme](https://squidfunk.github.io/mkdocs-material/getting-started/)
- [mkdocs-glightbox](https://github.com/blueswen/mkdocs-glightbox)

- [mkdocs navigation configuration](https://www.mkdocs.org/user-guide/writing-your-docs/)
- [mkdocs-glightbox](https://blueswen.github.io/mkdocs-glightbox/caption/caption/)
- [mkdocs-pdf](https://pypi.org/project/mkdocs-pdf/)
