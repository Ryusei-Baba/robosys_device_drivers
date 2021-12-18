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

![image](https://user-images.githubusercontent.com/92899820/146388302-837a8a73-4aa7-4a5d-9210-5725e3349ba8.png)

・配線図
![image0 495](https://user-images.githubusercontent.com/92899820/146334575-dc47aa5a-8b70-419e-8084-4aea567f836d.jpeg)

![image1 496](https://user-images.githubusercontent.com/92899820/146334599-4c2eeb6e-7c3c-45ce-9be2-1a42fb29c22a.jpeg)
***
# 使用方法
**・インストール**

以下のコマンドを実行してください。

```
$ git clone git@github.com:ryuseiiiii/robosys_device_drivers.git

$ cd robosys_device_drivers

$ make

$ sudo insmod myled.ko

$ sudo chmod 666 /dev/myled0
```
***
**・アンインストール**

以下のコマンドを実行してください。

```
$ sudo rmmod myled

$ make clean
```
***
**・実行**

※デモ動画がこの下にあります。

インストール後に以下のコマンドを実行してください。
***
**・すべての動作を終了させる**
```
$ echo 0 > /dev/myled0
```
***
**・LEDの点灯とブザーを鳴らす**
```
$ echo 1 > /dev/myled0
```
***
**・LEDの点滅とブザーを鳴らす**
```
$ echo 2 > /dev/myled0
```
***
# デモ動画
[[Raspberry Pi 4] デバイスドライバ](https://www.youtube.com/watch?v=oNSrJS55dIE)
***
# ライセンス
[GNU General Public License v3.0](https://github.com/ryuseiiiii/robosys_device_drivers/blob/main/COPYING)
***
# 参考
・以下のサイトを参考にしました。

[回路記号](https://www.edrawsoft.com/jp/basic-electrical-symbols.html)

[pin情報](https://iot.keicode.com/raspberry-pi/pinout.php#:~:text=%E3%81%BE%E3%81%9A%20Raspberry%20Pi%20%E3%81%AE%E3%83%94%E3%83%B3%E5%90%8D%E3%81%A7%E3%81%99%E3%81%8C%E3%80%81%E9%80%9A%E5%B8%B8%E4%BA%8C%E9%80%9A%E3%82%8A%E5%87%BA%E3%81%A6%E3%81%8D%E3%81%BE%E3%81%99%E3%80%82%20%E3%81%B2%E3%81%A8%E3%81%A4%E3%81%AF%20%E7%89%A9%E7%90%86%E3%83%94%E3%83%B3%E7%95%AA%E5%8F%B7%20%E3%81%A7%E3%80%81%E3%83%94%E3%83%B3%E3%81%AE%E4%B8%A6%E3%81%B3%E9%A0%86%E3%81%AB%201%2C,40%20%E3%81%A8%E5%89%B2%E3%82%8A%E5%BD%93%E3%81%A6%E3%81%BE%E3%81%99%E3%80%82%20%E4%B8%8B%E5%9B%B3%E7%9C%9F%E3%82%93%E4%B8%AD%E3%81%AE%E3%80%81%20%E6%9E%A0%E7%B7%9A%E3%81%A7%E5%9B%B2%E3%81%A3%E3%81%9F%EF%BC%92%E5%88%97%E3%81%AE%E6%95%B0%E5%AD%97%E3%81%8C%E7%89%A9%E7%90%86%E3%83%94%E3%83%B3%E9%85%8D%E7%BD%AE%E3%81%A7%E3%81%99%E3%80%82%20%E3%82%82%E3%81%86%E3%81%B2%E3%81%A8%E3%81%A4%E3%81%AF%E3%80%81%20BCM%20%E3%83%94%E3%83%B3%E7%95%AA%E5%8F%B7%20%E3%81%A8%E8%A8%80%E3%82%8F%E3%82%8C%E3%82%8B%E3%82%82%E3%81%AE%E3%81%A7%E3%81%99%E3%80%82)

[コードブロックの作成と強調表示](https://docs.github.com/ja/github/writing-on-github/working-with-advanced-formatting/creating-and-highlighting-code-blocks)

[Markdown記法](https://qiita.com/toshihirooya/items/949f571b85cd7c297cca)
***
# 自分のオリジナル
myled.c内の32行目から44行目は私のオリジナルです。目覚まし時計や小学生が良く持っている防犯ブザーをイメージして作成しました。
```
        else if(c == '2'){
                for(i=0;i<100;i++){
                        if(i%2 == 0){
                                gpio_base[7] = 1 << 25;
                                msleep(50);
                        }else if(1%2 != 0){
                                gpio_base[10] = 1 << 25;
                                msleep(50);
                        }
                }
                gpio_base[10] = 1 << 25;

        }
```
