# Nuxt Static Skeleton

Skeleton project for creating a blog with Nuxt-Content and Netlify CMS.

## Notes

Built with:
- [Vue](https://vuejs.org/)
- [Nuxt](https://nuxtjs.org/)
    - [nuxt-content](https://content.nuxtjs.org/)
    - [nuxt-dotenv](https://github.com/nuxt-community/dotenv-module)
    - [vue-moment](https://github.com/brockpetrie/vue-moment)
- [Skeleton CSS](http://getskeleton.com/)
    - Adapted CSS from Skeleton and renamed it to pile-of-bones.css.  Mainly because it's a mess. :)
- [Netlify](https://www.netlify.com/)
    - [Netlify CMS](https://www.netlifycms.org/)
    - [Netlify Sitemap Plugin](https://github.com/netlify-labs/netlify-plugin-sitemap)
- [illlustrations](https://illlustrations.co/)
- A few other packages

## What the project includes

- Home Page (custom)
- About Page (markdown)
- Contact Page (markdown)
- Blog Post List Page(s) (with pagination - default to 5 posts per page)
- Blog Post Single Page
- Google Fonts (Header / Body Text can be defined separately)
- [Flexbox Grid](http://flexboxgrid.com/)
- Modified [Skeleton CSS](http://getskeleton.com/)


## How to set up your own blog using this as a template

*To Do*

1. Fork the Repository
2. Run `npm install` to install the current dependencies
    * Optional: Run `npm run dev` to start a local development server
3. Link to Github. Create a new empty repo (in browser or CLI). Run `git init` to initiate a new project.  Add a remote connection (whatever URL github gave you). `git remote add origin https://github.com/[your-username]/[your-repo-name].git`.
    * To add all files to the project, run `git add *`, then run `git commit -m '[your message here]`
    * To push files to github, run `git push -u origin master`
4. Sign up for Netlify, link to your github.
5. In netlify options,  define:
    * build command: `npm run generate`
    * publish directory: `dist`
