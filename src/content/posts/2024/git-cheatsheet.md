---
title: 個人的によく忘れるGitの操作メモ
published: 2024-06-24
description: ''
image: ''
tags: ["git"]
category: 'git'
draft: false 
---
## addを取り消す

すべてのaddしたファイルを取り消したい場合は、以下のコマンドを叩く。
```bash
git reset HEAD
```
また、最後にファイルを指定することで、特定のファイルのみaddを取り消すことができます。
```bash
git reset HEAD path/to/file
```

## commitを分割する

まず、git log などで分割したいコミットよりも前のコミットのハッシュを調べます。その後、以下のコマンドを叩きます。
```bash
git rebase -i HASH
```
するとテキストエディタが開くので、分割したいコミットを"pick"から"edit"に変更して保存しましょう。すると、rebaseしている状態になります。
以下のコマンドを叩いて、分割したいコミットでaddしたすべてのファイルを取り消します。
```bash
git reset HEAD~
```
分割したい単位でファイルのaddとcommitを繰り返し、最後に
```bash
git rebase --continue
```
を叩きます。