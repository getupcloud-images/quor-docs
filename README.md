# Quor Documentation

This repository contains the source code for the [Quor](https://docs.quor.dev) documentation website. Quor is a secure container image catalog that provides production-ready images free of known CVEs, with digital signatures and SBOMs for supply chain security.

The documentation is built with [MkDocs](https://www.mkdocs.org/) using the [Material](https://squidfunk.github.io/mkdocs-material/) theme and supports English and Portuguese.

## Getting Started

### Prerequisites

- Python 3.x
- pip

### Clone the repository

```bash
git clone git@github.com:getupcloud-images/quor-docs.git
cd quor-docs
```

### Install dependencies

```bash
pip install mkdocs-material mkdocs-static-i18n
```

### Run locally

```bash
python3 -m mkdocs serve
```

The site will be available at `http://localhost:8000` with live reload enabled.

### Build

To generate the static site:

```bash
mkdocs build
```

The output will be in the `site/` directory.
