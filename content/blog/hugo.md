---
title: "HUGO處女作"
date: 2019-07-20T14:54:38+08:00
type: post
categories: ["HUGO"]
---

# HUGO

## 前言
在前輩的介紹下，第一次使用了hugo來建置部落格。因為很早就夢寐以求有自己的部落格，但卻又不想使用wordpress之類的，希望自己能夠進行比較多的客製化。所以終於實現了

## 初始化
直接來個傳送門 ````https://gohugo.io/getting-started/quick-start/````

## 遇到的小坑
1. 根據documentation上面的 ````hugo server -D````，原來-D是會把draft的東西一起呈現，結果推上去firebase之後發現文章不見了，把````draft:true````拿掉即可。
