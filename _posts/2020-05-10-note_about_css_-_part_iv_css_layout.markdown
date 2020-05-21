---
layout: post
title:      "Note about CSS - part IV(CSS Layout)"
date:       2020-05-10 21:36:34 -0400
permalink:  note_about_css_-_part_iv_css_layout
---


* ### Normal flow  
  In general, elements on webpage lay themselves out according to normal flow (the default setting of each element tag).   
	example:  
	![](http://)
![CSS-NormalFlow](https://github.com/vvlnote/vvlnote.github.io/blob/master/img/CSS-normalflow.png?raw=true)  

```
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>Flexbox 0 — starting code</title>
    <style>
      html {
        font-family: sans-serif;
      }

      body {
        margin: 0;
      }

      header {
        background: purple;
        height: 100px;
      }

      h1 {
        text-align: center;
        color: white;
        line-height: 100px;
        margin: 0;
      }

      article {
        padding: 10px;
        margin: 10px;
        background: aqua;
      }

      
    </style>
  </head>
  <body>
    <header>
      <h1>Normal flow</h1>
    </header>

    <section>
      <article>
        <h2>First article</h2>

        <p>Tacos actually microdosing, pour-over semiotics banjo chicharrones retro fanny pack portland everyday carry vinyl typewriter. Tacos PBR&B pork belly, everyday carry ennui pickled sriracha normcore hashtag polaroid single-origin coffee cold-pressed. PBR&B tattooed trust fund twee, leggings salvia iPhone photo booth health goth gastropub hammock.</p>
      </article>

      <article>
        <h2>Second article</h2>

        <p>Tacos actually microdosing, pour-over semiotics banjo chicharrones retro fanny pack portland everyday carry vinyl typewriter. Tacos PBR&B pork belly, everyday carry ennui pickled sriracha normcore hashtag polaroid single-origin coffee cold-pressed. PBR&B tattooed trust fund twee, leggings salvia iPhone photo booth health goth gastropub hammock.</p>
      </article>

      <article>
        <h2>Third article</h2>

        <p>Tacos actually microdosing, pour-over semiotics banjo chicharrones retro fanny pack portland everyday carry vinyl typewriter. Tacos PBR&B pork belly, everyday carry ennui pickled sriracha normcore hashtag polaroid single-origin coffee cold-pressed. PBR&B tattooed trust fund twee, leggings salvia iPhone photo booth health goth gastropub hammock.</p>

        <p>Cray food truck brunch, XOXO +1 keffiyeh pickled chambray waistcoat ennui. Organic small batch paleo 8-bit. Intelligentsia umami wayfarers pickled, asymmetrical kombucha letterpress kitsch leggings cold-pressed squid chartreuse put a bird on it. Listicle pickled man bun cornhole heirloom art party.</p>
      </article>
    </section>
  </body>
</html>
```  

We can do some modification to change it.   
	
* ### Flextbox  
  We can use   

```
section {
  display: flex;
}
```  
to convert the normal flow into a flexbox style, the result:  

![CSS-flexbox](https://github.com/vvlnote/vvlnote.github.io/blob/master/img/CSS-Flexbox.png?raw=true)  

```
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>Flexbox 0 — starting code</title>
    <style>
      html {
        font-family: sans-serif;
      }

      body {
        margin: 0;
      }

      header {
        background: purple;
        height: 100px;
      }

      h1 {
        text-align: center;
        color: white;
        line-height: 100px;
        margin: 0;
      }

      article {
        padding: 10px;
        margin: 10px;
        background: aqua;
      }

      section{
			   display: flex;
			}
      
    </style>
  </head>
```   

Flexbox is considered to set one-dimensional layouts, which is either veritical column or horizontal row direction. By default the flexbox displayed as horizontal row direction.  Flextbox layout is most appropriate to teh components of an application and small-scale layouts.

In general, when we start to use Flexbox model, we would need to first define a flext container.  The reason is that flextbox is a whole module and not a signle property, it involves a set of properties. Some of them are meant to be set on the container (parent element, known as 'flex container') whereas the others are meant to be set on the child items (flex items).

**Properties for the flex container:**
display: flex;  
flex-direction: row | row-reverse | column | column-reverse;  
flex-wrap: nowrap | wrap | wrap-reverse;  
flex-flow: column wrap;  
justify-content: flext-start | flex-end | center | space-between | space-around | space-evenly | start | end | left | right ... + safe | unsafe;   
algin-items: stretch | flext-start | flex-end | center | baseline | first bseline | last baseline | start | end | self-end + ... safe | unsafe;  
align-content: flex-start | flex-end | center | space-between | space-around | space-evenly | stretch | start | end | baseline | first baseline | last baseline + ... safe | unsafe;  

Properties for the flex items:  
order: 5;
flex-grow: 4;
flex-shrink: 3;
flex-basis:  | auto;
flex: none | [ <'flex-grow'> <'flex-shrink'> ? || <'flex-basis'> ]  
Note:  
* flex is the shorthand for 'flex-grow', 'flex-shrink' and 'flex-basis' combined. the 'flex-shrink' and 'flex-basis' are optional. 
* It is recommended to use this shorthand property rather than set the individual properties.   
algin-self: auto | flex-start | flex-end | center | baseline | stretch;  
Note: float, clear and vertical-align have no effect on a flex item.  


Reference: 
[A Complete Guide to Flexbox](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)

