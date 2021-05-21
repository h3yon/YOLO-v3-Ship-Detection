## 1. amanbasu/ship-detection

link: https://github.com/amanbasu/ship-detection

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

test해봄으로써 코드가 돌아가는지 확인합니다.

```
$ ./darknet detect cfg/yolov3.cfg yolov3.weights data/dog.jpg
```

ship 데이터를 train 시킵니다.

```
$ ./darknet detector train cfg/ship.data cfg/yolov3-ship.cfg darknet53.conv.74
```

test함으로써 결과를 확인합니다.

```
$ ./darknet detector test cfg/ship.data cfg/yolov3.cfg backup/backup_file.weights test_file.jpg
```
