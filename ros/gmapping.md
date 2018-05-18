# GMappingを使ったSLAM

Written by: 水野 on 2018/05/11

## SLAMとは

Simultaneous Localization And Mappingの略．直訳すると「自己位置推定と地図作成の同時実行」．ロボットがセンサ等の情報を元に，自分がどこにいるのか（自己位置推定）と周囲環境の地図（地図作成）を同時に行う**手法**のこと．移動ロボットが未探索の場所に入っていく際に行われる．

## GMappingとは

SLAMをするための**ソフトウェア**．公式ページの説明には

> GMapping is a highly efficient Rao-Blackwellized particle filer to learn grid maps from laser range data.

と書いてあるが，訳すと「LIDARからのデータを元にRao-Blackwellized Particle Filterというアルゴリズムを使って地図を作成する」ということ．Rao-Blackwellized Particle Filterとは，複数の予想（地図とその中での自分の位置．パーティクル）を持ち，センサデータが各パーティクルとどれだけ整合性が取れているかを計算する．整合性の取れていないパーティクルを枝切りすることで，パーティクルの精度を上げていくという手法．

## 実行手順

下記はビーゴあるいはメカノさんで実行することを前提としている．別のロボットや環境を使用する際はトピック名やフレーム名を適宜変更すること．

1. `sudo apt-get install ros-kinetic-gmapping` でパッケージをインストール
2. `rosrun gmapping slam_gmapping` を実行
3. `rosrun rviz rviz` でrvizを立ち上げる
4. 左上のGlobal Frameが `map` になっていることを確認する
5. 左下のAddで `Map` を選択し， `topic` を `/map` にする．
6. もう一度Addし， `LaserScan` を追加，`topic` を `/scan` にする
7. ロボットを走らせると地図ができる

### 実行できない場合

#### 問題

- 地図が生成されない

#### 対処

 `odom` → `base_link` のTF変換が発行されているかを確認する．また， `/scan` トピックが発行されていることを確認する．

#### 対処方法

[ここ](robot.md)を参照．
