# UbuntuとROSのインストール

Written by: 水野 on 2018/05/11

## オススメのバージョン

- Ubuntu 16.04.4
  + 研究室の多くのUbuntuがこのバージョンのため．
- ROS Kinetic
  + 現時点でリリースされているROSディストロのうち，最も長期のサポートがされるリリースであるため．

## Ubuntuのインストール

TODO: 解説してるサイトを探してくる

基本的な流れは以下の通り:

1. Ubuntuのイメージ（.isoファイル）をダウンロードする
2. イメージをUSBに焼く
  - Windowsの場合: ISO to USB
  - Mac，Linuxの場合: `dd` コマンドを使う
3. UbuntuをインストールするPCのBIOSに入り，起動の順番でUSBが優先されるようにする
  - BIOSでセキュアブートを無効にする必要がある場合もある
4. BIOSの設定を保存して終了し，USBから起動されることを確認する
5. `Install Ubuntu` を選択するとUbuntuのインストーラが立ち上がるので，指示に従ってインストールを進める
6. パーティションのステップになったら，分割を行う（次節を参照）
7. そのままインストールを進めると，Ubuntuがインストールされる

### パーティションの分割

パーティション分割とは，一つのハードディスクを幾つかの領域に分割し，隔離すること．これをすると，一つのハードディスクに複数のOSがインストールできたり（デュアルブートと呼ばれる），データ専用の領域を設けたりできる．ちなみに，パー**ティ**ション（partition）で，パー**テイ**ションではない．

オススメは，「Windows用」「Windows Recovery」「Ubuntuのシステム用」「Ubuntuのデータ用」4つに分けることである．Windows関連の2つのパーティションは既にあるはずなので，Ubuntu用のパーティションを作成するためには以下の作業が必要になる:

1. UbuntuインストールUSBのターミナルから， `sudo gparted` を起動
2. Windowsシステムパーティションの縮小
3. 空いた領域にUbuntuのパーティションを2つ作成

この際，Windowsのパーティションが暗号化されていないことを確認する．

TODO: 上記手順を書く（画像があると良い）

## ROSのインストール

ROSのインストールには以下のページを参考にする．

http://wiki.ros.org/kinetic/Installation/Ubuntu

基本的に上記ページに書いてあるコマンドを，ターミナルにコピペするけcでインストールできる．

### 注意点

ROSをインストールする前に `sudo apt-get update` を実行すると，稀にROSがインストールできなくなる．これが起こる理由は，ROSが依存するライブラリ等がアップデートされてしまい，依存関係がこじれてしまうため．ROSをインストールすると分かっているのであれば， `sudo apt-get update` するのはROSをインストールしてからにするべし．