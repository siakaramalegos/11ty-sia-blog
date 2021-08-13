# 11ty-sia-blog

An [Eleventy](https://github.com/11ty/eleventy) blog starter forked from [eleventy-base-blog](https://github.com/11ty/eleventy-base-blog) but with Sia's opinions.

Preview the starter site here: [11ty-sia-blog.netlify.app/](https://11ty-sia-blog.netlify.app/).

A partial list of Sia's changes (opinions):
- Move all source code to the **/src/** directory
- Move most filters to a separate **/src/_11ty/filters.js** file to clean up the **.eleventy.js** config file a bit
- Adds more filters commonly used by Sia
- Inline and minify CSS by default (Note: if you have a lot of CSS, you should probably undo this)

Styling changes:
- More accessible color scheme for code blocks. Uses CSS variables so it's easier to switch it up.
- Adds RSS link to navigation
- A responsive font size and flow system that is more readable, partially based on [Improve the readability of the content on your website](https://piccalil.li/tutorial/improve-the-readability-of-the-content-on-your-website/) by Andy Bell
- A footer at the bottom of the viewport
- Centers post article column with a set max-width of 780px (you should reduce this if you reduce the base font size), with wider image and code blocks, similar to the [Hylia](https://hylia.website/) starter

## Auto-Deploy to Netlify and Vercel

These builders are amazing—in just a few clicks, you'll have your repo and a build set up!

* [Get your own Eleventy web site on Netlify](https://app.netlify.com/start/deploy?repository=https://github.com/siakaramalegos/11ty-sia-blog)
* [Get your own Eleventy web site on Vercel](https://vercel.com/import/project?template=siakaramalegos%2F11ty-sia-blog)

## Getting Started

1. Clone this Repository (or your own if you used one of the auto-deploy links above)
2. Navigate to the directory and install dependencies
  ```
  cd my-blog-name
  npm install
  ```
3. Look at `.eleventy.js` to see if you want to configure any Eleventy options differently.
4. Edit _data/metadata.json
5. Run Eleventy locally on a dev server:
  ```
  npm start
  ```
6. Generate a production build:
  ```
  npm run build
  ```

To run in debug mode:
```
DEBUG=* npx eleventy
```

## Implementation Notes

Prepend all of these file paths with `src/`:

* `about/index.md` shows how to add a content page.
* `posts/` has the blog posts but really they can live in any directory. They need only the `post` tag to be added to this collection.
* Add the `nav` tag to add a template to the top level site navigation. For example, this is in use on `index.njk` and `about/index.md`.
* Content can be any template format (blog posts needn’t be markdown, for example). Configure your supported templates in `.eleventy.js` -> `templateFormats`.
	* Because `css` and `png` are listed in `templateFormats` but are not supported template types, any files with these extensions will be copied without modification to the output (while keeping the same directory structure).
* The blog post feed template is in `feed/feed.njk`. This is also a good example of using a global data files in that it uses `_data/metadata.json`.
* This example uses three layouts:
  * `_includes/layouts/base.njk`: the top level HTML structure
  * `_includes/layouts/home.njk`: the home page template (wrapped into `base.njk`)
  * `_includes/layouts/post.njk`: the blog post template (wrapped into `base.njk`)
* `_includes/postlist.njk` is a Nunjucks include and is a reusable component used to display a list of all the posts. `index.njk` has an example of how to use it.

## Learning Resources

Still new to Eleventy? Try out these learning resources:

- Start from scratch to learn the key features of Eleventy with the [Itsiest, Bitsiest Eleventy Tutorial](https://sia.codes/posts/itsiest-bitsiest-eleventy-tutorial/)
- Understand the fundamentals of templating with [Templating: Eleventy's Superpower](https://www.youtube.com/watch?v=rZyNBd1WgVM) from  Mike Aparicio

Also, get familiar with the 11ty docs!

Once you understand the fundamentals a bit more, dive into data with [Architecting data in Eleventy](https://sia.codes/posts/architecting-data-in-eleventy/). Then you can start building some more complex features like:

- [Optimize Images in Eleventy Using Cloudinary](https://sia.codes/posts/eleventy-and-cloudinary-images/)
- [An In-Depth Tutorial of Webmentions + Eleventy](https://sia.codes/posts/webmentions-eleventy-in-depth/)
- [Show conditional Twitter intents with Eleventy](https://sia.codes/posts/conditional-twitter-intents-with-eleventy/)
