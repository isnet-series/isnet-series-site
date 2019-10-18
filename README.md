# ISNET Series Website

This guide tells you how to modify and update the ISNET series website if you have permission. Please email Sarah Wesolowski at scwesolowski@salisbury.edu if you have some reason to work on this site.

## Structure

This site is built using the open-source [Hugo static site generator](https://gohugo.io). The website and files live in this repository, and [git submodules](https://git-scm.com/book/en/v2/Git-Tools-Submodules) are used to connect with the isnet-series.github.io repository. You will need both git and hugo installed on your machine to work on the site.

For a general reference on how to set up this site structure, see: [https://gohugo.io/hosting-and-deployment/hosting-on-github/](https://gohugo.io/hosting-and-deployment/hosting-on-github/)

This has only been tested on a Mac so far, and the site build script is a bash script, so this may not work on a Windows machine. But it should work on any Mac or Linux system with the above capabilities.

The hugo site has already been set up in this repository, so you only need to make modifications to the existing pages or add new content, then use the provided build script to build and push the site to git.

## Working on the site

Clone the repository locally using:

`git clone https://github.com/isnet-series/isnet-series-site.git`

The site can be run locally using hugo, simply use

`hugo server` 

in the repository directory. You should then be able to navigate to a local address in your browser.

The site uses a canned hugo theme called `hugo-theme-techdoc`, and theme details can be found at [https://themes.gohugo.io/hugo-theme-techdoc/](https://themes.gohugo.io/hugo-theme-techdoc/).

The content of the site lives in `content/`, where individual folders for each left menu tab exist with their own `_index.md` file. Edit these markdown files to change content, or add more folders to add menu tabs.

For more advanced tasks, see the theme documentation.

## Building and pushing the site

Run the script (you may need to chmod) 

`./deploy.sh`

to build the site to the directory `public/` and push it to git. The website, if your build succeeds, should be available shortly at [isnet-series.github.io](isnet-series.github.io).