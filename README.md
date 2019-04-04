# Project 7 - WordPress Pentesting

Time spent: **5** hours spent in total

> Objective: Find, analyze, recreate, and document **five vulnerabilities** affecting an old version of WordPress

## Pentesting Report

## 1. (Required) Authenticated Stored Cross-Site Scripting (XSS) in YouTube URL Embeds

-Summary: While using the Youtube URL embed shortcode, we can insert a script inside the youtube url for an XSS attack. The reason why   this works is because the HTML sanitzation function ( wp_kses() ) does not look for escape sequences such as the ones used in the gif, "\x3c". 

-Vulnerability type: XSS
-Tested in version: 4.2
-Fixed in version: 4.2.13

![](example1.gif)

-Steps to recreate:
   1) Go to the Posts tool in the toolbar and click on "Add New"
   2) Insert developed code attack, as shown in the GIF, into the body of the page
   3) Press "Update" then "View Post" 
   
-Affected source code: 
  [Link 1](https://core.trac.wordpress.org/changeset/40160/trunk/src/wp-includes/embed.php?old=38361&old_path=trunk%2Fsrc%2Fwp-includes%2Fembed.php)
  
  
## 2. (Required)  Legacy Theme Preview Cross-Site Scripting (XSS)

-Summary: This is caused due to a bug from a function (preview_theme()). If you are logged in as an administrator, you can visit one of the site's pages which use a few extra "$get" parameters that results in setting preview_theme_ob_filter as ob_Start callback function. As soon as ob_start() gets all of the pages content it will call preview_theme_ob_filter() to get all the HTML links. This removes the onlick=" event handler from the link tags.

-Vulnerability type: XSS
-Tested in version: 4.2
-Fixed in version: 4.2.4

![](example2.gif)

-Steps to recreate:
   1) Go to the Posts tool in the toolbar and click on "Add New"
   2) Insert developed code attack, as shown in the GIF, into the body of the page
   3) Press "Update" then "View Post" 
   
-Affected source code: 
  [Link 1](https://core.trac.wordpress.org/changeset/33549)
  
  
## 3. (Required) Authenticated Shortcode Tags Cross-Site Scripting (XSS)
 
 -Summary: By manipulating unclosed HTML elemtns that are in shortcode tags, an experienced hacker can execute an XSS attack by inserting a certain script insde the tag.
 
-Vulnerability type: XSS
-Tested in version: 4.2
-Fixed in version: 4.2.5

 
 ![](example3.gif)

-Steps to recreate:
   1) Go to the Posts tool in the toolbar and click on "Add New"
   2) Insert developed code attack, as shown in the GIF, into the body of the page
   3) Press "Update" then "View Post" 
   
   -Affected source code: 
  [Link 1](http://blog.checkpoint.com/2015/09/15/finding-vulnerabilities-in-core-wordpress-a-bug-hunters-trilogy-part-iii-ultimatum/)
 
## Resources

- [WordPress Source Browser](https://core.trac.wordpress.org/browser/)
- [WordPress Developer Reference](https://developer.wordpress.org/reference/)

GIFs created with [LiceCap](http://www.cockos.com/licecap/).

## License

    Copyright [2019] [Steven Melamud]

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

        http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
