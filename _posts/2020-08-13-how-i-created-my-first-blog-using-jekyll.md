---
layout : post
title : "How I created my first blog using Jekyll and Github Pages"
imgpath: "/assets/img/"
---

Jekyll is a static site generator and github pages are used to host the site build using jekyll. If you are comfortable with reading and understanding code, you can easily built a site using these tools. I customized the `minima` theme to suit my needs and for this I had to read about jekyll, liquid template, html, css and markdown. But I am amazed that with some efforts we can easily have a professional looking website. After looking at the result, I think it is well worth the efforts.  

In this blog, I outline the installation steps and how you can customize your blog.

**Important: These installation steps are for Ubuntu 16.04.**
## Installation

### Installing ruby using `rbenv`
Steps to install ruby can be found at [gorails website](https://gorails.com/setup/ubuntu/16.04#ruby-rbenv).
I have copied the steps from there.
{% highlight terminal %}
cd
git clone https://github.com/rbenv/rbenv.git ~/.rbenv
echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bashrc
echo 'eval "$(rbenv init -)"' >> ~/.bashrc
exec $SHELL

git clone https://github.com/rbenv/ruby-build.git ~/.rbenv/plugins/ruby-build
echo 'export PATH="$HOME/.rbenv/plugins/ruby-build/bin:$PATH"' >> ~/.bashrc
exec $SHELL

rbenv install 2.7.1
rbenv global 2.7.1
ruby -v
{% endhighlight %}
The last step is to install Bundler
{% highlight terminal %}
gem install bundler
{% endhighlight %}
Run `rbenv rehash` after installing bundler.

### Installing Jekyll
To install jekyll:
{% highlight terminal %}
gem install jekyll
{% endhighlight %}
Create a new Jekyll site at ./myblog.
{% highlight terminal %}
jekyll new myblog
{% endhighlight %}
You can refer to docs to create jekyll site on [Jekyll website](https://jekyllrb.com/docs/#instructions).  

Website folder will contain some or all of these folders :
- _posts
- _layouts
- _site ...etc.

You can learn about there function from [jekyll docs](https://jekyllrb.com/docs/).  

**_posts** : It contains all the posts. The name of posts should be of the format `YYYY-MM-DD-<post-name>.md`. eg : 2020-08-13-how-i-created-my-blog.md  

Each post contains a front matter which contains title, author, layout or any variable you want to include.
{% highlight yaml %}
---
layout: post
title: My first blog
---
{% endhighlight %}

### Customizing Theme 
To locate the theme's files on your computer run
{% highlight terminal %}
bundle info --path <theme-name>
{% endhighlight %}
`<theme-name>` is the name of the theme. eg : `bundle info --path minima` for minima theme.  

Copy the theme files in the website folder to customize them.  
Learn more about customizing themes from [jekyll theme docs](https://jekyllrb.com/docs/themes/).

#### Using Disqus comments
You can signup on [disqus](https://disqus.com/) and add your site there. Minima has a inbuilt support for disqus comments. 

**What is disqus shortname?**  
If your disqus url is your-shortname.disqus.com, then "your-shortname" is your disqus shortname.  

You have to add your disqus shortname in `config.yaml`.
{% highlight yaml %}
disqus:
  shortname: <disqus-shortname> 
{% endhighlight %}

#### Using Google Analytics
Minima has support for google analytics too.
You can signup on [google analytics](https://analytics.google.com/analytics/web/) and add your tracking id in `config.yaml`.
{% highlight yaml %}
google_analytics: XX-XXXXXXXXX-X
{% endhighlight %}

#### Adding share buttons on each post
You can add share buttons to every post by following the directions given [here](https://jekyllcodex.org/without-plugin/share-buttons/).  
[jekyllcodex](https://jekyllcodex.org/without-plugins/) has some plugin free solutions for jekyll blogs.

#### Changing layout of the blog
`_layouts` folder contains the files related to header, footer, pages format etc. They contains `html` code which can be changed as required or you can add file containing customized layout. This file has to be added to the front matter in your post.

eg. I created `note.html` file to have a different layout than the post. So to get `note` layout for a particular post, its front matter will contain:
{% highlight yaml %}
---
layout: note
---
{% endhighlight %}

### Deploying the site using github pages
Github has excellent documentation on [creating a GitHub Pages site with Jekyll](https://docs.github.com/en/github/working-with-github-pages/creating-a-github-pages-site-with-jekyll).

### Troublshooting tips
- Even after following all instructions from github documentation, site may not be published. There seems to be a bug. The workaround is to choose a theme(even if you don't want to) from repository settings as shown in image below.  
![github troubleshoot]({{ page.imgpath | append: "github-troubleshoot.png" }})
- If you have enabled disqus comments and they are still not showing, add `https://` to `url` defined in config.yaml.

You can fork this blog's repository [here](https://github.com/Eikansh/eikansh.github.io).
