+++
title = "githubのユーザー名変更と、それに伴うあれこれをしました。"
date = 2021-02-13T16:15:51+09:00
images = []
tags = ["github"]
categories = ["未分類"]
draft = true
+++

昨日このログ用のドメインを取ったとき、名前+llogでドメインを取ろうとしたところ、よく使ってる名前のものは既に埋まっていたので次点でたまに使うkit+llogにしたのですが、githubのidと合わないので変更しました。
<!--more-->
## 変更点
[GitHubのユーザー名を変更してみた - 一から勉強させてください](https://dangerous-animal141.hatenablog.com/entry/2014/05/05/000000)
[GitHub ユーザ名の変更 - GitHub Docs](https://docs.github.com/ja/github/setting-up-and-managing-your-github-user-account/changing-your-github-username)

上記を参考にユーザー名とローカルリポジトリのoriginを変更しました。

gitのユーザー名を変更
`$ git config --global user.name 'new_name'`
変更の確認
`$ git config --global -l`
各ローカルのリポジトリ達のoriginを変更
`$ git remote set-url origin git@github.com:new_name/repository_name.git`

他にどこに影響が出るのか思い出せないので、また問題が出たら修正することにしようと思います。
実際に問題が出たらまたユーザー名を変えたことを思い出せずに数時間格闘するような気もします。

半年ぶりくらいにgithubに新しいリポジトリを作ったら、たぶんBLMの流れだと思うのですが、masterブランチがmainブランチに変わっていました。こういうところちゃんとすぐ対応するのすばらしいなと思いました。