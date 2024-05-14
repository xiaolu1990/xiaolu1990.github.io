---
title: Cheatsheet for New Posts
tags: [Template, Cheatsheet]
style: fill
color: primary
description: Markdown syntax that lists the supported elements supported by the jekyll theme portfolYOU.
---

Source: [portfolYOU Elements](https://youssefraafatnasry.github.io/portfolYOU/elements/)

Listing of some useful code snippets that I use to create new posts. The basic markdown syntax are natively supported and can be used without any problem, thus I am not going to introduce in this cheatsheet.

# Headers
```
# H1  
## H2  
### H3  
#### H4  
##### H5  
###### H6   
```

# Emphasis
```markdown
- Italics, with *asterisks* or _underscores_.  
- Bold, with **asterisks** or __underscores__.  
- Bold & italics, with **asterisks and _underscores_**.  
- Strikethrough, uses two tildes. ~~Scratch this.~~
```
- Italics, with *asterisks* or _underscores_.  
- Bold, with **asterisks** or __underscores__.  
- Bold & italics, with **asterisks and _underscores_**.  
- Strikethrough, uses two tildes. ~~Scratch this.~~

# Highlight Text
```css
/* Using inline CSS method */

/* Highlight text font only */
<span style="color: Tomato;">I am highlighted text with font colort</span>

/* Highlight text with background fill only */
<span style="background-color: #90EE90;">I am highlighted text with background fill</span>

/* Highlight text font with background fill both */
<span style="background-color: #90EE90;"><span style="color: #000000;">I am highlighted text with both font and background</span></span>
```

<span style="color: Tomato;">I am highlighted text with font color</span>

<span style="background-color: #90EE90;">I am highlighted text with background fill</span>

<span style="background-color: #90EE90;"><span style="color: #000000;">I am highlighted text with both font and background</span></span>

# Figures with Caption
```html
<!-- Insert figure with caption using remote theme figure element -->
{% raw %}
{% include elements/figure.html image="https://images.unsplash.com/photo-1605315024122-7fd363c1f7ab?q=80&w=2077&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D" caption="Tomato" %}
{% endraw %}
```
{% include elements/figure.html image="https://images.unsplash.com/photo-1605315024122-7fd363c1f7ab?q=80&w=2077&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D" caption="Tomato" %}

# Album

```html
<!-- Using the remote theme carousel element -->
{% raw %}
{% capture carousel_images %}
https://images.unsplash.com/photo-1624821588855-a3ffb0b050ff?q=80&w=2070&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D
https://images.unsplash.com/photo-1598404148538-f0bc11a5515c?q=80&w=2070&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D
https://images.unsplash.com/photo-1509042509830-d41df2156c6f?q=80&w=1895&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D
{% endcapture %}
{% include elements/carousel.html %}
{% endraw %}
```

{% capture carousel_images %}
https://images.unsplash.com/photo-1624821588855-a3ffb0b050ff?q=80&w=2070&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D
https://images.unsplash.com/photo-1598404148538-f0bc11a5515c?q=80&w=2070&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D
https://images.unsplash.com/photo-1509042509830-d41df2156c6f?q=80&w=1895&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D
{% endcapture %}
{% include elements/carousel.html %}

# Video
```html
<!-- Using the remote theme videos element -->
{% raw %}
{% include elements/video.html id="17uxyViao2s" %}
{% endraw %}
```
> **How to get a YouTube video ID?**  
The video ID is located in the URL of the video page, right after the `v=` parameter.  
For exmaple, the URL of the video is: https://www.youtube.com/watch?v=17uxyViao2s  
Therefore, the ID of the video is 17uxyViao2s

{% include elements/video.html id="17uxyViao2s" %}
