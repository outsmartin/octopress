---
layout: post
title: "fontface compass und Ruby on Rails 3.1"
date: 2011-10-31 10:25
comments: true
categories: rubyonrails, compass, fonts, css, sass
---

Wenn man genug von Arial und Helvetica hat, kann man mit dem schon seit Internet Explorer 5 vorhandenem CSS-Feature @fontface eigene Schriftarten einbetten.

Da ich eine Weile probiert habe hier die Kurzform:

1. Als erstes eine zur Nutzung freigegebene Schriftart finden und zum Beispiel bei [fontsquirrel](http://www.fontsquirrel.com/fontface/generator "Fontsquirrel") in alle benötigten Typen umwandeln lassen.
2. Im Ordner app/assets/ einen neuen Ordner fonts anlegen. Hier rein die Schriftdateien .ttf .eot .otf. Rails sucht seit der neusten Version nach dem fonts Ordner, es muss nichts angepasst werden.
3. Jetzt möchte ich zwei Beispiele zeigen, einmal mit compass (und Sass) und einmal ohne.

Als erstes einmal mit Sass und compass, das ein mixin anbietet :).

{% codeblock fontface mit compass lang:sass %}
@import compass/css3
+font-face("FontName", font-files("fontname.ttf", truetype, "fontname.otf", opentype))
{% endcodeblock %}

Nun das ganze nochmal mit CSS.

{% codeblock mit CSS lang:css %}
@font-face {
  font-family: 'FontName';
  src:src url('fontname.eot');
  src: local('notexistingdummy'),
    url('fontname.woff') format('woff'),
    url('fontname.ttf') format('truetype'),
    url('fontname.svg#webfont') format('svg');
}
{% endcodeblock %}

Viel Spaß damit und auf die Lizenzen achten!
