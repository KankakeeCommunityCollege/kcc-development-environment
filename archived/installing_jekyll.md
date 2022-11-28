# Installing Jekyll

Official documentation found at <https://jekyllrb.com/>.

Install both Bundler and Jekyll using the following command in terminal:

```bash
gem install bundler jekyll
```

## Upgrading Ruby Versions

**Remember, that Bundler and Jekyll are bound to the ruby version used during their installations. If a new stable release of ruby comes out, you need install Bundler and Jekyll again with `gem install bundler jekyll`**

## Verify Jekyll Installation

You can verify your jekyll installation by generating a new default jekyll site.

```bash
cd ~/repositories
jekyll new default-jekyll-site
cd default-jekyll-site
bundle exec jekyll serve --watch
# Open http://localhost:4000/ in your browser
```
