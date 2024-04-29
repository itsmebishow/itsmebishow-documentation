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

## [Lists](https://squidfunk.github.io/mkdocs-material/reference/lists/)

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

- [mkdocs navigation configuration](https://www.mkdocs.org/user-guide/writing-your-docs/)
- [mkdocs-glightbox](https://blueswen.github.io/mkdocs-glightbox/caption/caption/)
- [mkdocs-pdf](https://pypi.org/project/mkdocs-pdf/)
