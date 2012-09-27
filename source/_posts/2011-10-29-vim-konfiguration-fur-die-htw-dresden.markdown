---
layout: post
title: "Vim Konfiguration für die HTW Dresden"
date: 2011-10-29 16:54
comments: true
categories: vim
---
In der Firma, in der ich tätig bin, haben wir eine fertige Vim-Umgebung, die über Github zugänglich ist. Da in der HTW aber leider kein Vim mit Ruby-Unterstützung vorhanden ist, habe ich unsere normale Umgebung geforkt und ein bisschen zurechtgestutzt, sodass man damit arbeiten kann.

{% codeblock lang:bash %}
ssh sxxxxx@ilux150.informatik.htw-dresden.de #erstmal auf den ilux verbinden
git clone git://github.com/outsmartin/vimfiles.git ~/.vim
ln -s ~/.vim/vimrc ~/.vimrc
cd ~/.vim
git submodule update --init
{% endcodeblock %}

Nachdem diese Aktionen durchgeführt wurden, lohnt sich der Blick auf [das Github Repository](http://github.com/outsmartin/vimfiles "vimfiles").
Hier findet man in der README Verlinkungen und Anleitungen für die Plugins.

Die wichtigsten Features sind:

* CodeCompletion
* Faltung
* Gutes Syntaxhighlighting
* verbesserte Usability (wenn man Tabs usw benutzt :))
* und vieles weitere mehr...

Viel Spaß mit Vim (und C in DBS3)

