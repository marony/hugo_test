# インストール手順

## Hugoのインストール(WSL)

aptだと古い

```
$ wget https://github.com/gohugoio/hugo/releases/download/v0.59.1/hugo_0.59.1_Linux-64bit.deb
$ sudo dpkg -i hugo_0.59.1_Linux-64bit.deb
$ hugo version
Hugo Static Site Generator v0.59.1-D5DAB232 linux/amd64 BuildDate: 2019-10-31T15:21:02Z
```

## プロジェクトの作成

```
$ hugo new site hugo_test
$ cd hugo_test
```

## テーマのインストール

```
$ git init
$ vim .gitignore
/public
$ git submodule add https://github.com/matcornic/hugo-theme-learn.git themes/learn
$ echo 'theme = "learn"' >> config.toml
```

## 日本語化
```
$ sed -i -e 's/"en-us"/"ja"/g' config.toml
```

## 起動確認

```
$ hugo -DEFw server
```

ブラウザで"http://localhost:1313/"を開く
^C

# 新規記事
```
$ hugo new posts/test.md
$ vim posts/test.md
# テストです

テストなんだよ

<div class="mermaid" align="left">
  graph LR;
  A[Hard edge] -->|Link text| B(Round edge)
  B --> C{Decision}
  C -->|One| D[Result one]
  C -->|Two| E[Result two]
</div>
```

```
$ git commit -m 'first commit'
```

# ビルド
```
$ hugo
```

"public/"配下にHTML, CSSなどが出力される

# テーマの更新
```
$ git submodule foreach git pull
```
