source "https://rubygems.org"

gem "jekyll", "~> 4.4.1"

# Force version 0.4.3 to fix the 'configure_sass' error
gem "jekyll-remote-theme", "~> 0.4.3"
gem "faraday-retry"
gem "jekyll-sass-converter", ">= 2.0"
gem "logger"

group :jekyll_plugins do
  gem "jekyll-paginate"
  gem "jekyll-sitemap"
  gem "jekyll-gist"
  gem "jekyll-feed"
  gem "jemoji"
  gem "jekyll-include-cache"
  gem "jekyll-algolia"
  gem "jekyll-seo-tag"
end

platforms :mingw, :x64_mingw, :mswin, :jruby do
  gem "tzinfo", ">= 1", "< 3"
  gem "tzinfo-data"
end

gem "wdm", "~> 0.1", :platforms => [:mingw, :x64_mingw, :mswin]
gem "http_parser.rb", "~> 0.6.0", :platforms => [:jruby]
