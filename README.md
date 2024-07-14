# git-github
Note to remember git and github.

GitとGithubの使い方を忘れないために<br>
https://qiita.com/seiji1997/items/c2d9ee9e8e85d8493243

# oh my zsh


# Oh My Zshを使ったコマンドラインのカスタマイズ手順

## 1. Oh My Zshのインストール
まずは、Oh My Zshをインストールします。以下のコマンドを実行してください：

```sh
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

## 2. Powerlevel10kテーマのインストール
`Powerlevel10k`テーマは非常にカスタマイズ性が高く、見やすいプロンプトを提供します。

```sh
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git $ZSH_CUSTOM/themes/powerlevel10k
```

次に、`~/.zshrc`ファイルを編集してテーマを変更します：

```sh
nano ~/.zshrc
```

`ZSH_THEME`の行を以下のように変更します：

```sh
ZSH_THEME="powerlevel10k/powerlevel10k"
```

設定を反映するために、ターミナルを再起動するか以下のコマンドを実行します：

```sh
source ~/.zshrc
```

次に、`p10k configure`を実行して、テーマの設定ウィザードを起動します。

```sh
p10k configure
```

## 3. プラグインのインストール
以下のプラグインをインストールして、快適な開発環境を構築します。

- `zsh-autosuggestions`: コマンドの自動補完を提供します。
- `zsh-syntax-highlighting`: コマンドのシンタックスハイライトを提供します。

これらをインストールするには、以下のコマンドを実行します：

```sh
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
```

次に、`~/.zshrc`ファイルを編集して、プラグインを有効にします：

```sh
nano ~/.zshrc
```

`plugins`の行を以下のように変更します：

```sh
plugins=(git zsh-autosuggestions zsh-syntax-highlighting)
```

設定を反映するために、ターミナルを再起動するか以下のコマンドを実行します：

```sh
source ~/.zshrc
```

## 4. プロンプトのカスタマイズ
`Powerlevel10k`テーマの設定が完了したら、必要に応じてプロンプトのカスタマイズを行います。`~/.p10k.zsh`ファイルを編集することで、プロンプトの表示内容を詳細に調整できます。

```sh
nano ~/.p10k.zsh
```

## 5. エイリアスの設定
よく使うコマンドをエイリアスとして設定しておくと便利です。例えば、`ll`コマンドを`ls -la`のエイリアスとして設定するには、`~/.zshrc`ファイルに以下を追加します：

```sh
alias ll='ls -la'
```

## 6. 日本語の設定
日本語の表示を改善するために、以下の設定を`~/.zshrc`に追加します：

```sh
export LANG=ja_JP.UTF-8
export LC_ALL=ja_JP.UTF-8
```

以上で、Oh My Zshを使ったコマンドラインのカスタマイズは完了です。必要に応じてさらに設定を調整し、自分に最適な環境を作り上げてください。
