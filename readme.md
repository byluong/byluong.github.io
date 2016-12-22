# Some build notes:

to build locally:  
run `bundle exec jekyll serve --no-watch`, then go to `http://localhost:4000/`  
## Gemfile:
```
source "https://rubygems.org"

gem "jekyll", "~> 3.3.0"
gem "minimal-mistakes-jekyll"
```
## _config.yml (add to line 7)
```
theme: minimal-mistakes-jekyll
```


to use github:  
delete _site folder  
## Gemfile:
```
source "https://rubygems.org"

gem "github-pages", group: :jekyll_plugins

group :jekyll_plugins do
  gem "jekyll-paginate"
  gem "jekyll-sitemap"
  gem "jekyll-gist"
  gem "jekyll-feed"
  gem "jemoji"
end
```
## _config.yml (remove line 7)
```
theme: minimal-mistakes-jekyll
```