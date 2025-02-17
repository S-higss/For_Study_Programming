# GitHubリモートレポジトリへpushするまで

以下，Linux環境での方法です．  
ssh接続する手順を紹介しています．

## 目次

- [Gitのインストール](#gitのインストール)
- [ユーザ名/メールアドレスの設定](#ユーザ名メールアドレスの設定)
- [公開/秘密鍵の作成](#公開秘密鍵の作成)
- [公開鍵の登録](#公開鍵の登録)
- [接続の確認](#接続の確認)
- [リポジトリにSSH接続](#リポジトリにssh接続)

## Gitのインストール

Windows環境ではインストーラーを用いてのインストールになります．  
その場合は[こちら](https://www.curict.com/item/60/60bfe0e.html)を参考にしてください．  

以下，Linux環境での説明です．  
まずコマンドライン上で

```bash
sudo apt-get update
sudo apt-get install git
```

を実行することによってGitがインストールされ,`git`コマンドが効くようになります．

```bash
git --version
```

でバージョンが表示されれば完了です．

[目次 に戻る](#目次)

[TOP に戻る](./README.md)

[HOME に戻る](../README.md)

## ユーザ名/メールアドレスの設定

以下, Windows/Linux共通です．  
まずGitHubアカウントを作成していることが大前提となるので，  
作成していない場合は[公式サイト](https://github.com/)にて，アカウントを作成してください．

GitHubにアクセスするために，`/.gitconfig`に登録済みユーザ名及びメールアドレスを設定します．  

```bash
git config --global user.name <登録したユーザー名>
git config --global user.email <登録したメールアドレス>
```

どちらも設定出来たら，

```bash
git config --global --list
```

で設定情報を確認することができます．

[目次 に戻る](#目次)

[TOP に戻る](./README.md)

[HOME に戻る](../README.md)

## 公開/秘密鍵の作成

以下, Windows/Linux共通です．  
`~/.ssh`配下に公開鍵・秘密鍵を作成します．  
初めて公開鍵・秘密鍵を作成する場合はディレクトリがなく，初回鍵作成時に作成されます．

```bash
ssh-keygen -t rsa
```

により公開/秘密鍵のペアが作成されます．  
その際，

```bash
Enter file in which to save the key (/home/<username>/.ssh/id_rsa):
Enter passphrase (empty for no passphrase):
```

と，鍵の保存ファイルのpath(名前，及びディレクトリ)，パスワードが聞かれます．  
初めての場合はデフォルトのpathで問題ないと思われます．  
パスワードも毎回打ち込むのが面倒であれば，何も入力せずEnterを押せば，パスワードなしの設定も可能です．  

これらを入力すると，先ほどのpathに公開・秘密鍵が作成されます．  
(デフォルトの場合，秘密鍵：`id_rsa`，公開鍵：`id_rsa.pub`というファイル名になります．)

[目次 に戻る](#目次)

[TOP に戻る](./README.md)

[HOME に戻る](../README.md)

## 公開鍵の登録

以下，主にLinux環境での説明となります．  
公開・秘密鍵を作成したら，次はGitHubアカウントに公開鍵の登録をします．  

まず，公開鍵の内容をコピーするため，

```bash
cat ~/.ssh/id_rsa.pub
```

とコマンドライン上に打ち込み，出力内容をコピーします．  
(鍵のディレクトリ・名前をデフォルトから変更した場合はこの通りではありませんので，公開鍵が保存されているpathに読み替えてください．)  
__Windows環境では,__ 直接`C:\Users\<ユーザ名>\.ssh\id_rsa.pub`を開いて内容をコピーしてください．  

次にGitHubをブラウザで開き，GithubアカウントのSettingからSSH and GPG keysを選択し，New SSH keyをクリックします．  
そこにその鍵の名前(Title)と，Keyに先ほどコピーした内容を貼り付けてAdd SSH Keyをクリックします．  
ここで，Key typeはデフォルトのAuthentication Keyで問題ありません．

__以下，先ほどデフォルトの名称で鍵生成をしなかった方向けです．__ (ssh接続の際`/.ssh/id_rsa`，`~/.ssh/id_dsa`，`~/.ssh/identity`をデフォルトで見に行くようになっているため)  
まず，configファイルを作成・編集します．  
以下のコマンドはLinux環境でのコマンドであり，Windows環境ではエクスプローラで直接アクセスし，編集してください．

```bash
vim ~/.ssh/config
```

例えば，鍵の名称をrsa_githubで作成している場合だと，編集画面で以下のように指定します．

```bash
Host github.com
HostName github.com
User git
IdentityFile "/home/<username>/.ssh/rsa_github"
```

その後，configファイルを保存して，完了です．

[目次 に戻る](#目次)

[TOP に戻る](./README.md)

[HOME に戻る](../README.md)

## 接続の確認

以下，Windows/Linux共通です．  
コマンドライン上で以下コマンドを実行します．

```bash
ssh -T git@github.com
```

初めて接続する際，

```bash
Are you sure you want to continue connecting (yes/no/[fingerprint])?
```

と聞かれますが，`yes`と答えれば大丈夫です．  
結果，

```bash
Hi <username>! You've successfully authenticated, but GitHub does not provide shell access.
```

と表示されれば成功です．

[目次 に戻る](#目次)

[TOP に戻る](./README.md)

[HOME に戻る](../README.md)

## リポジトリにSSH接続

以下，Windows/Linux共通です．  
ブラウザでGitHubにて使用するリポジトリを開き，`<> code`をクリックしてからsshを選択し，接続するための文字列をコピーします．  
コマンドライン上に戻り，これからリモートレポジトリをクローンしたいディレクトリ内で

```bash
git clone git@github.com:xxxx/test-repository.git
```

を実行すれば，リポジトリが紐づけられ，作業が可能になります．  
ここで，`git@github.com:xxxx/test-repository.git`は，先ほどGitHubにてコピーした接続するための文字列です．

[目次 に戻る](#目次)

[TOP に戻る](./README.md)

[HOME に戻る](../README.md)
