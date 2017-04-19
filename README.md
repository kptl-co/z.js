<img height="125" width="125" src="https://mn.tn/dev/z.js/z.js.png" alt=""/>

<h2><a href="https://mn.tn/dev/z.js">z.js</a>&mdash;turns content (in)visible*</h2>
*using Unicode's ZW(N)Js <small>(\u200c, \u200d)</small>


<h3>Demos</h3>
https://mn.tn/dev/z.js/blog-demo.php<br/>
https://mn.tn/dev/z.js/website.php (See source)<br/>


<h3>Changelog/Usage</h3>

<pre>
/*

CHANGELOG
0.3 (Sept 2015)
* Add AMD Loader and Node.js support (define and require)
* Export RC4 function too
* Beautify code

z.js(DAT [, PWD=false, MSK/RAW=false])

DAT -- content to hide/restore
       (z.js only parses \u200c and \u200d)
PWD -- Password (RC4)
MSK -- MASK; default (TRUE): ▉
       (optional 2nd char: Parts-mode (see Example 2.1))
RAW -- if TRUE, returns raw data instead of FALSE if encrypted


*/


1.   //Basic example; results in zero-width (168=("8"*8)+("11"*8)+"16")
     var tmp='Something'+z.js('hello world')+' inside';
     console.log(tmp,tmp.length); → Something‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‌‍‍‌‍‌‌‌‌‍‍‌‌‍‌‍‌‍‍‌‍‍‌‌‌‍‍‌‍‍‌‌‌‍‍‌‍‍‍‍‌‌‍‌‌‌‌‌‌‍‍‍‌‍‍‍‌‍‍‌‍‍‍‍‌‍‍‍‌‌‍‌‌‍‍‌‍‍‌‌‌‍‍‌‌‍‌‌ inside 168
     console.log(z.js(tmp)); → hello world


2.   //Masking; tags excluded
     console.log(z.js('hello &lt;em&gt;<em>world</em>&lt;/em&gt;',false,'*')) → *‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‌‍‍‌‍‌‌‌‌‍‍‌‌‍‌‍‌‍‍‌‍‍‌‌‌‍‍‌‍‍‌‌‌‍‍‌‍‍‍‍‌‌‍‌‌‌‌‌‌‌‍‍‍‍‌‌‌‍‍‌‌‍‌‍‌‍‍‌‍‍‌‍‌‌‍‍‍‍‍‌‌‍‍‍‌‍‍‍‌‍‍‌‍‍‍‍‌‍‍‍‌‌‍‌‌‍‍‌‍‍‌‌‌‍‍‌‌‍‌‌‌‌‍‍‍‍‌‌‌‌‍‌‍‍‍‍‌‍‍‌‌‍‌‍‌‍‍‌‍‍‌‍‌‌‍‍‍‍‍‌**** *****


2.1  //'Parts'-mode (2nd MSK-char); keeps wrapped content
     var tmp=z.js('hides only *this* and *that*.',false,'**');
     console.log(tmp) → hides only ‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌*‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‌‍‍‍‌‍‌‌‌‍‍‌‍‌‌‌‌‍‍‌‍‌‌‍‌‍‍‍‌‌‍‍*** and ‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌*‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‌‍‍‍‌‍‌‌‌‍‍‌‍‌‌‌‌‍‍‌‌‌‌‍‌‍‍‍‌‍‌‌***.
     console.log(z.js(tmp)) → hides only this and that.
     console.log(z.js('Re*pla*ce aster*iks-wrapped* with DOTS',false,'.*'));
     → Re‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌.‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‌‍‍‍‌‌‌‌‌‍‍‌‍‍‌‌‌‍‍‌‌‌‌‍..ce aster‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌.‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‌‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‍‌‍‍‌‍‌‌‍‌‍‍‌‍‌‍‍‌‍‍‍‌‌‍‍‌‌‍‌‍‍‌‍‌‍‍‍‌‍‍‍‌‍‍‍‌‌‍‌‌‍‍‌‌‌‌‍‌‍‍‍‌‌‌‌‌‍‍‍‌‌‌‌‌‍‍‌‌‍‌‍‌‍‍‌‌‍‌‌.......... with DOTS
     console.log(z.js('@hello wo@rld@',false,'@@')); → false "(?)"



3.  //Encrypt
    console.log(z.js(z.js('hello world','yay'),'nay')); → false
    console.log(z.js(z.js('hello world','yay'),'yay')) → hello world
    console.log(z.js(z.js('hello world','yay'),'nay',true)) → }Ý©ÒEû@ó[î(L    ¥

</pre>

