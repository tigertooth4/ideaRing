+++
title= "The insufficient vertical holes"
date = "2015-07-09 12:12:00"
draft = false
author = "tt4"
+++

This is just a simple note. The reason for writing this is to remind me things I can put my hands on in the future, regarding 3d printing technique. One is curling, which is more or less common in printing both PLA and ABS, especially for small objects. There's some article around. However, the physical process was unclear for me. So I'd like to save it for future investigation.

Another issue bothers me recently was the insufficient vertical holes. Take deltabot as an example, you can correct the physical dimension of your object by fine tune the diagonal rod length. For me it is the case. However, even I made the profile precisely the size compared with my model, sometimes the inner vertical holes were still smaller than expected. This is something annoying and strange!

Yesterday I've find a link maybe can solve this problem. An auther called *electrocbd* made a [patch](https://github.com/Ultimaker/CuraEngine/pull/94) to CuraEngine by providing a **stretch algorithm**. The results were show below (pics are from his github page).

![](~/12-26-32.jpg)

![](~/12-26-44.jpg)
It will be very interesting to try it! Time to dive deep into the world of slicing algorithm, yeah!
