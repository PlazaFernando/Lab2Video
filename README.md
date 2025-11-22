# Lab2Video
This is a repository for a lab assignment  of DLVSP focused on video object detection.  


First, create a new environment to work in
```python
conda create --name LAB2VIDEO -y python=3.7
source activate LAB2VIDEO
```

Install pip
```python
conda install ipython pip
```

Install mega and coco api dependencies
```python
pip install ninja yacs cython matplotlib tqdm opencv-python scipy
```

Install pytorch 1.2.0 and torchvision
```python
conda install pytorch=1.2.0 tochvision=0.4.0 cudatoolkit=10.0 -c pytorch
```

Install pycocotools
```python
export INSTALL_DIR=$PWD
git clone https://github.com/cocodataset/cocoapi.git
cd cocoapi/PythonAPI
python setup.py build_ext install
```

Install cityscapesScripts
```python
cd $INSTALL_DIR
git clone https://github.com/mcordts/cityscapesScripts.git
cd cityscapesScripts/
python setup.py build_ext install
```

Install apex
```python
cd $INSTALL_DIR
git clone https://github.com/NVIDIA/apex.git
```
Now, download from the repository the following archives: setup.py , scheduler.py , wrapper.py , graph.py , layer.norm.py , config.py , backend.py and test_dist_adam.py and paste them in their respective folders:
```python
~/apez/setup.py
~/apex/apex/contrib/torchsched/inductor/scheduler.py
~/apex/apex/contrib/torchsched/inductor/wrapper.py
~/apex/apex/contrib/torchsched/inductor/graph.py
~/apex/apex/contrib/torchsched/ops/layer.norm.py
~/apex/apex/contrib/torchsched/config.py
~/apex/apex/contrib/torchsched/backend.py
~/apex/apex/contrib/test/optimizers/test_dist_adam.py
```
And continue with the installation of apex
```python
cd apex
python setup.py build_ext install
```

Install mega.pytorch
```python
cd $INSTALL_DIR
gir clone https://github.com/Scalsol/mega.pytorch.git
```
Now, download from the repository the following archives: nms.py , roi_align.py , roi_pool.py and predictor.py and paste them in their respective folders:
```python
~/mega.pytorch/mega_core/layers/nms.py
~/mega.pytorch/mega_core/layers/roi_align.py
~/mega.pytorch/mega_core/layers/roi_pool.py
~/mega.pytorch/demo/predictor.py
```
And continue with the installation of mega.pytorch
```python
cd mega.pytorch
python setup.py build develop
```

Install pillow
```python
pip install 'pillow<7.0.0
unset INSTALL_DIR
```

Once the installation is complete, let's try some examples for object detection. Download from the repository the files R_101.pth and MEGA_R_101.pth and paste them in ~/mega.pytorch/ directory. Download image_folder.zip and video_folder.zip and unzip them. Copy the resulting folders in ~/mega.pytorch/ directory. Create a folder for visualizing the results, i.e., ~/mega.pytorch/visualization/

Finally, process the image samples for object detection using base approach:
```python
python demo/demo.py base configs/vid_R_101_C4_1x.yaml R_101.pth --suffix ".JPEG" --visualize-path image_folder --output-folder visualization --output-video
```
You can compare the results with MEGA approach:
```python
python demo/demo.py mega configs/MEGA/vid_R_101_C1_MEGA_1x.yaml MEGA_R_101.pth --suffix ".JPEG" --visualize-path image_folder --output-folder visualization --output-video
```

Some video samples are available too (change VIDEO.avi for the video sample you want to process):
```python
python demo/demo.py base configs/vid_R_101_C4_1x.yaml R_101.pth --video --visualize-path video_folder/VIDEO.avi --output-folder visualization --output-video
python demo/demo.py mega configs/MEGA/vid_R_101_C1_MEGA_1x.yaml MEGA_R_101.pth --video --visualize-path video_folder/VIDEO.avi --output-folder visualization --output-video
```

Resulting videos are shown in ~/mega.pytorch/visualization directory.

