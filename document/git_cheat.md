# Gitチートシート的な何か
#### 参考 : [Gitチュートリアル](https://www.atlassian.com/ja/git)

## よく使うリモートとのやり取り編

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

![git fetch](https://github.com/steelplus/HelloWorld/blob/master/document/img/branch_fetch.png "サンプル")

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

現在のブランチに指定ブランチをマージ(noff)
: `git merge --no-ff {branch}`

現在のブランチを指定ブランチにリベース
: `git rebase {branch}`

## - 修正作業編
### - コミットに対して
指定したコミットを打ち消すコミットを作成する
: `git revert {commit}`
### - ステージングエリアに対して
指定ファイルをステージングエリアから削除
: `git reset {file}`

ステージングエリアを直前のコミット時と一致させる
: `git reset`

### - ステージングエリア、作業ディレクトリに対して
直前のコミット状態まで巻き戻す
: `git reset --hard`

### - ブランチに対して
ブランチの先端を指定のコミットまで移動
: `git reset {commit}`

指定のコミット状態まで巻き戻す
: `git reset --hard {commit}`
