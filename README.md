# Requestly Blog

### How to install jekyll on MAC OSX 10.11

Steps mentioned here: https://github.com/jekyll/jekyll/issues/3984

    ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
    brew install ruby
    sudo gem install jekyll

### How to Run site on local environment

Added _config_dev.yml to override properties in _config.yml. We can run jekyll like this

    jekyll serve --config _config.yml,_config_dev.yml

In Dev environment we can specify some config which will override the default config.

