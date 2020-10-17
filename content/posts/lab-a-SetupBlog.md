---
title: "Lab a) : Blog Setup"
description: How I implemented this blog.
date: 2020-09-17
tldr: Followed tutorials, found ressources and used some tricks
draft: false
tags: [labs,hugo]
---
## Why Hugo ?
I decided to use Hugo because of the challenge it offered. At first, because I was getting behind on the lab, I thought of using a platform that would allow me to instantly and easily create a blog like we see so much nowadays. But I decided not to fall in the *Dark Pattern* of laziness and got my hands-on Hugo.
## How I got started ?
At first, I had chosen the [Paper Mod](https://themes.gohugo.io/hugo-papermod/ "Looks good, but not ideal") which had everything to satisfy me : it was clean, minimalist and readable.    
But I had major issues with the quick start linked with the project. Some of the modifications suggested could not be implemented because the author didn’t bother translating them to the toml format.   
Basically I didn't have the freedom to modidy everything I wanted and it bothered me since I wanted this blog to be truly mine.  
  
  Anyways, after several attempts, I decided to start over and found another template that was also a great fit.   
It is the template you’re currently browsing and the built-in tutorial was easy to follow and offered a lot of useful modifications. I also chose it because of the presence of tags which I think will be pretty useful once articles start to pile up.
I also added a browser icon thanks to this [tutorial](https://www.kiroule.com/article/add-favicon-to-hugo-based-website/). As I really wanted to adapt the theme to my taste and make it look personal, I believe the icon is a good way of achieving it.  


{{< figure src="/android-chrome-512x512.png" title="Isn't it beautiful ?" >}}  

Since the template supports the usage of emojis and even if I'm not going to overuse them, knowing how to use them is still a good [opportunity.](https://www.webfx.com/tools/emoji-cheat-sheet/) :muscle:

And finally to help the efficient writing of articles, I found this [site]( https://www.markdownguide.org/basic-syntax/) to be the best. As I had never written any Markdown documents, knowing the basic syntax was a must in order to make my content more readable.

## How did I host my Blog ?
Looking closely at my blog domain, you will notice that it's being hosted on GitHub pages. I chose this way because, since I am going to host the code relative to our labs on GitHub, why not hosting everything there ?  
  
The main issue with the Hugo built-in tutorial is that it does not extensively explain how to host on GitHub while using a theme. As I kept getting the same errors with my initial build (the one of Hugo's quickstart), I decided to do things my way.  
  
**How to host your Hugo Blog, Célestin's way:**
	
1) Follow Hugo's quickstart guide
2) If you want to use a theme, download the zip archive, extract it and copy the folders inside in your main directory (replace duplicate if needed)
3) In your config.toml, add publishDir = "docs"
4) From now on, you can follow Hugo's tutorial : *Deployment of Project Pages from /docs folder on master branch*

My way is not one advised by Hugo's tutorial (at least for the theme part), but it's the only way I found for my website to work. Professionnally speaking, this not an ideal way of building a website, since the docs repository is only a part of the GitHub repo, but since I can build my blog locally at first it is safe to use.  

## What I added to the theme ?

I really wanted to be able to embed local videos on my blog. Obviously, it is possible to directly embed Youtube videos in a markdown file but for fast created content it was much easier for me to host them directly in my repo.  

To do so, I created my own video [shortcode](https://gohugo.io/templates/shortcode-templates/) :
{{< highlight html "linenos=table,linenostart=1" >}}
{{ with .Get "mp4"}}
<figure>
  <video loop autoplay muted controls>
    <source src="{{ . }}" type="video/mp4">
    	{{ end }}
    Your browser does not support the video tag.
  </video>
  {{ with .Get "caption"}}
     <figcaption> <h4> "{{ . }}" </h4></figcaption>
  <style type="center">
  	</style>
</figure>
{{ end }}

{{< / highlight >}}  
  
{{< videofig mp4="/test.mp4" loop=true autoplay=true caption="Yeah, it works" >}}
