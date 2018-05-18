# ビーゴ固有の手順

Written by: 水野 on 2018/05/11

## セットアップ

```
$ git clone https://github.com/tadolab/beego_bringup ./src/beego_bringup
$ sudo apt-get install ros-kinetic-urg-node
```

`beego_bringup` はビーゴの操作に必要なROSノードを立ち上げてくれるlaunchファイルを含むパッケージ．

`ros-kinetic-urg-node` はURG（2次元LIDAR）用のドライバ．

## 起動

起動には，以下のコマンドを実行する:

```
$ roslaunch beego_bringup beego_bringup.launch
```

上記のコマンドは，ドライバ類を立ち上げ，速度指令を受け付ける状態にする．

ロボットの電源を投入してからURGが使えるようになるまで少し時間がかかる．電源投入直後にコマンドを実行した際にURGのノードが起動に失敗する場合は，少し時間を置いてから再度試す．
