---
title: "Gallery Demo"
date: "2025-02-14"
draft: true
---

This is a local-only demo page for image layout and sizing.

Manual sizing (classes):

<img class="w-60 center" src="assets/a.jpg" alt="60%">

<img class="w-40 center" src="assets/b.jpg" alt="40%">

Gallery (auto cols):

{{< gallery images="assets/a.jpg,assets/b.jpg,assets/c.jpg" captions="A,B,C" >}}

Gallery with fixed cols:

{{< gallery images="assets/a.jpg,assets/b.jpg,assets/c.jpg,assets/d.jpg" cols="2" >}}

Masonry layout:

{{< gallery images="assets/a.jpg,assets/b.jpg,assets/c.jpg,assets/d.jpg,assets/e.jpg" layout="masonry" cols="3" >}}

WeChat layout (with zoom):

{{< gallery images="assets/a.jpg,assets/b.jpg,assets/c.jpg,assets/d.jpg,assets/e.jpg" layout="wechat" >}}

Forced ratio (4/3):

{{< gallery images="assets/a.jpg,assets/b.jpg,assets/c.jpg,assets/d.jpg" ratio="4/3" >}}

Figure shortcode:

{{< figure src="assets/e.jpg" caption="Figure caption example" >}}

Video sizing:

{{< video src="assets/demo.mp4" poster="assets/poster.jpg" preload="metadata" lazy="true" >}}

<video class="w-60 center" controls preload="metadata" poster="assets/poster.jpg">
  <source src="assets/demo.mp4" type="video/mp4">
</video>

WeChat video:

{{< wechat-video src="assets/demo.mp4" poster="assets/poster.jpg" ratio="4/3" width="60%" lazy="true" >}}
