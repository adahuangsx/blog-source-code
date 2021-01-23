---
title: Hexo Memo
tags: Hexo
toc: true # this is for the right-up corner wiki-like categories.
---
## Create a new post

``` bash
$ hexo new|n "My New Post"
```

More info: [Writing](https://hexo.io/docs/writing.html)

## Tips for writing blogs

* Note that the images or other resources should be put in "/themes/.../images/" in the first place, because the `hexo clean` will erase the "/public/" folder. Meanwhile, `hexo g|generate` will generate all the resources into "/public/".

* The path of images should be as if in "/public/" folder, which means the path looks like "/images/.../image.jpg".

* The path of images should replace special characters like spaces with "%20".

* Changing posts supports hot deployment, which means I do not need to run `hexo s` again, but changing other resources like images does not. 

* Remember to renew the source files in Github.

## Run server

``` bash
$ hexo server|s
```

More info: [Server](https://hexo.io/docs/server.html)

## Generate static files

``` bash
$ hexo generate|g
```

More info: [Generating](https://hexo.io/docs/generating.html)

## Deploy to remote sites

``` bash
$ hexo deploy|d
```

More info: [Deployment](https://hexo.io/docs/one-command-deployment.html)
