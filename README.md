# git-github
Note to remember git and github.

GitとGithubの使い方を忘れないために<br>
- https://qiita.com/seiji1997/items/c2d9ee9e8e85d8493243

米国AIエンジニアblog<br>
- https://datawokagaku.com/category/%e8%ac%9b%e5%ba%a7%e4%b8%80%e8%a6%a7/git%e8%b6%85%e5%85%a5%e9%96%80%e8%ac%9b%e5%ba%a7/


## SSHでアクセスする
- ローカルからGitHubにアクセスする際にpassword認証ができなくなる
- https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token

1. SSHキーをローカルに作成

```
$ ssh-keygen -t ed25519 -C ”<email>”
SSHキーが~/.ssh/ id_ed25519と， SSHキーが~/.ssh/ id_ed25519.pubに作成される
$ eval "$(ssh-agent -s)”
ssh-agentを起動させる 
$ subl ~/.ssh/config
~/.ssh/configファイルを編集する
$ ssh-add -K ~/.ssh/id_ed25519
SSHキーをssh-agentに登録する
```

2. SSHキーをGitHubに登録

```
$ pbcopy < ~/.ssh/id_ed25519.pub
    公開鍵をクリップボードにコピー
```

- GitHub上でSeIngs -> SSH and GPG keys -> New SSH key ->公開鍵をペースト

## Oh My Zsh, Powerlevel10k
- https://ohmyz.sh/
- https://github.com/romkatv/powerlevel10k

## basic workflow

- 1リポジトリをコピー(clone)
- 2ブランチ(update-readme)を作成
- 3README.mdを更新しコミット
- 4ローカルリポをリモートリポ に反映する(push)
- 5update-readmeブランチを mainブランチにマージする
- 6リモーリポをローカルリポ に反映する(pull)
- 7不要なブランチを削除する

## branch and merge

```
ブランチ一覧を表示する(現在の作業ブランチを確認) 
$ git branch
新しいブランチを切る
$ git branch <branch-name>
作業するブランチを切り替える
$ git checkout <branch-name>
作業状態を確認する
$ git status
作業内容をStaging areaに追加する 
$ git add <filename>
特定のファイルの作業内容をStaging areaに追加する 
$ git add .
Staging areaの内容をコミットする
$ git commit -m ”<commit message>”
コミット履歴を表示する
$ git log
リモートリポの更新をローカルリポに反映する
$ git pull <remote_ref> <branchname>
mainブランチに移動する(checkout する) 
$ git checkout main
リモートリポのmainブランチをpullする 
$ git pull origin main
特定のブランチを削除する
$ git branch -d <branch-name>
```

## diff

```
Working directoryとローカルリポのdiffを確認する
$ git diff HEAD
Staging areaとローカルリポのdiffを確認する
$ git diff --staged HEAD
特定のファイルのdiffを確認する 
$ git diff -- <filename>
commit同士のdiffを確認する 
$ git diff <commitID> <commitID>
ブランチ同士のdiffを確認する
$ git diff <branchname> <branchname>
mergetoolを使ってコンフリクトに対処してマージする 
$ git mergetool
```

## rebase

```
pull時にmergeではなくrebaseする
$ git pull --rebase <remote_ref> <branchname>
デフォルトでpull時にrebaseする 
$ git config --global pull.rebase true
pull時にmergeではなくrebaseする
$ git pull --rebase <remote_ref> <branchname>
rebaseによるコンフリクト $ git mergetool
$ git rebase --conUnue
```

## stash

```
stashする
$ git stash
stashした内容を一覧表示する 
$ git stash list
stashした内容をWorking directoryに戻す 
$ git stash apply
作業内容をstashから消す 
$ git stash drop
untrackファイルの作業内容も含めてstashする 
$ git stash -u
特定のstashの内容を確認する
$ git stash show stash@{<i>}
$git stash applyと$git stash dropを同時に行う 
$ git stash pop
gibgnoreしているファイルの作業内容も含めてstashする 
$ git stash -a
stashする際にメッセージを添える 
$ git stash save “<message>”
特定のstashだけapplyする
$ git stash apply stash@{<i>}
特定のstashだけdropする
$ git stash drop stash@{<i>}
```

## tag

```
最新のコミットにラベル付けをする
$ git tag <tagname>
tag一覧を表示する
$ git tag --list
指定したtagを削除する
$ git tag --delete <tagname>
annotated tagを作成する
$ git tag -a <tagname>
tag同士のdiffを表示する
$ git diff <tagname1> <tagname2>
特定のコミットにtagを付ける 
$ git tag -a <tagname> <commitID>
指定のtagをリモートリポに送信する
$ git push <remote_ref> <tagname>
全てのtag情報をpushする
$ git push <remote_ref> --tags
特定のtag情報をリモートリポ上から削除する 
$ git push <remote_ref> :<tagname>
コードを特定のバージョンの状態にする
$ git checkout tags/<tagname>
全てのtag情報をローカルに取得する 
$git fetch --tags --all

```

## submodule

```
プロジェクトにsubmoduleを追加する 
$git submodule add <submodule_url>
submoduleの初期化(inibalize)をする
$git submodule init
submoduleの更新(update)をする 
$git submodule update
clone時に$git submodule initと$git submodule updateを実行する
$git clone --recurse-submodules <url>
全てのsubmoduleに対して特定のgitコマンドを実行する 
$git submodule foreach ’<git command>’
全てのsubmoduleでコマンドを実行する 
$git submodule foreach ‘<command>’
```

## git-flow and GitHub flow
- [A successful Git branching model](https://nvie.com/posts/a-successful-git-branching-model/)
- [Git-flow](https://qiita.com/KosukeSone/items/514dd24828b485c69a05)
- [GitHub flow](https://docs.github.com/en/get-started/quickstart/github-flow)

## wiki
• README.mdの追加情報を記載する
• プロジェクトの使い方や，設計や原理など，プロジェクトに関する⻑いコンテンツをwikiに書く 
• Markdownで書くことが可能

## Octotree
• Chrome Extension
• GithubのプロジェクトをTree形式でファイルやフォルダをナビゲーションできる
• Privateリポジトリには使えない

## zenhub
• ブラウザのExtension
• アジャイル開発における「カンバン」をGithubで実現 
• Github Issueをカンバン化してくれる

## Revert

```
指定したコミットの一つ前に状態が戻るようにrevert commitを作成しコミットする
$git revert <commitID>
```

## Reset

```
指定したコミットにHEADが移動する.(それまでのコミットは全て無くなる)
$git reset <commitID>
```

