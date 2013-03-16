cssunminifier-bookmarklet
=========================
A convenient bookmarklet for unminifying your CSS.

Uses:

* cssbeautifier
* Prism

# Installation

Get it now. Copy/paste:

```
javascript:(function(){(function(){function a(a,b){function s(a){return" "===a||"\n"===a||"   "===a||"\r"===a||"\f"===a}function t(a){return"'"===a||'"'===a}function u(a){return h>="a"&&"z">=h||h>="A"&&"Z">=h||h>="0"&&"9">=h||"-_*.:#".indexOf(a)>=0}function v(){var a;for(a=m;a>0;a-=1)g+=c.indent}function w(){g=r(g),p?g+=" {":(g+="\n",v(),g+="{"),"\n"!==i&&(g+="\n"),m+=1}function x(){var a;m-=1,g=r(g),q&&(a=g.charAt(g.length-1),";"!==a&&"{"!==a&&(g+=";")),g+="\n",v(),g+="}",f.push(g),g=""}var c,f,h,i,j,k,l,m,
n,o,r,d=0,e=a.length,g="",p=!0,q=!1;for(c=arguments.length>1?b:{},c.indent===void 0&&(c.indent="    "),"string"==typeof c.openbrace&&(p="end-of-line"===c.openbrace),"boolean"==typeof c.autosemicolon&&(q=c.autosemicolon),r=String.prototype.trimRight?function(a){return a.trimRight()}:function(a){return a.replace(/\s+$/,"")},l={Start:0,AtRule:1,Block:2,Selector:3,Ruleset:4,Property:5,Separator:6,Expression:7,URL:8},m=0,k=l.Start,o=!1,f=[],a=a.replace(/\r\n/g,"\n");e>d;)if(h=a.charAt(d),i=a.charAt(d+
1),d+=1,t(n))g+=h,h===n&&(n=null),"\\"===h&&i===n&&(g+=i,d+=1);else if(t(h))g+=h,n=h;else if(o)g+=h,"*"===h&&"/"===i&&(o=!1,g+=i,d+=1);else if("/"!==h||"*"!==i){if(k===l.Start){if(0===f.length&&s(h)&&0===g.length)continue;if(" ">=h||h.charCodeAt(0)>=128){k=l.Start,g+=h;continue}if(u(h)||"["===h||"@"===h){if(j=r(g),0===j.length)f.length>0&&(g="\n\n");else if("}"===j.charAt(j.length-1)||";"===j.charAt(j.length-1))g=j+"\n\n";else for(;;){if(i=g.charAt(g.length-1)," "!==i&&9!==i.charCodeAt(0))break;g=
g.substr(0,g.length-1)}g+=h,k="@"===h?l.AtRule:l.Selector;continue}}if(k!==l.AtRule)if(k!==l.Block)if(k!==l.Selector)if(k!==l.Ruleset)if(k!==l.Property)if(k!==l.Separator)if(k!==l.Expression)k===l.URL&&")"===h&&g.charAt("\\"!==g.length-1)?(g+=h,k=l.Expression):g+=h;else{if("}"===h){x(),k=l.Start,m>0&&(k=l.Block);continue}if(";"===h){g=r(g),g+=";\n",k=l.Ruleset;continue}if(g+=h,"("===h&&"l"===g.charAt(g.length-2)&&"r"===g.charAt(g.length-3)&&"u"===g.charAt(g.length-4)){k=l.URL;continue}}else{if(!s(h)){g+=
h,k=l.Expression;continue}t(i)&&(k=l.Expression)}else{if(":"===h){g=r(g),g+=": ",k=l.Expression,s(i)&&(k=l.Separator);continue}if("}"===h){x(),k=l.Start,m>0&&(k=l.Block);continue}g+=h}else{if("}"===h){x(),k=l.Start,m>0&&(k=l.Block);continue}if("\n"===h){g=r(g),g+="\n";continue}if(!s(h)){g=r(g),g+="\n",v(),g+=h,k=l.Property;continue}g+=h}else{if("{"===h){w(),k=l.Ruleset;continue}if("}"===h){x(),k=l.Start;continue}g+=h}else{if(u(h)){if(j=r(g),0===j.length)f.length>0&&(g="\n\n");else if("}"===j.charAt(j.length-
1))g=j+"\n\n";else for(;;){if(i=g.charAt(g.length-1)," "!==i&&9!==i.charCodeAt(0))break;g=g.substr(0,g.length-1)}v(),g+=h,k=l.Selector;continue}if("}"===h){x(),k=l.Start;continue}g+=h}else{if(";"===h){g+=h,k=l.Start;continue}if("{"===h){j=r(g),w(),k="@font-face"===j?l.Ruleset:l.Block;continue}g+=h}}else o=!0,g+=h,g+=i,d+=1;return g=f.join("")+g}"undefined"!=typeof exports?module.exports=exports=a:"object"==typeof window&&(window.cssbeautify=a)})();(function(){var e=/\blang(?:uage)?-(?!\*)(\w+)\b/i,
t=self.Prism={util:{type:function(e){return Object.prototype.toString.call(e).match(/\[object (\w+)\]/)[1]},clone:function(e){var n=t.util.type(e);switch(n){case "Object":var r={};for(var i in e)e.hasOwnProperty(i)&&(r[i]=t.util.clone(e[i]));return r;case "Array":return e.slice()}return e}},languages:{extend:function(e,n){var r=t.util.clone(t.languages[e]);for(var i in n)r[i]=n[i];return r},insertBefore:function(e,n,r,i){i=i||t.languages;var s=i[e],o={};for(var u in s)if(s.hasOwnProperty(u)){if(u==
n)for(var a in r)r.hasOwnProperty(a)&&(o[a]=r[a]);o[u]=s[u]}return i[e]=o},DFS:function(e,n){for(var r in e){n.call(e,r,e[r]);t.util.type(e)==="Object"&&t.languages.DFS(e[r],n)}}},highlightAll:function(e,n){var r=document.querySelectorAll('code[class*="language-"], [class*="language-"] code, code[class*="lang-"], [class*="lang-"] code');for(var i=0,s;s=r[i++];)t.highlightElement(s,e===!0,n)},highlightElement:function(r,i,s){var o,u,a=r;while(a&&!e.test(a.className))a=a.parentNode;if(a){o=(a.className.match(e)||
[,""])[1];u=t.languages[o]}if(!u)return;r.className=r.className.replace(e,"").replace(/\s+/g," ")+" language-"+o;a=r.parentNode;/pre/i.test(a.nodeName)&&(a.className=a.className.replace(e,"").replace(/\s+/g," ")+" language-"+o);var f=r.textContent;if(!f)return;f=f.replace(/&/g,"&amp;").replace(/</g,"&lt;").replace(/>/g,"&gt;").replace(/\u00a0/g," ");var l={element:r,language:o,grammar:u,code:f};t.hooks.run("before-highlight",l);if(i&&self.Worker){var c=new Worker(t.filename);c.onmessage=function(e){l.highlightedCode=
n.stringify(JSON.parse(e.data));l.element.innerHTML=l.highlightedCode;s&&s.call(l.element);t.hooks.run("after-highlight",l)};c.postMessage(JSON.stringify({language:l.language,code:l.code}))}else{l.highlightedCode=t.highlight(l.code,l.grammar);l.element.innerHTML=l.highlightedCode;s&&s.call(r);t.hooks.run("after-highlight",l)}},highlight:function(e,r){return n.stringify(t.tokenize(e,r))},tokenize:function(e,n){var r=t.Token,i=[e],s=n.rest;if(s){for(var o in s)n[o]=s[o];delete n.rest}e:for(var o in n){if(!n.hasOwnProperty(o)||
!n[o])continue;var u=n[o],a=u.inside,f=!!u.lookbehind||0;u=u.pattern||u;for(var l=0;l<i.length;l++){var c=i[l];if(i.length>e.length)break e;if(c instanceof r)continue;u.lastIndex=0;var h=u.exec(c);if(h){f&&(f=h[1].length);var p=h.index-1+f,h=h[0].slice(f),d=h.length,v=p+d,m=c.slice(0,p+1),g=c.slice(v+1),y=[l,1];m&&y.push(m);var b=new r(o,a?t.tokenize(h,a):h);y.push(b);g&&y.push(g);Array.prototype.splice.apply(i,y)}}}return i},hooks:{all:{},add:function(e,n){var r=t.hooks.all;r[e]=r[e]||[];r[e].push(n)},
run:function(e,n){var r=t.hooks.all[e];if(!r||!r.length)return;for(var i=0,s;s=r[i++];)s(n)}}},n=t.Token=function(e,t){this.type=e;this.content=t};n.stringify=function(e){if(typeof e=="string")return e;if(Object.prototype.toString.call(e)=="[object Array]")return e.map(n.stringify).join("");var r={type:e.type,content:n.stringify(e.content),tag:"span",classes:["token",e.type],attributes:{}};r.type=="comment"&&(r.attributes.spellcheck="true");t.hooks.run("wrap",r);var i="";for(var s in r.attributes)i+=
s+'="'+(r.attributes[s]||"")+'"';return"<"+r.tag+' class="'+r.classes.join(" ")+'" '+i+">"+r.content+"</"+r.tag+">"};if(!self.document){self.addEventListener("message",function(e){var n=JSON.parse(e.data),r=n.language,i=n.code;self.postMessage(JSON.stringify(t.tokenize(i,t.languages[r])));self.close()},!1);return}var r=document.getElementsByTagName("script");r=r[r.length-1];if(r){t.filename=r.src;document.addEventListener&&!r.hasAttribute("data-manual")&&document.addEventListener("DOMContentLoaded",
t.highlightAll)}})();Prism.languages.css={comment:/\/\*[\w\W]*?\*\//g,atrule:/@[\w-]+?(\s+[^;{]+)?(?=\s*{|\s*;)/gi,url:/url\((["']?).*?\1\)/gi,selector:/[^\{\}\s][^\{\}]*(?=\s*\{)/g,property:/(\b|\B)[a-z-]+(?=\s*:)/ig,string:/("|')(\\?.)*?\1/g,important:/\B!important\b/gi,ignore:/&(lt|gt|amp);/gi,punctuation:/[\{\};:]/g};Prism.languages.markup&&Prism.languages.insertBefore("markup","tag",{style:{pattern:/(&lt;|<)style[\w\W]*?(>|&gt;)[\w\W]*?(&lt;|<)\/style(>|&gt;)/ig,inside:{tag:{pattern:/(&lt;|<)style[\w\W]*?(>|&gt;)|(&lt;|<)\/style(>|&gt;)/ig,
inside:Prism.languages.markup.tag.inside},rest:Prism.languages.css}}});var prismStyle=document.createElement("style");var beautified=cssbeautify(document.body.textContent,{autosemicolon:true});var highlighted=Prism.highlight(beautified,Prism.languages.css);prismStyle.textContent='code[class*="language-"],pre[class*="language-"]{color:black;text-shadow:0 1px white;font-family:Consolas,Monaco,\'Andale Mono\',monospace;direction:ltr;text-align:left;white-space:pre;word-spacing:normal;-moz-tab-size:4;-o-tab-size:4;tab-size:4;-webkit-hyphens:none;-moz-hyphens:none;-ms-hyphens:none;hyphens:none;}@media print{code[class*="language-"],pre[class*="language-"]{text-shadow:none;}}pre[class*="language-"]{padding:1em;margin:.5em 0;overflow:auto;}:not(pre) > code[class*="language-"],pre[class*="language-"]{background:#f5f2f0;}:not(pre) > code[class*="language-"]{padding:.1em;border-radius:.3em;}.token.comment,.token.prolog,.token.doctype,.token.cdata{color:slategray;}.token.punctuation{color:#999;}.namespace{opacity:.7;}.token.property,.token.tag,.token.boolean,.token.number{color:#905;}.token.selector,.token.attr-name,.token.string{color:#690;}.token.operator,.token.entity,.token.url,.language-css .token.string,.style .token.string{color:#a67f59;background:hsla(0,0%,100%,.5);}.token.atrule,.token.attr-value,.token.keyword{color:#07a;}.token.regex,.token.important{color:#e90;}.token.important{font-weight:bold;}.token.entity{cursor:help;}';
document.head.innerHTML="";document.head.appendChild(prismStyle);document.body.innerHTML="<code><pre>"+highlighted+"</pre></code>"})();
```

A [UserScript](https://github.com/sindresorhus/cssprettifier-userscript) for this project by Sindre Sorhus is also available.

# Screenshots

### Before

```css
.callout{margin:15px 0;padding:10px;font-size:13px;color:#8d8d6d;background:#fffef1;border:1px solid #e5e2c8;border-radius:4px;}.callout strong{font-weight:bold;color:#000;}.callout h2{margin:0;font-size:16px;font-weight:300;}.callout p:last-child{margin-bottom:0;}
```

### After

```css
.callout {
    margin: 15px 0;
    padding: 10px;
    font-size: 13px;
    color: #8d8d6d;
    background: #fffef1;
    border: 1px solid #e5e2c8;
    border-radius: 4px;
}

.callout strong {
    font-weight: bold;
    color: #000;
}

.callout h2 {
    margin: 0;
    font-size: 16px;
    font-weight: 300;
}

.callout p:last-child {
    margin-bottom: 0;
}
```


# License

[MIT License](http://en.wikipedia.org/wiki/MIT_License)
(c) [Addy Osmani](http://addyosmani.com)
