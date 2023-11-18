---
title: How to deploy Eleventy (11ty) on GitHub Pages
description: This is a post on my tech blog about how to deploy Eleventy (11ty) on GitHub Pages
date: 2023-11-17 21:00:00
tags:
  - eleventy
  - github pages
  - github actions
---

Just like the title says, this is a post about how to deploy Eleventy (11ty) on GitHub Pages. This website is built with Eleventy and deployed on GitHub Pages, so I thought I'd share how I did it.

## What is Eleventy?

Eleventy is a static site generator. It's a tool that takes a bunch of files and turns them into a website. It's similar to Jekyll, Hugo, and Gatsby. It's written in JavaScript and is very flexible. It's also very fast.

## What is GitHub Pages?

GitHub Pages is a free service that lets you host a website on GitHub. It's a great way to host a static website. It's also a great way to host a website that's built with Eleventy.

## Setup new repo

- First, we have to use the eleventy-base-blog template to create a new Eleventy project.
- After finishing the new repo setup, make sure to clone the repo locally

Great! Now you have a GitHub repo for your new blog! Let's go back to your IDE and start editing the files.

First, let's clean up the `package.json` file to reflect the new project name and description:

<script src="https://emgithub.com/embed-v2.js?target=https%3A%2F%2Fgithub.com%2F11ty%2Feleventy-base-blog%2Fblob%2Fmain%2Fpackage.json%23L1-L12&style=default&type=code&showBorder=on&showLineNumbers=on&showFileMeta=on&showFullPath=on&showCopy=on"></script>

For starters, update the `build-ghpages` script to include your repo name in `--pathprefix`. Then, update the other attributes like `name`, `description`, `author`, `repository` and `homepage` to reflect your new project.

To see the changes locally, run `npm run build-ghpages` and then `npm run start`. You should see the site at `http://localhost:8080/`.

Also, make sure to follow the 3 steps from the [demo website](https://eleventy-base-blog.netlify.app/) of the eleventy-base-blog template:

{% image "./steps.png", "Eleventy base blog steps" %}

## Create a new GitHub workflow

Copy the `.github/workflows/gh-pages.yml` below in your new repo, commit and push the changes to the main branch.

<script src="https://emgithub.com/embed-v2.js?target=https%3A%2F%2Fgithub.com%2Fgaler7%2Ftech-blog%2Fblob%2Fmain%2F.github%2Fworkflows%2Feleventy_build.yaml&style=default&type=code&showBorder=on&showLineNumbers=on&showFileMeta=on&showFullPath=on&showCopy=on"></script>

The `peaceiris/actions-gh-pages@v3` action will build the site and push it to the `gh-pages` branch. GitHub Pages will then serve the site from the `gh-pages` branch.

## Commit and push the changes

Commit and push the changes to the main branch. This will trigger the GitHub workflow and build the site. The site will be available at `https://<your-github-username>.github.io/<your-repo-name>/`.

## Conclusion

That's it! You now have a new Eleventy blog hosted on GitHub Pages. You can now start writing blog posts and publish them on your new blog.

## References

- Maarten Tibau: [How to deploy your Eleventy website to GitHub Pages with GitHub Actions](https://maarten.be/blog/20220730/how-to-deploy-your-eleventy-website-to-github-pages-with-github-actions/)
- 11ty GitHub: [eleventy-base-blog](https://github.com/11ty/eleventy-base-blog)
- GitHub workflow file: [eleventy_build.yaml](https://github.com/galer7/tech-blog/blob/main/.github/workflows/eleventy_build.yaml)
