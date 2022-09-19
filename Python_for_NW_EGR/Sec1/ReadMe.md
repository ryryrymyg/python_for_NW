# 1. Python Basics
Pythonによる作業を行う際に、以下の環境を決める必要がある
- OS
- エディタ
- Pythonのバージョン

本学習はDebian LinuxとPython 3.7で実行される物とする
## 作業のための環境構築
環境構築のためには以下の選択肢がある
- VMを用意する
- クラウドサービスを利用する
- VMを立てないで環境を構築する

今回は簡単のためにWindowsマシン上にWSL2を用いてDebian仮想環境を構築する

### WSL2を用いたDebian環境構築方法
[このへん](https://www.kkaneko.jp/tools/wsl/wsl2.html)を見て構築してください

## OSとエディタ
OSやエディタはぶっちゃけ何でも良い。ただし、これから書いていく内容はPython 3.9を利用しているため、初学者はPython 3.9を使うと良いと思います。
また、以後すべてのコマンドはDebian上で実行されるため、OSはDebianがおすすめです。ただ、他のOS上でも出力が異なる場合があるだけで、以後タスクを行うことができます。

エディタはVSCodeがお勧めです。勝手にPythonファイルを認識して、シンタックスハイライトとかやってくれます。Python以外にもGit連携等色々できます。<br>
[Pyton for network engineer](https://pyneng.readthedocs.io/en/latest/index.html "Python for network engineer")ではMu Editor, PyCharm, Geany等を勧めているようです。
好きなものを使うとよいと思います。

## Package management system Pip
Pythonは豊富なライブラリによる拡張性の高い言語です。その多様な拡張性の恩恵を受けるためのパッケージ管理システムとして、PIPを用います。<br>
以下のコマンドでpipのバージョンを確認してみてください
```console
$ pip --version
pip 20.3.4 from /usr/lib/python3/dist-packages/pip (python 3.9)
```
もしコマンドが失敗した場合、pipが入っていません。
pipのインストールについては[この資料](https://pip.pypa.io/en/stable/installation/ "https://pip.pypa.io/en/stable/installation/")を確認してください。

## 仮想環境
Pythonの仮想環境を利用するメリットは以下の通りです
- 異なるプロジェクトの実行環境を分離することができる
- それに伴いパッケージのバージョンはプロジェクト毎に別の場所へ配置されます
- 仮想環境にインストールされたパッケージは、コンピュータ全体のパッケージ(グローバルパッケージ)に影響を与えません

Pythonには仮想環境作成オプションが幾つかあります。どれを使ってもいいですが、まずはvisualenvwrapperを使ってみて、最終的に何を使うか考えてみましょう。

### 仮想環境構築ツール：virtualenvwrapper
---
まず以下のコマンドでvirtualenvwrapperをインストールする
```
sudo pip install virtualenvwrapper
```
次に、homeディレクトリ配下の.bashrcファイルに以下のコメントを書き加える(環境変数の追加、仮想環境の)
```shell
export VIRTUALENVWRAPPER_PYTHON=/usr/bin/python3.9
export WORKON_HOME=~/venv
. /usr/local/bin/virtualenvwrapper.sh
```
その後以下のコマンドで
上記設定を読み込む。
```
exec bash
```
なんかうまくいかん時は[Stack Overflow](https://stackoverflow.com/questions/2518127/how-to-reload-bashrc-settings-without-logging-out-and-back-in-again)参照

### 仮想環境を構築する
---
以下のコマンドで仮想環境pynengを構築する
```
$mkvirtualenv --python=/usr/bin/python3.9 pyneng
created virtual environment CPython3.9.2.final.0-64 in 333ms
  creator CPython3Posix(dest=/home/<username>/venv/pyneng, clear=False, no_vcs_ignore=False, global=False)
  seeder FromAppData(download=False, pip=bundle, setuptools=bundle, wheel=bundle, via=copy, app_data_dir=/home/<username>/.local/share/virtualenv)
    added seed packages: pip==22.2.2, setuptools==65.3.0, wheel==0.37.1
  activators BashActivator,CShellActivator,FishActivator,NushellActivator,PowerShellActivator,PythonActivator
virtualenvwrapper.user_scripts creating /home/<username>/venv/pyneng/bin/predeactivate
virtualenvwrapper.user_scripts creating /home/<username>/venv/pyneng/bin/postdeactivate
virtualenvwrapper.user_scripts creating /home/<username>/venv/pyneng/bin/preactivate
virtualenvwrapper.user_scripts creating /home/<username>/venv/pyneng/bin/postactivate
virtualenvwrapper.user_scripts creating /home/<username>/venv/pyneng/bin/get_env_details
(pyneng)$
```
仮想環境に入れました。
これで.bashrcで指定した仮想環境設定格納ディレクトリにpynengディレクトリが作成されました。
```
(pyneng)$ ls ~/venv
get_env_details  postactivate    postmkproject     postrmvirtualenv  predeactivate  premkvirtualenv  pyneng
initialize       postdeactivate  postmkvirtualenv  preactivate       premkproject   prermvirtualenv
```
