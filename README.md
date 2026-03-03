# Readme

## 前提
- chezmoi
- git

### 基本概念
chezmoiにはレイヤーがある
1. 実際に使うファイル(local)
    * ~/.zshrc
2. chezmoiの管理用のsource
    * ~/.local.share/chezmoi


## Usecase
### 新規でchezmoi管理下にdotfilesを登録 or 変更を反映
変更を chezmoi の source に取り込む
```sh
chezmoi add ~/.zshrc
# ~/.zshrc  →  ~/.local/share/chezmoi/dot_zshrc 新規作成or上書き
```

差分の確認
```sh
chezmoi diff # chezmoi cd && git diffでもいい
```

gitにcommit
```sh
chezmoi cd
git add .
git commit -m "update zsh"
git push
```

### 別のpcでdotfilesを反映させる
```sh
chezmoi init --apply <this repo url>
# 内部的にやっていること：
# 1. リポジトリを clone
# 2. ~/.local/share/chezmoi に配置
# 3. chezmoi apply 実行
# 4. ~/.zshrc などを生成
```

### すでに初期化済みの別マシン
```sh
chezmoi update
# git pull
# chezmoi apply
```