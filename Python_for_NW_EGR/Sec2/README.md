# 2. Using Git and Github
> 注意<br>この章は内容が難しいので飛ばしてもよいです。ただ、gitはタスクの保存、管理に便利なので使えると良いです

[Pyton for network engineer](https://pyneng.readthedocs.io/en/latest/index.html "Python for network engineer")にはたくさんのタスクがあるため、それをどこかに保存する必要があります。

Git/Githubはその選択肢の一つです。<br>
Gitを扱うとバージョン管理が容易に行えるため、変更点を確認しやすいです。

以下三点、実践的な問題に焦点を当てまとめていきます。
- gitとGithubの始め方
- 基本的な設定方法
- 情報、及び変更点の確認方法

ここでは理論的な部分にあまり触れずに進めていきます。
<br>GitやGithubが日常になったタイミングでもっと勉強すると良いです。
Gitはなんの役に立つのでしょうか。
- 設定と設定の変更を保存する
- ドキュメントとその全バージョンを保存する
- スキームとその全バージョンを保存する
- コードとそのバージョンを保存する

Githubは上記のようなものを一元的に保存できますが、それらのリソースは他の人にも公開されることを考慮する必要があります。Githubには一応プライベートリポジトリもありますが、こちらもパスワードなどの情報は含んでいないほうが良いです

もちろん、Githubの主な用途は、様々なプロジェクトのコードを配置することですが、他にも以下のような使い方ができます。

- Webサイト用のホスティング(Github Pages)
- オンラインプレゼンテーションのためのホスティングとそのためのツール(GitPitch)
- 書籍やドキュメントを出版するためのプラットフォーム

# Git fundamentals
GitはGNU GPL v2ライセンスで公開され、広く利用されている分散型バージョン管理システム(Version Control System, VCS)です。以下のことができます
- ファイル変更のトラッキング
- 同じファイルの複数バージョンを保存する
- 変更の取り消し
- だれがいつどのような変更を行ったか記録する

Git は、変更をリポジトリ全体のスナップショットとして保存します。このスナップショットは、各 "commit "コマンドの後に作成されます。

gitは以下のようにインストールします
```
sudo apt-get install git
```

## Gitの初期設定
Gitを使い始めるには、ローカルリポジトリとGithubリポジトリを同期するために使用するユーザ名と電子メールを以下のコマンドで指定する必要があります。
```
$ git config --global user.name "username"
$ git config --global user.email "username.user@example.com"
```
usernameとusername.user@example.comは適宜変更してください
<br>以下のコマンドで設定内容を確認できます
```
git config --list
```

## レポジトリの初期化
以下のコマンドでリポジトリの初期化ができます
```
[~/tools/first_repo]
$ git init
Initialized empty Git repository in /home/vagrant/tools/first_repo/.git/
```
