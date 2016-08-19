# Gitチートシート的な何か
#### 参考 : [Gitチュートリアル](https://www.atlassian.com/ja/git), [こわくない Git](http://www.slideshare.net/kotas/git-15276118)
#### お勧め : [Gitクエスト](http://unit8.net/gq/)

## よく使うリモートとのやり取り編

![git](/document/img/areas.png "各エリアの図")

### - 接続関連のコマンド
接続の作成
: `git remote {name} {url}`

接続の削除
: `git remote rm {name}`

接続名の変更
: `git remote rename {old-name} {new-name}`

### - 取ってくるコマンド
リモートからファイルを取ってくる
: `git fetch {remote} {branch}`

![git fetch](/document/img/branch_fetch.png "fetchの図")

fetch + merge
: `git pull {remote} {branch}`

fetch + rebase
: `git pull --rebase {remote} {branch}`

### - 送るコマンド
作業ファイルをステージングエリアへ送る
: `git add {file or directory}`

ステージングエリアのファイルをローカルリポジトリに送る
: `git commit -m "message"`

ローカルリポジトリのファイルをリモートリポジトリに送る
: `git push {remote} {branch}`

## - ブランチを弄る編

### - ブランチの基本
新規ブランチを作成
: `git branch {branch}`

ブランチ名を変更
: `git branch -m <branch>`

指定のブランチに移動
: `git checkout {branch}`

### - 複数のブランチ間での操作
現在のブランチに指定ブランチをマージ
: `git merge {branch}`

![git merge](/document/img/branch_merge.png "mergeの図")


現在のブランチに指定ブランチをマージ(noff)
: `git merge --no-ff {branch}`

現在のブランチを指定ブランチにリベース
: `git rebase {branch}`

![git rebase](/document/img/branch_rebase.png "rebaseの図")


## - 修正作業編
### - コミットに対して
指定したコミットを打ち消すコミットを作成する
: `git revert {commit}`

直前のコミットの内容を修正したい
: `git commit --amend`
### - ステージングエリアに対して
指定ファイルをステージングエリアから削除
: `git reset {file}`

ステージングエリアを直前のコミット時と一致させる
: `git reset`

### - ステージングエリア、作業ディレクトリに対して
直前のコミット状態まで巻き戻す(ローカルでした編集を無かったことにする)
: `git reset --hard`

### - ブランチに対して
ブランチの先端を指定のコミットまで移動
: `git reset {commit}`

指定のコミット状態まで巻き戻す
: `git reset --hard {commit}`

## - 情報参照編
現在のブランチのログを確認する
: `git reflog`

現在のブランチのコミットログを確認する
: `git log`

| git logオプション | 内容|
|:--|:--|
| `-n {limit}`|{limit}個のログを表示|
| `--oneline`|コミットの内容を1行にして表示|
| `--stat`|改変されたファイルとその行数増減を表示|
| `-p`| 各コミットごとのパッチの内容を表示|
| `--author="{pattern}"`|特定の人物が行ったコミットを検索|
| `--grep="{pattern}"`|特定のコミットメッセージを持つコミットを検索|
| `{since}..{until}`|{since}と{until}の間のコミットを表示|
| `{file}`|{file}を含むコミットを表示|
