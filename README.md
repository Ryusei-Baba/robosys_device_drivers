# robosys_device_driver
これは2021年にロボットシステム学課題1で作成したデバイスドライバです。

入力によってLEDやブザーの出力が変わります。
***
# 動作環境
・Raspberry Pi 4

・OS : ubuntu 18.04 LTS
***
# 使用したもの
・Raspberry Pi 4

・LED × 1

・電磁ブザー × 1

・ブレッドボード × 1

・ジャンパー線（オス-メス）× 2

・ジャンパー線（オス-オス）× 1
***
# 回路
・回路図
![image](https://user-images.githubusercontent.com/92899820/146334518-2a3d00d7-e971-440e-bd79-09a335ba3945.png)


・配線図
![image0 495](https://user-images.githubusercontent.com/92899820/146334575-dc47aa5a-8b70-419e-8084-4aea567f836d.jpeg)

![image1 496](https://user-images.githubusercontent.com/92899820/146334599-4c2eeb6e-7c3c-45ce-9be2-1a42fb29c22a.jpeg)


・pin情報

![image](https://user-images.githubusercontent.com/92899820/145713427-35931895-a114-4aae-8761-1b0c34c36515.png)
***
# 使用方法
**【インストール】**

以下のコマンドを実行してください。

```
$ git clone git@github.com:ryuseiiiii/robosys_device_drivers.git

$ cd robosys_device_drivers

$ make

$ sudo insmod myled.ko

$ sudo chmod 666 /dev/myled0
```
***
**【アンインストール】**

以下のコマンドを実行してください。

```
$ sudo rmmod myled

$ make clean
```
***
**【実行】**

※ページ下に実行時の動画があります。

インストール後に以下のコマンドを実行してください。
***
**すべての動作を終了させる**
```
$ echo 0 > /dev/myled0
```
***
**LEDの点灯とブザーを鳴らす**
```
$ echo 1 > /dev/myled0
```
***
**LEDの点滅とブザーを鳴らす**
```
$ echo 2 > /dev/myled0
```
***
# デモ動画
https://www.youtube.com/watch?v=oNSrJS55dIE
***
# ライセンス
[GNU General Public License v3.0](https://github.com/ryuseiiiii/robosys_device_drivers/blob/main/COPYING)
