## Jekyll Commands

Jekyll is a static site generator. It takes text written in your favorite markup language and uses layouts to create a static website. You can tweak the site’s look and feel, URLs, the data displayed on the page, and more.

### Install all [prerequisites](https://jekyllrb.com/docs/installation/)

### Install the jekyll and bundler gems on Linux Subsystem

```bash
  sudo gem install jekyll bundler
```

### Create a new Jekyll site at ./YourBlogName

```bash
  jekyll new YourBlogName
```

### Change into your new directory

```bash
  cd YourBlogName

```

### Build the site and make it available on a local server

```bash
  bundle exec jekyll serve --livereload
```

### Browse to [http://localhost:4000](http://localhost:4000) to find your site
