---
layout: post
title: "Howto: Setup Ubuntu 12.04 for Ruby/Rails development on an Asus U44S Ultrabook"
date: 2012-09-27 17:43
comments: true
categories: howto, ubuntu, rails, ruby
---
_This article was in the making some time ago, but somehow I managed to delete my notes while installing... so here is another attempt._

starting point
---------------

- The Asus U44S
- Usb Stick with Ubuntu 12.04 64bit (for the 8GB ram) [link](http://www.ubuntu.com/start-download?distro=desktop&bits=64&release=lts) for the lazy

things I wanted
---------------

- a nice stable setup for programming
- vim setup
- rvm setup
- zsh setup

things I did
--------------

First thing to do is install ubuntu + all upgrades it wanted to do and then reboot for the kernel stuff.

Now to get support for the multigpu setup install bumblebee:
    sudo add-apt-repository ppa:bumblebee/stable
    sudo apt-get update
    sudo apt-get install bumblebee bumblebee-nvidia
Then a lot of packages you need to get rolling:
    sudo apt-get install vim-gnome build-essential openssl libreadline6 libreadline6-dev curl git-core zlib1g zlib1g-dev libssl-dev libyaml-dev libsqlite3-dev sqlite3 libxml2-dev libxslt-dev autoconf libc6-dev ncurses-dev automake libtool bison subversion pkg-config

You can skip this one if you are on 32bit. These files are needed to use the android sdk and other things you might want to use.
    sudo apt-get install ia32-libs

Now you can install zsh if you want to have a shell with some modern features like git branch markers and other goodies.
    sudo apt-get install zsh
I like using oh-my-zsh :) read up on it on its [github page](https://github.com/robbyrussell/oh-my-zsh), to install just
    curl -L https://github.com/robbyrussell/oh-my-zsh/raw/master/tools/install.sh | sh
    chsh -s /bin/zsh
I had to restart at this point so ubuntu would accept the new login shell.

Now we install [RVM](http://rvm.io) for convenient per project ruby package and version isolation.
    curl -L https://get.rvm.io | bash -s stable --ruby
Restart the terminal, so your enviroment variables are all set, then
    rvm install 1.9.3
should install the most recent ruby, if you think that is not the most recent version(2.0 is coming soon) just check with a quick
    rvm list known
and install accordingly.

After installing (I had to change the settings of the terminal default profile to use a login shell at this point) you can use
    rvm use 1.9.3 --default
to use this version by default.

    ruby -v
    ruby 1.9.3p194 (2012-04-20 revision 35410) [x86_64-linux]
Should give output like shown.

Now you can
    gem install rails

    rails new my_project
and you are set for using Ruby on Rails :).

Some extras
----------
It is a good idea to set up your dotfiles now, you probably want a:

.zshrc: You already got one by installing ohmyzsh, but there are lots of goodies to add and themes to explore.

.gitconfig: You probably want to write your name or nickname in there.

Here is my config:
```
[alias]
st = status
ci = commit
requests = fetch origin +refs/merge-requests/*:refs/merge-requests/*
unpushed = log origin/master..HEAD

[color]
branch = auto
diff = auto
interactive = auto
status = auto

[user]
name = Your Name
email = your@email.com
```

.vimrc + .vim:

Maybe you already got a setup or you can always look at existing setups, for example:

- [akitaonrails](https://github.com/akitaonrails/vimfiles)
- [krisleech](https://github.com/krisleech/vimfiles)

I want to add some more things I use daily:

[Yakuake:](http://en.wikipedia.org/wiki/Yakuake)
    sudo apt-get install yakuake
I use this one all the time with a slightly changed Solarized theme and I really love it.

The multiload indicator for ubuntu. Somehow it is not in Unity by default...
    sudo add-apt-repository ppa:indicator-multiload/stable-daily
    sudo apt-get update
    sudo apt-get install indicator-multiload

Feel free to give me hints on optimizations for the process.
