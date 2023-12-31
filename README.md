﻿## AI project - 항공 이미지를 활용한 건물 객체 추출

### :radio_button:TEAM 3
- 팀장: 이재웅
- 팀원: 박태현 임석현 서인규 이정아 임유진

### :radio_button:Dataset
- [Inria Aerial Image Labeling Dataset](https://www.kaggle.com/datasets/huanranye/inria-aerial-image-labeling-dataset/)  
  <img src="./img/data1.png" width="200" /> <img src="./img/data2.png" width="200" />
### :radio_button:Data Preprocessing
- Gaussian Blur  
  <img src="./img/gaussianBlur.jpg" width="200" />  
  
- RandomBrightnessContrast  
  <img src="./img/RBC.jpg" width="200" />  
  
- Optical Distortion  
  <img src="./img/distortion.jpg" width="200" />  
  
- Flip / Transpose / Rotate  
  <img src="./img/flip.jpg" width="200" />  
  
  
### :radio_button:Model processing
1) Baseline
  - [Vanilla UNet](https://github.com/ingyuseo/AI_project_team3/blob/main/FinalProject/code/Baseline.ipynb)
  - [UNet + ResNet](https://github.com/ingyuseo/AI_project_team3/blob/main/FinalProject/code/UnetVanila_UnetResnet_Week13.ipynb)

2) [UNet + EfficientNet for Encoder Backbone](https://github.com/ingyuseo/AI_project_team3/blob/main/FinalProject/code/Unet_efficientnet.ipynb)

3) [Grid Search + Cross-validation](https://github.com/ingyuseo/AI_project_team3/blob/main/FinalProject/code/GridsearchCV.ipynb)
  Tuning the optimal parameters
    |lr|epoch|batch size|
    |:---:|:---:|:---:|
    |1e-3|50|32|
    |<span style="color:red">**1e-4**</span>|<span style="color:red">**100**</span>|<span style="color:red">**16**</span>|
    |1e-5|200|8|

4) [UNet + ConvNext](https://github.com/ingyuseo/AI_project_team3/blob/main/FinalProject/code/Unet_ConvNext.ipynb)

5) [Swin Transformer](https://github.com/ingyuseo/AI_project_team3/blob/main/FinalProject/code/Upernet_Swin.ipynb)

### :radio_button:Performance
1) IoU performance: Baseline UNet vs. UNet + EfficientNet
   <!--<img src="./img/iou.png" width="600" /> -->
    |Model|Hyper parameter setting|IoU|
    |:---:|:---:|:---:|
    |UNet + EfficientNet|batch size:16, lr: 1e-4, # of epochs: 100|78.9%|
    |Baseline UNet|batch size:16, lr: 1e-4, # of epochs: 100|73.5%|
   
2) Output performance: Vanilla UNet vs. UNet + EfficientNet  
  <img src="./img/vanillaU.png" width="200" /> <img src="./img/Ueffi.png" width="200" />
   
3) [GMAC, GFLOPS] 
 (https://github.com/ingyuseo/AI_project_team3/blob/main/FinalProject/code/Flops_Counting.ipynb)


---
[DVC google storage](https://drive.google.com/drive/folders/11Jspj2-U19l0dgJj56GoSFkup0A0qjtV)
