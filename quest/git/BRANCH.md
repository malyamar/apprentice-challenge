# ブランチを利用して開発を進めることができる

Git で管理されているディレクトリに移動してください。

## 1. ブランチの新規作成

feature という名前のブランチを新規作成してください。
```
$ git branch feature
```

## 2. ブランチの切り替え

ローカルリポジトリのブランチを feature ブランチに切り替えてください。
```
$ git checkout feature
```

## 3. マージ

feature ブランチでファイルの変更を行い、コミットしてください。そしてローカルリポジトリのブランチを main ブランチに切り替えてください。

次に、feature ブランチの変更を main ブランチに取り込んでください。なお、他のブランチの変更を取り込むことをマージと言います。

<br>

1. featureブランチ上でファイルの変更、コミット後、mainブランチに切り替える。
```
$ git checkout　main
```
2. featureブランチで変更した内容をマージしていく。
```
$ git merge feature
```

## 4. ブランチの名前の変更

feature ブランチの名前を rename という名前に変更してください。
```
$ git branch -m  feature rename
```
もしくは、今、featureブランチ上にいる場合
```
$ git branch -m rename
```



## 5. ブランチの削除

rename ブランチを削除してください。
```
$ git branch -d rename
```
