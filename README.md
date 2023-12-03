## AI project - 항공 이미지를 활용한 건물 객체 추출

### :small_orange_diamond:TEAM 3
- 팀장: 이재웅
- 팀원: 박태현 임석현 서인규 이정아 임유진

### :small_orange_diamond:Dataset
- [Inria Aerial Image Labeling Dataset](https://www.kaggle.com/datasets/huanranye/inria-aerial-image-labeling-dataset/)
  
### :small_orange_diamond:Data Preprocessing
- Gaussian Blur
- RandomBrightnessContrast
  ![dataloaderImg]()
<!--
  ```python
    train_transform = A.Compose(
        [
            A.RandomCrop(384, 384),
            A.HorizontalFlip(p=0.3),
            A.VerticalFlip(p=0.3),
            A.RandomRotate90(p=0.3),
            A.Transpose(p=0.3),
            A.RandomBrightnessContrast(p=0.2),
            A.RandomShadow(shadow_roi=(0, 0, 1, 1), p=0.1),
    
            A.OneOf([
                # A.ElasticTransform(p=1),
                A.OpticalDistortion(p=1),
                A.GridDistortion(p=1),
            ], p=0.1),
            A.Normalize(),
            ToTensorV2()
        ]
    )
    test_transform = A.Compose(
        [
            A.CenterCrop(384, 384),
            A.Normalize(),
            ToTensorV2()
        ]
    )
  ```
  -->

### :small_orange_diamond:Model processing
1) Baseline
  - [UNet + convolution filer](https://github.com/ingyuseo/AI_project_team3/blob/main/FinalProject/code/Baseline.ipynb)
  - [UNet + ResNet](https://github.com/ingyuseo/AI_project_team3/blob/main/FinalProject/code/UnetVanila_UnetResnet_Week13.ipynb)
    
2) [UNet + EfficientNet for Encoder Backbone](https://github.com/ingyuseo/AI_project_team3/blob/main/FinalProject/code/Unet_efficientnet.ipynb)


3) [Grid Search + Cross-validation](https://github.com/ingyuseo/AI_project_team3/blob/main/FinalProject/code/GridsearchCV.ipynb)
   ![gridSearchImg]()
- Tuning the optimal parameters
   
    |lr|epoch|batch size|
    |:---:|:---:|:---:|
    |1e-3|50|32|
    |<span style="color:red">**1e-4**</span>|<span style="color:red">**100**</span>|<span style="color:red">**16**</span>|
    |1e-5|200|8|

4) [UNet + ConvNext](https://github.com/ingyuseo/AI_project_team3/blob/main/FinalProject/code/Unet_ConvNext.ipynb)

5) [Swin Transformer](https://github.com/ingyuseo/AI_project_team3/blob/main/FinalProject/code/Upernet_Swin.ipynb)

### :small_orange_diamond:Performance
1) IoU performance: Baseline UNet vs. UNet + EfficientNet
   ![iouImg]()
   
3) Output performance: Vanilla UNet vs. UNet + EfficientNet
  ![vanillaUImg]()    ![UEffiImg]()
   
2) [GMAC, GFLOPS](https://github.com/ingyuseo/AI_project_team3/blob/main/FinalProject/code/Flops_Counting.ipynb)


---
[DVC google storage](https://drive.google.com/drive/folders/11Jspj2-U19l0dgJj56GoSFkup0A0qjtV)
