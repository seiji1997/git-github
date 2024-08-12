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


## key setting for UK
MacのUKキー配列では、デフォルトでShift + 3を押すと£が入力される設定になっていますが、<br>
Shift + 3で#を入力したい場合、以下の方法を試してみてください。

- 方法1: カスタムキーマッピングアプリの使用
    - Karabiner-Elementsなどのカスタムキーマッピングアプリをインストールします。Karabiner-Elementsは、キーボードのキーの動作を変更できる強力なツールです。

https://formulae.brew.sh/cask/karabiner-elements

```shell 
brew install --cask karabiner-elements
```

アプリをインストールして起動した後、Simple Modificationsタブで以下のように設定します。<br>

```
From key: Shift + 3
To key: #
```

この設定により、Shift + 3を押すと#が入力されるようになります。<br>


- 方法2: macOSの入力ソースを変更
    - システム環境設定を開き、キーボードを選択します。
    - 入力ソースタブで英字 (US配列) など他のキー配列に切り替えます。
    - US配列に変更すると、Shift + 3で#が入力されるようになります。ただし、この方法はキー配列全体が変わってしまうため、他のキーにも影響が出る可能性があります。

- 方法3: キーボードショートカットのカスタマイズ
    - システム環境設定 > キーボード > ショートカットに移動します。
    - App Shortcutsを選択し、新しいショートカットを追加します。特定のアプリでのみ有効にしたい場合は、そのアプリのショートカットとして設定できます。
    - ただし、一般的にShift + 3の動作を変えるためには、Karabiner-Elementsなどのカスタムキーマッピングツールを使用する方法が最も柔軟で効果的です。


- Karabiner-Elementsでの設定方法
```
Simple Modificationsタブを開いている状態で、右側の「Add item」をクリックします。
新しく追加された項目の左側のドロップダウンメニューから、「3」キーを選択します。
表示されるリストから3を選んでください。
右側のドロップダウンメニューから、「#」を選択します。
表示されるリストから#を選んでください。
この設定を保存すると、Shift + 3を押した際に#が入力されるようになります。
```

もし、Shift + 3を設定するオプションが表示されない場合は、Complex Modificationsタブを使用する必要があるかもしれません。その場合は、以下の手順を試してみてください。

- Complex Modificationsを使用する場合
```
左側のメニューからComplex Modificationsを選択します。
下部にある「Add rule」をクリックし、「Import more rules from the internet」をクリックして、ブラウザが開きます。
開いたページで「Shift + 3 to #」などを検索して、該当するルールをインポートします。
インポート後、Complex Modificationsタブに戻り、追加したルールを有効にします。
この手順で、Shift + 3を押すと#が入力されるように設定できるはずです。
```