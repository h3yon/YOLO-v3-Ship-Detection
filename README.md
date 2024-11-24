## 1. amanbasu/ship-detection

- link1: https://github.com/amanbasu/ship-detection
- link2: https://github.com/pjreddie/darknet

#### clone and make(images)

```
$ git clone https://github.com/amanbasu/ship-detection
$ git clone https://github.com/pjreddie/darknet
$ cd darknet
$ make
$ wget https://pjreddie.com/media/files/darknet53.conv.74
# darknet 디렉토리에서 darknet53.conv.74 파일 다운로드
```

`amanbasu/ship-detection`의 darknet_files 파일들을 darknet 디렉토리 아래 data, cfg 디렉토리로 이동시킵니다.

```
data/ship.names
cfg/ship.data
cfg/yolov3-ship.cfg
```

`amanbasu/ship-detection`의 dataset 디렉토리 또한 darknet 디렉토리 아래로 이동시킵니다.
yolov3.weights 파일 또한 다운로드 받아 darknet 디렉토리 아래로 이동시킵니다.
yolov3.weights 파일은 [여기](https://pjreddie.com/media/files/yolov3.weights)에서 다운로드 가능합니다.

test해봄으로써 코드가 돌아가는지 확인합니다.

```
$ ./darknet detect cfg/yolov3.cfg yolov3.weights data/dog.jpg
```

![image](https://user-images.githubusercontent.com/46602874/119124918-29799400-ba6c-11eb-9835-4e28b39c1ff5.png)
test의 결과는 위와 같습니다.

![image](https://user-images.githubusercontent.com/46602874/119124918-29799400-ba6c-11eb-9835-4e28b39c1ff5.png)
test의 결과는 위와 같습니다.

![image](https://user-images.githubusercontent.com/46602874/119244452-cbec6100-bbab-11eb-9e4d-e71c6f9e8f4f.png)
ship 데이터를 train 시킵니다.
중간에 멈추더라도 일정 시간이 지나면 backup파일에 결과물이 있음을 알 수 있습니다.

```
$ ./darknet detector train cfg/ship.data cfg/yolov3-ship.cfg darknet53.conv.74
```

test함으로써 결과를 확인합니다.

```
$ ./darknet detector test cfg/ship.data cfg/yolov3.cfg backup/backup_file.weights test_file.jpg
```

![image](https://user-images.githubusercontent.com/46602874/119244541-c5aab480-bbac-11eb-820b-f290b04b655b.png)
backup파일에 있던 weights 파일 이름을 넣어주고 test할 파일을 darknet 디렉토리 안에 넣어줍니다.
test하면 ship이 잘 나옴을 알 수 있습니다.
