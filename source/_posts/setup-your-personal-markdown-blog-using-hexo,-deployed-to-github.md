title: Setup your personal markdown blog using hexo, deployed to github
date: 2013-11-25 15:13:07
tags:
---
***
To setup your personal programming blog (based on markdown) using hexo, you can follow these steps :   

*   ### **Installing Git, Node and Hexo** ###   
This is a pretty straight forward step so i will assume that you have them installed.   
The [documentation here](http://zespia.tw/hexo/docs/index.html) can be helful to you for the same.

*   ### **Initialize you blog** ###   
To setup you blog, you need to create an initial hexo project.   
``` bash Initialize hexo project http://zespia.tw/hexo/docs/setup.html Source Article
$ hexo init <project-name> # If you installed hexo globally
$ node_modules/hexo/bin/hexo init <project-name> # If you installed hexo locally
# Example $ hexo init ksck23
```   
> After this, you should see a &lt;project-name&gt; folder with the following structure.
.
├── _config.yml
├── package.json
├── scaffolds
├&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;├── draft.md
├&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;├── page.md
├&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;├── photo.md
├&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└── post.md
├── source
├&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;├── _drafts
├&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└── _posts
├── themes
├&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└── ...
└── README.md

*   ### **Configure your blog** ###   
The configuration file is a straight forward yaml file located at **&lt;project-folder&gt;/_config.yml**   
You can follow the sample code written below to configure yours.   

``` yaml Configure hexo project http://zespia.tw/hexo/docs/configuration.html Source Article
# Hexo Configuration
# Site
title: Hackers Hub
subtitle: A hackers blog
description:
author: Shiva Chandra Kumar K
email: ksck23@gmail.com
# follow IETF format codes given here
# http://www.w3.org/International/articles/language-tags
language: en
# URL
url: http://&ltblog-name&gt.github.io
root: /
permalink: :year/:month/:day/:title/
tag_dir: tags
archive_dir: archives
category_dir: categories
code_dir: downloads/code
# Writing
new_post_name: :title.md # File name of new posts
default_layout: post
auto_spacing: false # Add spaces between asian characters and western characters
titlecase: false # Transform title into titlecase
external_link: true # Open external links in new tab
max_open_file: 100
multi_thread: true
filename_case: 0
render_drafts: false
highlight:
  enable: true
  line_number: true
  tab_replace:
# Category & Tag
default_category: uncategorized
category_map:
tag_map:
# Archives
## 2: Enable pagination
## 1: Disable pagination
## 0: Fully Disable
archive: 2
category: 2
tag: 2
# Server
## Hexo uses Connect as a server
## You can customize the logger format as defined in
## http://www.senchalabs.org/connect/logger.html
port: 4000
logger: false
logger_format:
# Date / Time format
## Hexo uses Moment.js to parse and display date
## You can customize the date format as defined in
## http://momentjs.com/docs/#/displaying/format/
date_format: MMM D YYYY
time_format: H:mm:ss
# Pagination
## Set per_page to 0 to disable pagination
per_page: 10
pagination_dir: page
# Disqus
disqus_shortname:
# Extensions
## Plugins: https://github.com/tommy351/hexo/wiki/Plugins
plugins:
# Add this line to generate an atom feed for your blog
- hexo-generator-feed
## Themes: https://github.com/tommy351/hexo/wiki/Themes
# Add this line to choose a custom theme for your blog
theme: greyshade
exclude_generator:
# Deployment
## Docs: http://zespia.tw/hexo/docs/deploy.html
deploy:
  type: github # To deploy you blog to github
  repository: https://github.com/<github-username>/<github-username>.github.io.git
  #Example : https://github.com/ksck23/ksck23.github.io.git
```

*   ### **Installing a theme** ###   
You can skip this step, if the theme you configured was the default **light** theme.
In other case, run the following :   
``` bash Get your hexo theme http://zespia.tw/hexo/docs/setup.html Source Article
$ cd <project-folder>/themes
$ git clone <git-url-of-theme> <theme-name>
# Example $ git clone https://github.com/nuklly/hexo-theme-greyshade.git greyshade
```   
Once the cloning is done, ensure that the theme is configured in the **&lt;project-folder&gt;/_config.yml**.
Any theme specific configuration can be set in the **&lt;project-folder&gt;/themes/&lt;theme-name&gt;/_config.yml** file

*   ### **Installing a plugin** ###   
You can install a plugin in a simple step :   
``` bash Get a plugin https://github.com/tommy351/hexo/wiki/Plugins Source Article
$ npm install <plugin-name> --save
# Example $ npm install hexo-generator-feed --save
```   
Once the installation is done, ensure that the plugin is configured in the **&lt;project-folder&gt;/_config.yml**.

*   ### **Create a blog post** ###   
You can create a blog post :   
``` bash Create a post 
$ hexo new <post-title> # If you installed hexo globally
$ node_modules/hexo/bin/hexo new <post-title> # If you installed hexo locally
# Example $ hexo new "Hello World"
```   
After you create your post, you should see a file named **&lt;post-title&gt;** in **&lt;project-folder&gt;/source/_posts** folder.   
You can edit the file to write your post data in markdown. The [documentation](http://daringfireball.net/projects/markdown/syntax) on markdown syntax could help you write better markdown code. A nice [online markdown editor](http://markable.in/editor/) called markable can help you validate your markdown code.   

*   ### **To generate the static files** ###   
You need to generate the static HTML/CSS/JS files for your blog post :   
``` bash Generate Static files 
$ hexo generate # If you installed hexo globally
$ node_modules/hexo/bin/hexo generate # If you installed hexo locally
# Example $ hexo generate
```   

*   ### **To run a server locally** ###   
You can run a local server to checkout your blog. It will start based on the config parameters given in the **&lt;project-folder&gt;/_config.yml** file :   
``` bash Start a local server 
$ hexo server # If you installed hexo globally
$ node_modules/hexo/bin/hexo server # If you installed hexo locally
# Example $ hexo server
```   

*   ### **To deploy your blog to github repository** ###   
You need to create a repository named **&lt;github-username&gt;.github.io** in github before this step.   
Also ensure that the github repository url is configured properly in the **&lt;project-folder&gt;/_config.yml**   
Then do :   
``` bash Deploy code to github repository 
$ hexo deploy # If you installed hexo globally
$ node_modules/hexo/bin/hexo deploy # If you installed hexo locally
# Example $ hexo deploy
```   
Now, you should be able to see your blog static files in the **&lt;github-username&gt;.github.io** repository. After 5-10 mins you should be able to see your blog hosted at http://&lt;github-username&gt;.github.io and your blogs atom feed at http://&lt;github-username&gt;.github.io/atom.xml   

###That's it. Happy Blogging hackers !!!!!!