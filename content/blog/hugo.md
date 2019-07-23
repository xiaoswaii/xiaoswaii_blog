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
* 直接來個傳送門 ````https://gohugo.io/getting-started/quick-start/````

## Hosting
* Firebase
* 傳送門： ````https://gohugo.io/hosting-and-deployment/hosting-on-firebase/````
## Travis CI
* 為了能夠在每次git push之後就可以自動推上firebase，不需要再多打一行指令
* 先在部落格根目錄執行````firebase login:ci````，這時候就會產生token
* 在根目錄增加````.travis.yml````
````
language: node_js
node_js:
  - "8"
install:
  - npm install -g firebase-tools
  - wget -O /tmp/hugo.deb https://github.com/gohugoio/hugo/releases/download/v0.55.6/hugo_0.55.6_Linux-64bit.deb
  - sudo dpkg -i /tmp/hugo.deb 
script:
 - echo "Deploy!!"
after_success:
 - hugo && firebase deploy --project <your_project_id> --token <your_token>
 ````

 * 到 travis-ci.org利用github登入，之後再開啟該repo的按鈕，進入setting，在environment variable的部分輸入FIREBASE_TOKEN，然後輸入剛產生的token

## 遇到的小坑
1. 根據documentation上面的 ````hugo server -D````，原來-D是會把draft的東西一起呈現，結果推上去firebase之後發現文章不見了，把````draft:true````拿掉即可。
2. 在進行travis CI設定的時候，遇到每次推上去firebase的時候檔案都是0，因為性子太急，所以以為是什麼bug，但其實只是推上去的速度有點慢稍微等一下就有了:sweat_smile:
