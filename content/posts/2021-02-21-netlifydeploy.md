+++
title = "HUGOを呑気に旧石器時代の方法でNetlifyでデプロイしようとしたらだめだった話。"
date = 2021-02-21T16:09:19+09:00
slug = ""
images = []
tags = ["hugo","netlify"]
categories = ["未分類"]
draft = false
+++
<!--more-->
HUGOで作ったサイトを今回久しぶりにNetlifyでホストしようと思って、旧石器時代の記憶のとおりに

```
Repository：github.com/ccels/ccelsar  
Base directory：Not set  
Build command：hugo -D  
Publish directory：public  
```

とご機嫌で設定したら、  

```
Error message
Command failed with exit code 255: hugo -D
```

と冷たく言われたので、半べそかきながら新時代の方法に対応しました。
<!--more-->

やり方はすべて[ここ](https://gohugo.io/hosting-and-deployment/hosting-on-netlify/)に英語で書いてありますが、英語なのでやり方を簡単にメモしておきます。  
[Host on Netlify | Hugo](https://gohugo.io/hosting-and-deployment/hosting-on-netlify/)

## その① netlify.tomlを作る
ルートディレクトリに作る。内容はこう。

```netlify.toml
[build]
publish = "public"
command = "hugo --gc --minify"

[context.production.environment]
HUGO_VERSION = "0.81.0"
HUGO_ENV = "production"
HUGO_ENABLEGITINFO = "true"

[context.split1]
command = "hugo --gc --minify --enableGitInfo"

[context.split1.environment]
HUGO_VERSION = "0.81.0"
HUGO_ENV = "production"

[context.deploy-preview]
command = "hugo --gc --minify --buildFuture -b $DEPLOY_PRIME_URL"

[context.deploy-preview.environment]
HUGO_VERSION = "0.81.0"

[context.branch-deploy]
command = "hugo --gc --minify -b $DEPLOY_PRIME_URL"

[context.branch-deploy.environment]
HUGO_VERSION = "0.81.0"

[context.next.environment]
HUGO_ENABLEGITINFO = "true"

```

## ②Netlify側の設定をする。
Build commandを変更する。

```
Build command：hugo --gc --minify 
```

おしまい。
今回やった時は`netlify.toml`をpushした時点でNetlifyのビルドが始まってデプロイに成功していたので、もしかすると Build command の再設定は必要ないのかもしれないが念の為設定しておきました。ヨシ！