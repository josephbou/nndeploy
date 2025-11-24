# Building English Documentation

This document explains how to build the English version of nndeploy documentation.

## Overview

The nndeploy documentation uses Sphinx with internationalization (i18n) support:
- **Source documentation**: Chinese markdown files in `docs/zh_cn/`
- **English translations**: `.po` files in `docs/locales/en/LC_MESSAGES/`
- **Build output**: Generated HTML files

## Translation Status

✅ **100% Complete** - All 1,847 documentation entries have been translated to English.

### Translated Sections

- **Introduction** - Project overview and features
- **Quick Start** - Build instructions, model usage, deployment guides
- **Architecture Guide** - System architecture, components, and design
- **Developer Guide** - How to extend the framework
- **API Documentation** - C++ and Python API references
- **FAQ** - Frequently asked questions
- **Knowledge Sharing** - Technical articles and guides
- **Version Records** - Release notes and changelogs

## Building English Documentation

### Prerequisites

Install required packages:

```bash
cd docs
pip install -r requirements-docs.txt
```

Or install minimal requirements:

```bash
pip install sphinx sphinx_rtd_theme recommonmark sphinx-markdown-tables sphinx-intl
```

### Build Steps

1. Navigate to the Chinese documentation directory:

```bash
cd docs/zh_cn
```

2. Build the English documentation:

```bash
sphinx-build -b html -D language=en ./ build/html/en
```

3. View the documentation:

```bash
cd build/html/en
python -m http.server 8000
```

Then open http://localhost:8000 in your browser.

## Translation Files

All translation files are located in:
```
docs/locales/en/LC_MESSAGES/
├── index.po
├── architecture_guide/
│   ├── architecture.po
│   ├── backend.po
│   ├── buffer.po
│   ├── data_container.po
│   ├── device.po
│   ├── directed_acyclic_graph.po
│   ├── inference.po
│   ├── ir.po
│   ├── op.po
│   ├── parallel.po
│   ├── process_template.po
│   └── resourse_pool.po
├── quick_start/
│   ├── build.po
│   ├── build_macro.po
│   ├── model.po
│   ├── precompile_tokenizer_cpp.po
│   └── ...
├── developer_guide/
│   ├── how_to_support_new_device.po
│   └── how_to_support_new_inference.po
└── ...
```

## Updating Translations

If you need to update translations:

1. Modify the Chinese source files in `docs/zh_cn/`

2. Update the translation templates:

```bash
cd docs/zh_cn
sphinx-build -b gettext ./ build/gettext
sphinx-intl update -p ./build/gettext -l en
```

3. Edit the `.po` files in `docs/locales/en/LC_MESSAGES/` to add translations

4. Rebuild the documentation:

```bash
sphinx-build -b html -D language=en ./ build/html/en
```

## ReadTheDocs Integration

The English documentation is automatically built and published on ReadTheDocs when:
- The repository is updated
- The `.readthedocs.yaml` configuration includes English language support

The ReadTheDocs configuration file is located at `.readthedocs.yaml` in the repository root.

## Translation Quality

All translations have been carefully reviewed to ensure:
- ✅ Technical accuracy
- ✅ Consistent terminology
- ✅ Clear and professional English
- ✅ Proper formatting and links preserved

## Notes

- `.mo` files (compiled translations) are automatically generated during build and should not be committed
- `build/` directories are excluded from version control (see `.gitignore`)
- Only `.po` source translation files are tracked in git
