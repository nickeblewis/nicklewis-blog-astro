---
title: Cloudinary and Lightroom
heroImage: "https://res.cloudinary.com/dqpknoetx/image/upload/w_1200/v1421699526/_DSC1123-2_cw7m43.jpg"
description: "Having recently discovered a cloudinary add-on that enables you to use Lightroom filters, I had to explore further"
alt: 'astro'
layout: '../../layouts/BlogPost.astro'
publishDate: 'March 24 2021'
author: 'Nick'
---

![](https://res.cloudinary.com/dqpknoetx/image/upload/w_640/v1421699526/_DSC8931_lttnkn.jpg)


<p class="lead">Having recently discovered a cloudinary add-on that enables you to use Lightroom filters, I had to explore further...</p>

Digging through my Cloudinary account, I decided to search for an image I had totally forgotten about and I came across this photo. It was taken using my old Nikon camera and would have been taken in the workshops at the fabulous Bluebell Line railway in Sussex. The first image is not processed but is being loaded from Cloudinary rather than using same server as this site which is hosted on Netlify. 

I want to explore what we can do with images using just Cloudinary and then introducing the [Lightroom add-on](https://cloudinary.com/documentation/adobe_photoshop_lightroom_addon) that you can install via your [Cloudinary](https://cloudinary.com) account, asuming you already have one. 

## Using Shortcodes

Just at the point I was writing this article I decided that it would perhaps be easier to use shortcodes, rather than using the longer form URLs that look like this:

``https://res.cloudinary.com/dqpknoetx/image/upload/v1423155364/train.jpg``

Google is your friend, I did a search and came across [juanfernandes/eleventy-plugin-cloudinary](https://github.com/juanfernandes/eleventy-plugin-cloudinary) a plugin that does what I need. So having followed the instructions in setting it up, the previous URL can now be expressed instead as:

```md
  cloudinaryImage
    "v1423155364/train.jpg",
    "f_auto",
    "The train"
```

## The basic image with no manipulations

![](https://res.cloudinary.com/dqpknoetx/image/upload/w_640/v1423155364/train.jpg}

Dependent on where you are and your internet speed, this first image may take longer to load than any other on this page because it is not scaled, nor compressed in any way. However once it is cached on the DNS that underpins Cloudinary, it will load faster.

## Let's scale it a bit

```md
  cloudinaryImage
    "v1423155364/train.jpg",
    "c_scale,w_320",
    "The train"
```

![](https://res.cloudinary.com/dqpknoetx/image/upload/w_640/v1423155364/train.jpg)

In this instance I have added ``c_scale,w_320`` into the URL path, which essentially specifies the image filter of ``c_scale`` and that we want to scale the image to 320 along the width. It scales the height to be proportional to this.

## Let's add Lightroom to the mix

It is important to note here that I have activated the Lightroom add-on within Cloudinary without which the following wouldn't work. 

```md
  cloudinaryImage
    "v1423155364/train.jpg",
    "c_scale,e_lightroom:VignetteAmount_-50:Saturation_-100,w_640",
    "Lightroom and Cloudinary"
```

``e_lightroom:VignetteAmount_-50:Saturation_-100`` we use Lightroom's Vignette preset and drop the saturation down 100%, effectively turning the photo black and white.

![](https://res.cloudinary.com/dqpknoetx/image/upload/w_640/v1423155364/train.jpg)

## To finish off

Some more images from my Cloudinary account with some Lightroom filters or presets applied. Including this gorgeous shot of Rome from one of the hilltops.

```md
  cloudinaryImage
    "v1616535212/_DSC1123-2_cw7m43.jpg",
    "c_scale,e_lightroom:Saturation_-100,w_1200",
    "Rome in black and white"
```

![](https://res.cloudinary.com/dqpknoetx/image/upload/w_640/v1616535212/_DSC1123-2_cw7m43.jpg)

A recent shot taken in Rotherwick, Hampshire with a little bit of extra vibrance added in Lightroom

```md
  cloudinaryImage
    "v1616541707/_DSC8949_vr7gsp.jpg",
    "c_scale,e_lightroom:Vibrance_16,w_1200",
    "Rotherwick Village Hall"
```

![](https://res.cloudinary.com/dqpknoetx/image/upload/w_640/v1616541707/_DSC8949_vr7gsp.jpg)

That is not actually all there is to say about these tools, so what I'd rather do is, introduce more features I find useful through Cloudinary in future photographic posts. I will be sharing those with you soon.
