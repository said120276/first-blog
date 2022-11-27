---
layout: post
title: The Illutated Stable Diffusion
tags: second markdown
categories: demo
---

 الآلة في مجال معالجة اللغة الطبيعية ورؤية الحاسب، حيث يعتقد الكثير من الخبراء أن الترانزفورمر في طريقه لاستبدال أحد أهم الشبكات العصبية المفضلة في مجال التعلم العميق، ألا وهي شبكات ال  RNN.


 ساهم تطور الترانزفومرز في تشكيل حراك ملحوظ في مشهد الذكاء الاصطناعي، حيث أصبح هناك سباق محموم بين عمالقة التقنية في بناء نماذج الذكاء الاصطناعي المولدة ذات المعاملات البليونية. مثلا، السنة الماضية ، أعلنت مايكروسوفت عن نموذجها الضخم   Turing-NLG mode ذو ال ١٧ بليون معامل، تبعتها OpenAI معلنة عن نسخة ضخمة من نموذجها المولد  GPT 3  ١٧٥ بليون معامل!  أخيرا نموذج  DALL·E المذهل الذي ملأ الدنيا وشغل الناس بقدرته الخلاقة على توليد صور من النصوص المدخلة. (المزيد من مقالات منظور السابقة حول النماذج المولدة باستخدام الترانزفورمر - ١، ٢، ٣). 


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
