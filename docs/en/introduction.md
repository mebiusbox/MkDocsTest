# Get started

## About MkDocs

mkdocs is a static site generator. The content is basically a source file written in markdown format. You can also use HTML format files. This article summarizes the minimum personal creation environment on Windows.

- [MkDocs](http://www.mkdocs.org/)


## How to install

First, install python. Next, install mkdocs using pip.

```
pip install mkdocs
```

environment:

```
python                  3.7.0
mkdocs                  1.0.4
mkdocs-material         4.1.1
fontawesome-markdown    0.2.6
mdx_unimoji             1.0
python-markdown-math    0.6
pymdown-extensions      6.0
```


## MkDocs commands

Use `mkdocs new` to create a new project.

```
mkdocs new
```

The next step is to build to generate the necessary files for the site. To build, execute the following command


```
mkdocs build
```

If successfully generated, it will be created in the site folder. Upload this folder if you want to publish on the Internet. If you want to check the build locally before publishing, run the `serve` command to start the server.

```
mkdocs serve
```

The output of the command will show the address and port number as `Serving on http://127.0.0.1:8000`, which you can verify by typing the address into your browser.

While running SERVE, file additions and changes are detected and automatically built.


## mkdocs.yml

You can configure and customize the documentation by editing the mkdocs.yml file. This file describes the site title, theme, extension settings, etc. This file is automatically created when you create a project.

