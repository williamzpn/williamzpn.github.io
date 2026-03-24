# Peining Zhang Personal Website

This repository contains the source code for the personal academic website of Peining Zhang (William).

Site URL: [https://williamzpn.github.io](https://williamzpn.github.io)

The site is built with Jekyll and based on the Academic Pages / Minimal Mistakes ecosystem, but the homepage and content structure have already been customized for this personal website.

## Current Structure

- [`_config.yml`](./_config.yml): global site settings, author profile, sidebar information, site title, email, and social links
- [`_pages/about.md`](./_pages/about.md): homepage layout and section order
- [`_data/homepage.yml`](./_data/homepage.yml): homepage content data
- [`_data/navigation.yml`](./_data/navigation.yml): top navigation items
- [`assets/css/homepage-overrides.css`](./assets/css/homepage-overrides.css): custom homepage styling
- [`_publications/`](./_publications): publication entries
- [`_teaching/`](./_teaching): teaching and service-style entries used by the site
- [`files/`](./files): downloadable files such as CVs and PDFs
- [`images/`](./images): profile image, icons, and static images

## Homepage Content Source

The homepage is data-driven.

Most homepage sections are maintained in [`_data/homepage.yml`](./_data/homepage.yml), including:

- About Me
- Research Interests
- News
- Work Experiences
- Honors and Awards
- Services
- Educations

`News` is currently rendered as plain text items from `homepage.yml`, not from Jekyll posts.

## Local Development

### Requirements

- Ruby
- Bundler
- Node.js

### Install dependencies

```bash
bundle install
npm install
```

### Run locally

```bash
bundle exec jekyll serve -l -H localhost
```

Then open:

```text
http://localhost:4000
```

## Updating Common Content

### Update homepage text

Edit:

```text
_data/homepage.yml
```

### Update sidebar profile

Edit:

```text
_config.yml
```

This includes:

- name
- avatar
- bio
- employer
- email
- Google Scholar
- GitHub

### Update homepage layout or section order

Edit:

```text
_pages/about.md
```

### Update homepage styles

Edit:

```text
assets/css/homepage-overrides.css
```

## JavaScript Build

If you change files under `assets/js/`, rebuild the bundled script with:

```bash
npm run build:js
```

## Deployment

The site is intended to be deployed through GitHub Pages from this repository.

After committing and pushing changes, GitHub Pages should rebuild the site automatically.
