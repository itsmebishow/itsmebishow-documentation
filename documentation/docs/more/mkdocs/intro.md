## Welcome to MkDocs

For full documentation visit [mkdocs.org](https://www.mkdocs.org).

## Commands

* `mkdocs new [dir-name]` - Create a new project.
* `mkdocs serve` - Start the live-reloading docs server.
* `mkdocs build` - Build the documentation site.
* `mkdocs -h` - Print help message and exit.

## Project layout

    mkdocs.yml    # The configuration file.
    docs/
        index.md  # The documentation homepage.
        ...       # Other markdown pages, images and other files.


---

## Deploying your docs

!!! success "Deploying"

    ```
    my-project/
        mkdocs.yml
        docs/
    orgname.github.io/

    $ cd ../orgname.github.io/
    $ mkdocs gh-deploy --config-file ../<your-repo>/mkdocs.yml --remote-branch <master>
    ```

## Plugins Used

1. [MkDocs](https://www.mkdocs.org/)
2. [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/getting-started/)
3. [MkDocs GLightbox](https://github.com/blueswen/mkdocs-glightbox)
4. [MkDocs Video](https://pypi.org/project/mkdocs-video/)

## Suggestion

- [best MkDocs plugins](https://chrieke.medium.com/the-best-mkdocs-plugins-and-customizations-fc820eb19759)
- [Uick Guide: setup essentials](https://squidfunk.github.io/mkdocs-material/setup/adding-a-git-repository/)

- Admonition
- [Admonitions](https://squidfunk.github.io/mkdocs-material/reference/admonitions/)
- [Admonitions 2](https://squidfunk.github.io/mkdocs-material/setup/extensions/python-markdown/#admonition)