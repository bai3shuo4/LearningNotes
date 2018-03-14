Solver.prototxt
===
1. test_interval >= sample/train\_batchsize

2. test_iter >= test\_sample/test\_batchsize

3. max_iter = iternumber*(sample/train\_batchsize)

4. stepsize = max\_iter/change of lr

train_val.prototxt
===
1. batch\_size should be set not too large corresbonding to samples
2. kernel size shoule be set larger than stride
3. crop_size should be set smaller than ???

Train and Val data create
===
###sample.py(random pick n image as test)

```
import os, random, shutil

def copyFile(fileDiri,tarDir):
    pathDir = os.listdir(fileDir)
    sample = random.sample(pathDir, 480)
    print sample
    for name in sample:
        shutil.move(fileDir+name, tarDir+name)
        
if __name__ == '__main__':
    fileDir = '/path/to/src'
    tarDir = '/path/to/des'
    copyFile(fileDir,tarDir)
```
###train_val.sh(create train.txt and val.txt)


```
# /usr/bin/env sh
TRUEDATA=/path/to/label1
FALSEDATA=/path/to/label0
DATASAVE=/path/to/dataset
echo "Create train.txt..."

find $TRUEDATA -name label1*.jpg | cut -d '/' -f2-5 | sed "s/$/ 1/">>$DATASAVE/test.txt
find $FALSEDATA -name label0*.jpg | cut -d '/' -f2-5 | sed "s/$/ 0/">>$DATASAVE/tmp.txt

cat $DATASAVE/tmp.txt>>$DATASAVE/test.txt

rm -rf $DATASAVE/tmp.txt

echo "Done.."
```
###create_imagenet.sh

```
EXAMPLE=/path/to/lmdb
DATA=/path/to/train.txt&val.txt
TOOLS=caffe/build/tools

TRAIN_DATA_ROOT=/path/to/train
VAL_DATA_ROOT=/path/to/va

# Set RESIZE=true to resize the images to 256x256. Leave as false if images have
# already been resized using another tool.
RESIZE=false
```
###make\_imagenet_mean.sh

```
EXAMPLE=/path/to/lmdb
DATA=/path/to/train.txt&val.txt
TOOLS=caffe/build/tools
```

###run command

```
build/bin/caffe train -solver = train_val.prototxt
```

Learning rate
---

1. train loss 不断下降，test loss不断下降，说明网络仍在学习;

2. train loss 不断下降，test loss趋于不变，说明网络过拟合;

3. train loss 趋于不变，test loss不断下降，说明数据集100%有问题;

4. train loss 趋于不变，test loss趋于不变，说明学习遇到瓶颈，需要减小学习率或批量数目;

5. train loss 不断上升，test loss不断上升，说明网络结构设计不当，训练超参数设置不当，数据集经过清洗等问题。