# AMCLを使った自己位置推定

Written by: 水野 on 2018/05/11

## AMCLとは

Augmented Monte Carlo Localizationの略．[GMapping](gmapping.md)と同様にパーティクルフィルタを使用し，与えられた地図の中のどこにロボットがいるかを推定するアルゴリズム．

## 手順

前準備として，ドライバ類を立ち上げ， `odom` → `base_link` が発行されていることを確認する．また，ジョイパッドで操作できるようにする．

1. `sudo apt-get install ros-kinetic-amcl ros-kinetic-map-server`
  - AMCLをインストール
2. `rosrun map_server map_server 地図YAMLファイルへのパス` で地図をロード
3. `rosrun amcl amcl` でAMCLを起動
4. `rosrun rviz rviz` で可視化用にrvizを立ち上げる
5. 左下のAddでPoseArrayを選択
6. PoseArrayの `topic` を `/particlecloud` にする
7. AddからTFを追加する
8. AddからMapを追加し， `/map` で地図が表示されることを確認する．
9. ツールバーのInital Poseで，ロボットの地図上の初期位置・向きを指定する
10. ロボットを動かし，自己位置が正しく収束していくかを確認する

TODO: 実行しているときの画像
