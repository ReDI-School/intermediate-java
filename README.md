![ReDI](redi_banner.png)

# Please note

### When exposing a lesson you must update the following properties in the markdown

```yaml
nav_order: 0
nav_exclude: false
```

### - The `nav_order` must be set to the corresponding course number, 
### - and the `nav_exclude` set to `false`

# Intermediate Java

This is the support project for the "Intermediate Java" course
at [ReDI School](https://www.redi-school.org).

The website is visible at:

**https://redi-school.github.io/intermediate-java/**

This website was generated from
the [course-template](https://github.com/ReDI-School/course-template). You can create your own
course website creating a repository out of the same template.

## Configuring the project

Please replace Intermediate Java in this file with the name of the course, as configured in GitHub.
This must be the GitHub project name and it's used in the final URL. Then delete this paragraph.

## Authoring the website

Every markdown `.md` file is scanned and transformed into a page automatically. This includes files
in subdirectories. The course homepage is stored in `index.md`.

The website is built using [Jekyll](https://jekyllrb.com) and hosted automatically by GitHub Pages.
You cannot use a different generator, as Jekyll is the only one supported by GitHub Pages.

For details on how to author a static website using Jekyll, please see
the [Jekyll documentation](https://jekyllrb.com/docs).

## How to publish and update the course website

This website is built by GitHub Pages using Jekyll. This happens automatically if GitHub Pages is
configured in the following way:

- Go to the settings of the project
- Enable GitHub Pages
- Configure GitHub Pages to publish directly the `master` branch (not `master/docs` or `gh-pages`)
- Don't select a theme

Once these settings are applied to the project, every commit on `master` will trigger a new build of
the website that automatically replaces the older version at the `github.io` URL above. The URL
can't be changed.

## Building locally

To build and test the website, you must have a Ruby development environment with Bundler.

### Installing Ruby, Bundler, Jekyll

On Ubuntu LTS 20.04:

```
sudo apt install bundler ruby-dev zlib1g-dev
```

The last two packages are needed to compile some native Ruby dependencies (Ubuntu specific). On
MacOS and Windows, please follow the installation instructions of Ruby and Bundler as suggested in
the Jekyll [install guide](https://jekyllrb.com/docs/installation).

Once Ruby and Bundler are installed, use the following command to download the gems, including the
proper version of Jekyll (only once):

```
bundle install --path vendor/bundle
```

This creates the `.bundle` and `vendor` directories, that should *not* be committed to the git
repository.

### Building and testing the website

To build, test and serve the website locally, please run:

```
bundle exec jekyll serve
```

You can then visit the website on [localhost:4000](http://localhost:4000).

## About the ReDI theme

Note this website uses Just The Docs, a well-known Jekyll theme, customized with ReDI colors and
logos.

For instuctions and examples of what the theme can do, and how you can do the same in your course
pages, please see: https://pmarsceill.github.io/just-the-docs
