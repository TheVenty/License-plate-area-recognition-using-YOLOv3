# License-plate-area-recognition-using-YOLOv3

## Create license plate image dataset
- https://github.com/TheVenty/Korean-license-plate-Generator



**1. Download Darkflow to directory**   

    !git clone https://github.com/thtrieu/darkflow.git

**2. Build a learning environment and mount Google Drive**

    cd /content/darkflow

    !python setup.py build_ext --inplace
    !pip install .
    !pip install --upgrade tensorflow==1.13.1
    
    from google.colab import drive
    drive.mount('/content/drive')
    
**3-1. YOLO image learning (initial learning)**

    !python flow --model ./cfg/caps.cfg --labels ./labels.txt --trainer adam --dataset '/content/drive/My Drive/Colab Notebooks/data/dataset/' --annotation '/content/drive/My Drive/Colab Notebooks/data/annotations/' --train --summary ./logs --batch 5 --epoch 1000 --save 200 --keep 5 --lr 1e-04 --gpu 1.0
    
**3-2. YOLO image training (load checkpoint)**

    !python flow --model ./cfg/caps.cfg --labels ./labels.txt --trainer adam --dataset '/content/drive/My Drive/Colab Notebooks/data/dataset/' --annotation '/content/drive/My Drive/Colab Notebooks/data/annotations/' --train --summary ./logs --batch 5 --epoch 500 --save 100 --keep 5 --lr 1e-04 --gpu 1.0 --load -1

**4. License plate detection test**

    !python flow --imgdir /content/drive/My Drive/Colab Notebooks/data/samples --model ./cfg/caps.cfg --load -1 --batch 1 --threshold 0.5
    
**5. Weight optimization and saving training files**

    !python flow --model ./cfg/caps.cfg --load -1 --savepb
    
## Detection Image
![image](https://user-images.githubusercontent.com/49277505/137445618-1157cbcf-f173-4180-986f-06dc4c49567d.png)

![image (1)](https://user-images.githubusercontent.com/49277505/137445622-2c4a295c-b9f7-4a69-978e-c7a588da46a6.png)

![image (2)](https://user-images.githubusercontent.com/49277505/137445625-763e6e91-1a77-4d99-8042-48c5210fc73d.png)

![image (3)](https://user-images.githubusercontent.com/49277505/137445632-c6f6e0b3-3894-4cad-ae6e-2f695194b2f1.png)
