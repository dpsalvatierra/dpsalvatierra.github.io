# dpsalvatierra.github.io

Personal GitHub Pages site for Daniel Salvatierra, built with Jekyll and a dark Midnight-based theme.

## Local development

```bash
bundle install
bundle exec jekyll serve
```

## Setup and run (Ubuntu)

```bash
sudo apt update
sudo apt install ruby-full build-essential zlib1g-dev
echo 'export GEM_HOME="$HOME/gems"' >> ~/.bashrc
echo 'export PATH="$HOME/gems/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc
gem install bundler
cd /path/to/your/jekyll-site
bundle install
bundle exec jekyll serve
```

## Setup and run (PowerShell)

```powershell
gem install bundler
cd C:\path\to\your\jekyll-site
bundle install
bundle exec jekyll serve
```

The site is configured for GitHub Pages using `jekyll-theme-midnight` with custom layout and styling.
