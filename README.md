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


## rebase


## stash


## tag


## submodule


## git-flow and GitHub flow


## wiki

## Octotree


## zenhub


## Revert


## Reset
