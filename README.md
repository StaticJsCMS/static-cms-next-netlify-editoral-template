![Next.js blogging template for Static CMS on Netlify](https://user-images.githubusercontent.com/1388138/197867836-58de8783-9712-4196-937f-4101b1327612.png)

[![Netlify Status](https://api.netlify.com/api/v1/badges/94f05f8f-379a-4dd5-885f-ac2a0cb8a012/deploy-status)](https://app.netlify.com/sites/static-cms-next-editorial/deploys)
[![MADE BY Next.js](https://img.shields.io/badge/MADE%20BY%20Next.js-000000.svg?style=flat&logo=Next.js&labelColor=000)](https://nextjs.org/)

Next.js blogging template for Netlify is a boilerplate for building blogs with only Netlify stacks.

There are some boilerplate or tutorials for the combination of Next.js and Netlify on GitHub. These resources have documentation and good tutorial to get started Next.js and Netlify quickly, but they are too simple to build blogs with standard features like tagging.

Next.js blogging template for Netlify has already implemented these standard features for building blogs with only using Next.js and Netlify stacks.

## Demo

Deploy on your environment by clicking here:

[![Deploy to Netlify](https://www.netlify.com/img/deploy/button.svg)](https://app.netlify.com/start/deploy?repository=https://github.com/StaticJsCMS/static-cms-next-netlify-editoral-template&stack=cms)

Or access the following demo sites:

- [Production](https://next-editorial.staticcms.org/)
- [Staging](https://next-editorial-staging.staticcms.org/)

## Editorial Workflow Setup

There are two build commands `yarn build` (or `npm run build`) and `yarn build:staging` (or `npm run build:staging`).

- `build` - Builds the production version of the site. Posts marked as `draft` are excluded from the build.
- `build:staging` - Builds the staging version of the site. All posts are included in the build, regardless of `draft` status.

### Setup

1. Create a deployment that uses the `build` command. This is your production site.
2. Create a deployment that uses the `build:staging` command. This is your staging site to view draft changes.

## Features

- **Tagging**: organizes content by tags
- **Author**: displays author names who write a post
- **Pagination**: limits the number of posts per page
- **CMS**: built with CMS to allow editors modifying content with the quickest way
- **SEO optimized**: built-in metadata like JSON-LD
- **Shortcode**: extends content writing with React component like WordPress shortcodes

## Dependencies

- [TypeScript](https://www.typescriptlang.org/)
- [Next.js](https://nextjs.org/)
- [Netlify](https://www.netlify.com/)
- [MDX](https://mdxjs.com/)

## Getting started

To create your blog using the template, open your terminal, `cd` into the directory you'd like to create the app in,
and run the following command:

```
npx create-next-app your-blog --example "https://github.com/StaticJsCMS/static-cms-next-netlify-editoral-template"
```

After that, set up your project as following the Netlify blog:

[A Step-by-Step Guide: Deploying on Netlify](https://www.netlify.com/blog/2016/09/29/a-step-by-step-guide-deploying-on-netlify/)

## Customization

This template is just a template and a boilerplate in which users can customize anything after the project was cloned and started.
The following instructions introduce common customization points like adding new metadata or applying a new design theme.

### Styling pages by a customized theme

All source codes related to the blog are under [components](/src/components) and [pages](/src/pages) directory.
You can modify it freely if you want to apply your design theme.
All components use [styled-jsx](https://github.com/vercel/styled-jsx) and [css-modules](https://github.com/css-modules/css-modules) to define their styles, but you can choose any styling libraries for designing your theme.

The directory tree containing the blog source code are described below:

```
meta: yaml files defining metadata like authors or tags
public: images, favicons and other static assets
src
├── assets: other assets using inside of components
├── components: pieces of components consisting of pages
├── content: mdx files for each post page
├── lib: project libraries like data fetching or pagination
└── pages: page components managing by Next.js
```

### Organizing content by categories

The category metadata that associates with content have the same relationship with the authors' one.
Then reference these implementations for adding new metadata:

- [public/admin/config.yml](/public/admin/config.yml#L51): author metadata definition for Static CMS
- [src/lib/authors.tsx](/src/lib/authors.ts): fetches metadata and defines utility functions for components
- [meta/authors.yml](/src/meta/authors.yml): author content managed by Static CMS
- [src/components/PostLayout.tsx](/src/components/PostLayout.tsx): displays author content for each page

You understood they have four steps to add the category metadata on your project after you read the above source codes:

1. Define the category metadata on the above Static CMS config file
2. Create an empty file named with `categories.yml` under [meta](/src/meta/) directory
3. Create a new module for fetching category metadata
4. Display the category metadata on [src/components/PostLayout.tsx](/src/components/PostLayout.tsx#L75) or other components you want

It is all you have to do. After that, you can access Static CMS and create new categories at any time.

### Locale settings for Static CMS

Modify [config.yml](/public/admin/config.yml) and
[index.html](/public/admin/index.html) under [public/admin](/public/admin/) directory
as following instructions:

[Static CMS - Configuration Options #Locale](https://staticjscms.netlify.app/docs/configuration-options/#locale)

## References

- [Static CMS Documentation](https://staticjscms.netlify.app/docs/intro/)
- [Building a Markdown blog with Next 9.4 and Netlify](https://www.netlify.com/blog/2020/05/04/building-a-markdown-blog-with-next-9.4-and-netlify/)
- [Hugo Theme - Codex](https://github.com/jakewies/hugo-theme-codex)
- [Next.js Starter Template for TypeScript](https://github.com/vercel/next-learn-starter/tree/master/typescript-final)
- [Building Blog with NextJS and Static CMS](https://dev.to/mefaba/building-blog-with-nextjs-and-netlify-cms-fom)
- [Unicons](https://github.com/Iconscout/unicons)

## License

MIT
