# robosys_device_driver
これは2021年にロボットシステム学課題1で作成したデバイスドライバです。

入力（0or1）によってLEDが点灯したり、消灯したりします。

# 動作環境
・Raspberry Pi 4

・OS : ubuntu 18.04 LTS

# 使用したもの
・Raspberry Pi 4

・LED × 1

・抵抗220Ω × 1

・ブレッドボード × 1

・ジャンパー線（オス-メス）× 2

# 回路

・回路図

![image](https://user-images.githubusercontent.com/92899820/145713388-04a6a622-a1f8-48d7-97c9-00587eb5f4f4.png)

・配線図

![image0 482](https://user-images.githubusercontent.com/92899820/145683722-dd070b78-4581-4406-9772-ffa9b4c18347.jpeg)

![image1 483](https://user-images.githubusercontent.com/92899820/145683737-ea24c765-7951-4364-80f2-1443380609e8.jpeg)

・pin情報

![image](https://user-images.githubusercontent.com/92899820/145713427-35931895-a114-4aae-8761-1b0c34c36515.png)

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
**LEDを点灯させる**
```
$ echo 1 > /dev/myled0
```
***
**LEDを消灯させる**
```
$ echo 0 > /dev/myled0
```
***
# デモ動画
https://www.youtube.com/watch?v=8JNyMI1Xf30
***
# ライセンス
[GNU General Public License v3.0](https://github.com/ryuseiiiii/robosys_device_drivers/blob/main/COPYING)
