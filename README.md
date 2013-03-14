cssunminifier-bookmarklet
=========================

A bookmarklet for the browser based on cssunminifier allowing you to turn this:

![](http://i.imgur.com/x59Jyg0.png)

into this:

![](http://i.imgur.com/gTvjUBs.png)

Get it now. Copy/paste:

```shell
javascript:(function () { 'use strict';   function unminCSS(code, tab) { var tabSize = 4; var space = '';   if (typeof tab === 'string'){ tab = /^\d+$/.test(tab) ? parseInt(tab,10) : tabSize; };  if (typeof tab === 'undefined'){ tab = tabSize; }   if (tab < 0){ tab = tabSize; }   code = code .split('\t').join(' ') .replace(/\s*{\s*/g, ' {\n ') .replace(/;\s*/g, ';\n ') .replace(/,\s*/g, ', ') .replace(/[ ]*}\s*/g, '}\n') .replace(/\}\s*(.+)/g, '}\n$1') .replace(/\n ([^:]+):\s*/g, '\n  $1: ') .replace(/([A-z0-9\)])}/g, '$1;\n}');   if (tab !== 4) { for (;tab != 0;tab--) { space += ' '; } code = code.replace(/\n /g, '\n'+space) }   return code; }   document.body.innerHTML = '<pre>' + unminCSS(document.body.innerText) + '</pre>'; })();
```