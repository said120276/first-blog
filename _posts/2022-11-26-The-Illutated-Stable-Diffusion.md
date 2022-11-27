---
layout: post
title: The Illutated Stable Diffusion
tags: second markdown
categories: demo
---

(V2 Nov 2022: Updated images for more precise description of forward diffusion thanks to Jeremy and Hamel. A few more images in this version)

AI image generation is the most recent AI capability blowing people’s minds (mine included). The ability to create striking visuals from text descriptions has a magical quality to it and points clearly to a shift in how humans create art. The release of Stable Diffusion is a clear milestone in this development because it made a high-performance model available to the masses (performance in terms of image quality, as well as speed and relatively low resource/memory requirements).

After experimenting with AI image generation, you may start to wonder how it works.

This is a gentle introduction to how Stable Diffusion works.
![this an image of cat](https://alwankids.com/img/classes/calss-img1.jpg)

-----------------------

> block list 
> is lik this
> end this 

table is like this :

|cat |dog |horse|
|---|---|---|
|2 |3 |6 |

Stable Diffusion is versatile in that it can be used in a number of different ways. Let’s focus at first on image generation from text only (text2img). The image above shows an example text input and the resulting generated image (The actual complete prompt is here). Aside from text to image, another main way of using it is by making it alter images (so inputs are text + image).

## The Components of Stable Diffusion

Stable Diffusion is a system made up of several components and models. It is not one monolithic model.

As we look under the hood, the first observation we can make is that there’s a text-understanding component that translates the text information into a numeric representation that captures the ideas in the text.
![image here](http://jalammar.github.io/images/stable-diffusion/stable-diffusion-text-understanding-component-image-generation.png)

The image generator goes through two stages:

## 1- Image information creator

This component is the secret sauce of Stable Diffusion. It’s where a lot of the performance gain over previous models is achieved.

This component runs for multiple steps to generate image information. This is the steps parameter in Stable Diffusion interfaces and libraries which often defaults to 50 or 100.

The image information creator works completely in the image information space (or latent space). We’ll talk more about what that means later in the post. This property makes it faster than previous diffusion models that worked in pixel space. In technical terms, this component is made up of a UNet neural network and a scheduling algorithm.

## 2- Image Decoder

The image decoder paints a picture from the information it got from the information creator. It runs only once at the end of the process to produce the final pixel image.
