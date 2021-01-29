# Next.js WordPress Starter <!-- omit in toc -->

WebDevStudios fork of the official Next.js WordPress [example](https://github.com/vercel/next.js/tree/canary/examples/cms-wordpress). Used as a starter for headless WordPress projects.

**This project is still in active development. Use at your own risk.**

https://nextjs-wordpress-starter-staging.vercel.app/

<a href="https://webdevstudios.com/contact/"><img src="https://webdevstudios.com/wp-content/uploads/2018/04/wds-github-banner.png" alt="WebDevStudios. Your Success is Our Mission."></a>

## 🗂 Table of Contents <!-- omit in toc -->

- [🎓 Overview](#-overview)
  - [Why?](#why)
  - [How's this all work?](#hows-this-all-work)
- [🚀 Frontend Setup (Next.js)](#-frontend-setup-nextjs)
  - [Dependencies](#dependencies)
  - [Install](#install)
- [🔧 Backend Setup (WordPress)](#-backend-setup-wordpress)
  - [Dependencies](#dependencies-1)
  - [Install](#install-1)
- [💻 Frontend Development](#-frontend-development)
  - [Git Workflow](#git-workflow)
  - [Deployments](#deployments)
  - [Storybook](#storybook)
- [WebDevStudios Specific Info](#webdevstudios-specific-info)
  - [WordPress Github](#wordpress-github)
  - [WP Engine](#wp-engine)
  - [Chromatic](#chromatic)
  - [1Password](#1password)
  - [Migrate DB Pro](#migrate-db-pro)
  - [Copy WP Engine Environments](#copy-wp-engine-environments)
- [:octocat: Contributing](#octocat-contributing)

---

## 🎓 Overview

### Why?

It's easy to query a WordPress REST-API and map over some blog posts in JavaScript. That's where many examples on the Internet stop and you'd be hard pressed to find anything about supporting advanced features because **_headless WordPress is hard!_**

At WebDevStudios we believe that WordPress is so much more than a blog-- and our clients require support for things like: SEO, forms, post previews, search, comments, authentication, custom post types, custom fields, etc...

With this starter, we've figured out "the hard stuff" and placed the sum of our knowledge into something the community (and our future projects) could use as a jumping off point.

### How's this all work?

The frontend (Next.js) talks to the backend (WordPress) via GraphQL.

<details>
<img src="https://dl.dropbox.com/s/9wsal7szatfwt6g/nextjs-wordpress-starter-frontend-backend-graphic.png?dl=0" alt="A graphic showing the relationship between environments">
</details>

---

## 🚀 Frontend Setup (Next.js)

The following steps will stand up a local install of Next.js.

### Dependencies

Before you get started, make sure you have the following dependencies installed on your computer:

- [Node 12](https://nodejs.org/en/)
- [Yarn](https://yarnpkg.com/)
- [Vercel CLI](https://vercel.com/download)

### Install

**Step 1: Clone the repo**

```bash
git clone git@github.com:WebDevStudios/nextjs-wordpress-starter.git
```

**Step 2: Change directories**

```bash
cd nextjs-wordpress-starter
```

**Step 3: Install dependencies**

```bash
yarn
```

**Step 4: Setup ENV Variables**

Copy the sample ENV file, then add your credentials:

```bash
cp .env.sample .env
```

--OR--

[Link the project with Vercel](https://vercel.com/docs/cli#commands/overview/project-linking), then pull down the ENV variables:

<details>

The following steps require A) access to a Vercel account and B) assumes the ENV vars are already set up on Vercel. If you need access to the WDS Team account on Vercel, please reach out to Greg.

**Step 1: Install the [Vercel CLI](https://vercel.com/download)**

```bash
npm i -g vercel
```

**Step 2: Initialize Vercel**

```bash
vercel init
```

Answer the questions in the command line when prompted.

**Step 3: Pull down the ENV variables**

```bash
vercel env pull
```

</details>

---

## 🔧 Backend Setup (WordPress)

The following steps will stand up a local install of WordPress.

### Dependencies

Before you get started, make sure you have the following dependency installed on your computer:

- [Local WP](https://localwp.com/)

### Install

**Step 1: Download the Local WP export**

- [nextjs-wp-01.29.2021.zip (162MB)](https://drive.google.com/file/d/1iTVxyTS6ezy6RUhba9CbAjZL1x3iZyv7/view?usp=sharing)

**Step 2: Import the .zip**

- https://localwp.com/help-docs/getting-started/how-to-import-a-wordpress-site-into-local/

**Step 3: Start the `nextjs-wp` site**

**Note:** Make sure your Local URL matches the `LOCAL_WORDPRESS_API_URL` in the frontend `.env` file!

---

## 💻 Frontend Development

### Git Workflow

1. Create a `feature` branch off `staging`
2. Work locally adhereing to coding standards
3. When ready, open a draft Pull Request on Github
4. When finished, fill out the PR template and publish your PR
5. Your PR must pass assertions and deploy successfully
6. After peer review, the PR will be merged back into `staging`
7. Repeat ♻️

### Deployments

[Vercel](https://nextjs-wordpress-starter-gregrickaby.webdevstudios.vercel.app) is connected to this Github repository and will automatically build and deploy. Learn more about [Vercel + Github integration](https://vercel.com/docs/git/vercel-for-github).

### Storybook

To work with Storybook on your Local, run the following command:

```bash
yarn storybook
```

Stories are written in `.mdx` and should be placed next to the component. Learn more about [Storybook](https://storybook.js.org/).

## WebDevStudios Specific Info

The following information pertains to internal tools and workflows at WebDevStudios.

<details>

### WordPress Github

There is a Github repo for the backend. This repo manages plugins and the headless theme. Future projects should probably mimic this setup:

https://github.com/WebDevStudios/nextjs-starter-wordpress

**Note: There is no frontend for WordPress** - But it is running a headless theme which houses `/acf-json` and other headless-related functions.

### WP Engine

There are 3 WordPress environments on WP Engine:

- [Develop](https://nextjsdevstart.wpengine.com/wp-admin/)
- [Staging](https://nextjsstgstart.wpengine.com/wp-admin/)
- [Production](https://nextjs.wpengine.com/wp-admin)

Use the orange "WebDevStudios Login" button to log in.

### Chromatic

This project supports UI review via Chromatic, which is triggered via Github Actions.

View this project's [Chromatic](https://chromatic.com/library?appId=5fe0becf19ad53002147b034&branch=staging) by logging in with your WDS Github account.

### 1Password

All of the credentials are in the following vault:

```text
1Password --> Next.js Starter
```

### Migrate DB Pro

You can use Migrate DB Pro to pull databases and files. Please see 1password for credentials

### Copy WP Engine Environments

WP Engine supports [copying environments](https://wpengine.com/support/copy-site/). This should be done at the end of two week sprints (or as needed).

**The following steps will copy Develop to Staging:**

1. Log into the WP Engine [User Portal](https://my.wpengine.com/sites)
2. Click on [Nextjsstgstart](https://my.wpengine.com/installs/nextjsstgstart)
3. In the top right corner, click the "Copy environment" button
4. Select the options:
   ![screenshot](https://dl.dropbox.com/s/uvzm2trqbgbpyky/Screen%20Shot%202020-12-21%20at%2011.19.34%20AM.png?dl=0)
5. Click "Preview copy" and a modal will appear to let you verify the options
6. Click "Copy environment"

</details>

---

## :octocat: Contributing

[Contributions](https://github.com/WebDevStudios/nextjs-wordpress-starter/blob/main/.github/CONTRIBUTING.md) are welcome. 🍻
