source "https://rubygems.org"

# GitHub Pages 官方支持的 Jekyll 版本与插件集合
# 这样可以确保在 GitHub Pages 环境下直接构建
gem "github-pages", group: :jekyll_plugins

# Jekyll 插件
group :jekyll_plugins do
  gem "jekyll-feed"
  gem "jekyll-seo-tag"
  gem "jekyll-sitemap"
end

# Windows 和 JRuby 不包含 zoneinfo 文件
platforms :mingw, :x64_mingw, :mswin, :jruby do
  gem "tzinfo", ">= 1", "< 3"
  gem "tzinfo-data"
end

# 性能优化（仅 Windows 需要）
gem "wdm", "~> 0.1.1", :platforms => [:mingw, :x64_mingw, :mswin]

# 锁定 http_parser.rb gem 版本
gem "http_parser.rb", "~> 0.6.0", :platforms => [:jruby]
