# Experiment using CMC dataset

## Dataset

https://github.com/DeepPathology/MITOS_WSI_CMC  

## How to experiment in docker

0. Build Environment  

```
sudo docker pull continuumio/anaconda3:2021.05  
sudo docker build -t gaussunet .  
sudo docker run -it --rm --runtime=nvidia -e NVIDIA_VISIBLE_DEVICES=all -p 8888:8888 --name gaussunet gaussunet  
# sudo docker run -it --rm --runtime=nvidia -e NVIDIA_VISIBLE_DEVICES=all --storage-opt size=120G -p 8888:8888 --name gaussunet gaussunet  
```

## How to experiment without docker
### 1-3 安装anaconda,如已经安装可跳过
1. ` wget -c https://repo.anaconda.com/archive/Anaconda3-2021.05-Linux-x86_64.sh` 
2. ` bash Anaconda3-2021.05-Linux-x86_64.sh` 
3. ` source ~/.bashrc` 
### 此时如果命令行前面显示（base）则安装成功，否则参考https://zhuanlan.zhihu.com/p/426655323
### 4-5我也不知道干啥，原来Dockerfile里面的命令
4. ` apt-get update && apt-get upgrade -y` 
5. ` apt-get install -y libgl1-mesa-dev` 
### 6-7配anaconda环境
6. ` conda env create -f ./tf-keras.yml` 
7. ` conda activate tf-keras` 
### 8-9下载代码，启动jupyter
8. Clone the git repository of CMC dataset   
` git clone https://github.com/DeepPathology/MITOS_WSI_CMC.git`   
9. Open jupyter notebook  
`jupyter notebook `  
10. Download WSIs using MITOS_WSI_CMC/Setup.ipynb  
11. Make a dataset with Gaussian labels using make_dataset.ipynb  
12. Train the model  
`python train.py`  
13. Evaluate the model using evaluate.ipynb  
