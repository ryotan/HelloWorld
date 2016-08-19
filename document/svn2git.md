# SVN-Gitコマンド対応表

|コマンド|SVN|Git|
|:-|:-|:-|
|追加|svn add {file or dir}|git add {file or dir}|
|コミット|svn commit|git add -> git commit -> git push|
|マージ|svn merge -r {rev1}:{rev2} {url}|git merge {branch}|
|更新|svn update|git pull|
|ファイル変更取消|svn revert {file}|git checkout {file}|
|削除|svn rm {file or dir}|git rm {file}|
|移動|svn mv{file or dir}|git mv {file}|
|スイッチ|svn switch {url}|git checkout {branch}|
|ブランチ作成|svn copy {url} {url}|git branch {branch}|
|ログ|svn log|git log|
