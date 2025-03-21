# Quarto-cv Format

[![quarto-ext-chk](https://github.com/mps9506/quarto-cv/actions/workflows/check-extension.yaml/badge.svg)](https://github.com/mps9506/quarto-cv/actions/workflows/check-extension.yaml)

A Quarto template for generating a CV in pdf format. The template is based entirely
on [Steven Miller's R Markdown templates](https://github.com/svmiller/stevetemplates).

## Installing

```bash
quarto install extension mps9506/quarto-cv
```

This will install the template for use with existing Quarto projects or documents.

*or* To install the extension and create an example qmd file and project (easiest way to start):

```bash
quarto use template mps9506/quarto-cv
```


## Usage

To use with with quarto in the cli:

```bash
quarto render your_cv.qmd --to quarto-cv.pdf
```

or specify in the document yaml:

```yaml
format:
  quarto-cv-pdf: default
```

## Format Options

### Contact Block

The contact block at the top of the CV is rendered using the following metadata:

```yaml
author: First Name Last Name
address: Street, City, State, Country
# The following are optional
phone: your contact number
email: you@email.com
github: github account
orcid: orcid identfier
osf: five character osf id
twitter: twitter handle
web: web address (no `https://`)
```

### Bibliographies

The template includes a lua filter to easily incorporate multiple bibliographies using `.bib` files if you choose to manage publications this way. This is a good option for separating out book/chapter, journal articles, white papers, datasets, and software.

In the document yaml header simply point to your `.bib` files and provide a unique name:

```yaml
bibliography:
  peer: peer.bib
  reports: reports.bib
  books: books.bib
  software: software.bib
validate-yaml: false
```

Note, that the `validate-yaml` key must be false in quarto because it expects
a character value when it vaildates the yaml header.

Now create different bibliographies for each one:

```
# Journal Articles

::: {#refs-peer}
:::

# Software

::: {#refs-software}
:::
```

You can specify the bibliographic style using the csl variable. By default it points to an APA style sorted by descending date. Other styles can be found [here](https://www.zotero.org/styles).


## Example

Here is the source code for a minimal sample document: [template.qmd](template.qmd).

# License

The template is based entirely
on [Steven Miller's R Markdown templates](https://github.com/svmiller/stevetemplates)
licensed under GPL-2. A copy of the pandoc 
[`multibib`](https://github.com/pandoc-ext/multibib) lua filter 
licensed under MIT is included as part of this template.

# Release Notes

## v1.0.2 (not released)

- Update tex template for changes to citeproc in pandoc >=3.1.8 (Fixes [#4](https://github.com/mps9506/quarto-cv/issues/4)).

## v1.0.1

- Properly embed [pandoc-ext `multibib`](https://github.com/pandoc-ext/multibib) extension (Fixes [#2](https://github.com/mps9506/quarto-cv/issues/2)).
- Add CI test for pull requests on main.
- Add .quartoignore to avoid copying extra files.
- Fix README.md install instructions (@anielsen001) ([#1](https://github.com/mps9506/quarto-cv/pull/1)).


## v1.0.0

- Initial Release