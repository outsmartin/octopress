---
layout: post
title: "Solarized Colorscheme für Vim"
date: 2011-11-21 18:45
comments: true
categories: vim, colorscheme
---

Seit kurzem benutze ich das Solarized Colorscheme für Vim und will hier eine kurze Installationsanleitung posten.

* Ihr benötigt die Colorscheme Dateien. Wenn ihr pathogen für Vim benutzt, könnt ihr das github Repository clonen:

{% codeblock %}
git clone git://github.com/altercation/vim-colors-solarized.git ~/.vim/bundle/vim-colors-solarized
{% endcodeblock %}

* Da das Colorscheme 256 Farben benötigt, muss das Terminal ebenfalls darauf abgestimmt werden. Dazu entweder ein passendes Farbschema herunterladen oder wie in meinem Fall(ich nutze yakuake) in der .bashrc folgende Zeile einfügen:

{% codeblock %}
    export TERM='xterm-256color'
{% endcodeblock %}

* Jetzt kann in der .vimrc das colorscheme aktiviert werden:

{% codeblock %}    
    let g:solarized_termcolors=256 "benoetigt für xterm mit 256 farben
    set background=dark "mit light gibts einen hellen hintergrund
    colorscheme solarized
{% endcodeblock %}

Viel Spaß mit eurem sonnigen Design.
