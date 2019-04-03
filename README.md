# CyberSecurity-Week7

1)(Required) Authenticated Stored Cross-Site Scripting (XSS) in YouTube URL Embeds

[Summary]:  While using the Youtube URL embed shortcode, we can insert a script inside the youtube url for an XSS attack. The reason why this works is because the HTML sanitzation function ( wp_kses() ) does not look for escape sequences such as the ones used in the gif, "\x3c". 

-Vulnerability types: XSS
-Tested in version: 4.2
-Fixed in version: 4.2.13
