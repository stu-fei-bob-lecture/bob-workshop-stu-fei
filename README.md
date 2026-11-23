# IBM Bob — STU FEI Lecture Guide

Hands-on lab guide for the IBM Bob lecture at STU FEI. Three tracks — Beginner, Intermediate and Expert — plus an optional Challenge.

**Site:** https://stu-fei-bob-lecture.github.io/bob-workshop-stu-fei

The site is available in English and Slovak (`/sk/`).

## Local Development

```bash
pip install -r requirements.txt
mkdocs serve
```

Open http://127.0.0.1:8000

## Build

```bash
mkdocs build
```

## Deploy (GitHub Pages)

Push to `main` — the GitHub Actions workflow in `.github/workflows/deploy.yml` builds and deploys automatically.

## Translations

Translations use [mkdocs-static-i18n](https://github.com/ultrabug/mkdocs-static-i18n) with the suffix structure: `page.md` is English, `page.sk.md` is Slovak. Pages without a `.sk.md` file fall back to English.

## Structure

```
docs/
├── index.md / index.sk.md          # Home page
├── setup.md / setup.sk.md          # Setup before the lecture
├── labs/
│   ├── beginner.md / beginner.sk.md
│   ├── intermediate.md
│   ├── expert.md
│   └── challenge.md
└── assets/                         # Logo, CSS
galaxium-travels/                   # Demo app used in the labs (git submodule)
mkdocs.yml                          # Site configuration
requirements.txt                    # Python dependencies for MkDocs
```

## Cloning

`galaxium-travels/` is a git submodule:

```bash
git clone --recurse-submodules https://github.com/stu-fei-bob-lecture/bob-workshop-stu-fei.git
```
