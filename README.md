# robsys_kadai2
## 概要
## 動作環境
以下の環境で動作を確認しています．
- Raspberry Pi 4 Model B
- ROS Noetic
- OS:Ubuntu 20.04 LTS
- USBカメラ:Logicool C615
- OpenCV:4.5.1(python)
## 環境構築
1.本パッケージをインストールします．
```
$ cd ~/catkin_ws/src
$ git clone https://github.com/bananati/robsys_kadai2.git
$ git ~/catkin_ws
$ catkin_make
```
2.APTによるROSパッケージのインストールを行います．
```
$ sudo apt install ros-noetic-cv-camera
$ sudo apt install ros-noetic-cv-bridge
```
3.web_video_serverというパッケージをgitからインストールします．
```
$ sudo apt install ffmpeg
$ cd ~/catkin_ws/src/
$ git clone https://github.com/GT-RAIL/async_web_server_cpp.git
$ git clone https://github.com/RobotWebTools/web_video_server.git
$ cd ~/catkin_ws/ && catkin_make -j 4
```
## 実行方法
1.<端末１>でroscoreを立ち上げます．
```
$ roscore
```
2.<端末２>でカメラを立ち上げます．その際，ビデオのデバイスがあるか確認します．
```
$ ls /dev/video*
/dev/video0
$ rosrun cv_camera cv_camera_node
```
3.<端末３>で本パッケージのカメラ画像をグレイスケールにするサンプルコードを実行します．
```
$ rosrun robsys_kadai2 gray_img.py
```
4.<端末４>でサーバーを立ち上げます．
```
$ rosrun web_video_server web_video_server
```
5.ブラウザでhttp://ラズパイのIPアドレス:8080 にアクセスすると映像の確認ができます．
## デモ動画
デモ動画はになります．
## 参考文献
ソースコードはのサイトを参考にしています．
