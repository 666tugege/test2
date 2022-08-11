# test2
1. Labels. Image labeling we use a tool called labelimg: https://github.com/tzutalin/labelImg and create a new .yaml:
```
train: ../yolo_A/images/
val: ../yolo_A/images/
nc: 1
names: ['ROI']
```
2. Divided into two folders and one file: images, labels, A.yaml and compressed into one zip file yolo_A.zip. 
Enter colab and enter the yolov5 environment：
```
!git clone https://github.com/ultralytics/yolov5  # clone
%cd yolov5
%pip install -qr requirements.txt  # install
import torch
import utils
display = utils.notebook_init()  # checks
```
3. Uncompress yolo_A.zip
```
!pip install pyunpack
!pip install patool
from pyunpack import Archive
Archive('/content/yolo_A.zip').extractall('/content/yolo_A')
```
4. Train
```
!python train.py --img 640 --batch 8 --epochs 100 --data ../yolo_A/A.yaml --weights yolov5n.pt --nosave --cache
```
5. Test
```
!python detect.py --weights /content/yolov5/runs/train/exp2/weights/last.pt --img 640 --conf 0.25 --source /content/yolo_A/images
```
