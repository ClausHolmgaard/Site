---
title: "Configuration"
date: 2017-12-02T22:07:47+01:00
draft: false
---

### Links
These are the links I used when creating this site. Below I've included what I did, hopefully without forgetting anything. <br>
[Hugo documentation](https://gohugo.io/documentation/) <br>
[Hugo quick start guide](https://gohugo.io/getting-started/quick-start/) <br>
[Hugo Learn theme](https://themes.gohugo.io/hugo-theme-learn/) <br>
[Learn documentation](https://learn.netlify.com/en/) <br>
[Hugo and Jupyter](http://journalpanic.com/post/blogging-with-hugo-and-jupyter-notebooks/)


Hugo init
add theme
theme setup
	color
	logo
serve script for testing
publish...


### Setup

I use two repos, one for the source for site generation, and one with the webpage. <br>
[Source](https://github.com/ClausHolmgaard/Site) <br>
[Webpage](https://github.com/ClausHolmgaard/ClausHolmgaard.github.io) <br>
To set up a github webpage, follow [this](https://pages.github.com/).

Create and clone both repos. <br>
Change directory to source repo directory. <br>
Initialize Hugo site using `hugo new site --force` <br>

Now add the Learn theme as a submodule using `git submodule add https://pages.github.com/ themes/Learn`.<br>
And set `theme = "Learn"` in `config.toml`.

I use the following while developing the site <br>
`hugo server -s ~/git/Site/ -d ~/git/clausholmgaard.github.io/` <br>
To start a local server and generate output in the webpage repo.

### General Config

##### Changing default colors
Add the following to `config.toml`. <br>
```
[params]
themeVariant = "blue"
```

##### Changing Logo
Edit `themes/Learn/layouts/partials/logo.html` and place an html [img] reference.

```
<img src="/logo.png" height="100" width="200">
```



### Adding new content


### Jupyter
Install hugo_jupyter and initialize source directory.
```
pip install hugo_jupyter
hugo_jupyter --init
```

From the [Journal Panic](http://journalpanic.com/post/blogging-with-hugo-and-jupyter-notebooks/) site mentioned before, grab the [fab](https://github.com/knowsuchagency/knowsuchagency.github.io/blob/src/fabfile.py) script. Place fabfile.py in the root of your site source directory.

> Note:
I had some problems with the location of images generated from notebooks, and made some changes to the fabfile. These changes can be found in the fabfile in my source dir.

Create a notebooks directory in the root of your site source directory.

Now run Jupyter and create new notebook in the notebooks directory. <br>
Edit the metadata, and add a block like the following:
```
{
  "front-matter": {
    "title": "Test Notebook",
    "date": "2017-12-03",
    "slug": "test-notebook"
  },
  "hugo-jupyter": {
    "render-to": "content/Configuration/"
  }
```

`fab render_notebooks` will render the notebooks as .md files, and if you're running the server, the changes should be picked up. It should also be possible to use `fav serve` to watch for changes, and render automatically while editing notebooks. I had some problems with this though...



