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

## Submodule information

This repository connects to the `isnet-series.github.io` repository via the directory `/public`. This directory is where hugo builds the site. Using git submodules, the created `/public` directory has a different remote than this repository. The contents of this directory are pushed to the `isnet-series.github.io` repository. This directly updates the live site.

### Troubleshooting if site is not building

If the site is not updating properly, it's possible that the submodule has not been added correctly. You may have to completely remove the submodule and then add it again. Try the following steps to remove the submodule (from the answer to [this stackexchange question](https://stackoverflow.com/questions/20929336/git-submodule-add-a-git-directory-is-found-locally-issue))

1. Run `git rm --cached public` and `rm -rf public` to clean up the builds from git and the directory.
2. Delete the relevant lines from the .gitmodules file. e.g. delete these:
```
[submodule "public"]
	path = public
	url = https://github.com/isnet-series/isnet-series.github.io.git
	branch = master
```
3. Delete the relevant section from `.git/config`. e.g. delete these:
```
[submodule "public"]
        url = https://github.com/isnet-series/isnet-series.github.io.git
        active = true
```
4. Finally, remove the following `rm -rf .git/modules/public`

## Building and pushing the site

Run the script (you may need to chmod) 

`./deploy.sh`

to build the site to the directory `public/` and push it to git. The website, if your build succeeds, should be available shortly at [isnet-series.github.io](isnet-series.github.io).
