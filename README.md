# U-NET을 이용한 지정맥영상 segmentation
### 졸업프로젝트(2020.04~2020.06)
------------

### U-NET 요약설명
 - U-NET = Convolutional Networks for Biomedical Image Segmentation
 > <img src="https://user-images.githubusercontent.com/47767202/88923860-50809280-d2ad-11ea-9929-cf3135aa2d8a.png" width="50%"> <br>
 >> 순서대로 FCN과 U-NET의 구조(U-NET은 FCN을 기반으로 구축됨) <br>
 
 > <img src="https://user-images.githubusercontent.com/47767202/88924195-e1576e00-d2ad-11ea-9936-5c0cbd9445ac.png" width="50%"> <br>
 >> U-NET이 FCN으로부터 어떻게 변형되었는지를 설명
 
-------------

### denselayer_based_Unet
- **x train** data: [deepLearning_GAN에서 사용한 데이터](https://github.com/sohyeon98720/deepLearning_GAN#keras-gan-with-vein-data)의 일부와 이 원본데이터를 **augmentation**한 데이터를 적절히 섞어 재구성한 지정맥영상 **1880장**<br>
  - 원본데이터 2610장을 그대로 사용하지않은 이유는 한 명의 사람이 한 손가락에 대해 10장씩 영상이 획득되었기때문에 비슷한 영상이 너무 많아 학습이 잘 이루어지지 않을 것을 고려한 것임
  - data augmentation은 데이터의 특성(의료데이터)을 고려하여 flip, crop등의 원본 데이터를 해칠 수 있는 연산을 제외하고 brightness와 contrast만 조절하였음
- **y train** data: x_train에서 직접 지정맥 부분에 선을 그려 이진화처리한 영상 1880장<br>
- **test** data: deepLearning_GAN에서 사용한 데이터의 일부와 이 원본데이터를 augmentation한 데이터를 적절히 섞어 재구성한 지정맥 영상 **600장** <br>

  |x_train|x_train->y_train처리과정|y_train|
  |:---:|:---:|:---:|
  |<img src="https://user-images.githubusercontent.com/47767202/91634249-e4b75400-ea29-11ea-88aa-74447b0a1676.jpg">|<img src="https://user-images.githubusercontent.com/47767202/91634269-129c9880-ea2a-11ea-9cf5-7fb328a81e4b.jpg">|<img src="https://user-images.githubusercontent.com/47767202/91634311-6d35f480-ea2a-11ea-940d-651d4dc7bcc7.jpg">|
  |원본|원본+선|원본+선+이진화|


- __평가지표__: mean IoU(IoU의 평균)
  - **IoU** = intersection over union = Area of Overlap / Area of Union <br>
    <img src="https://user-images.githubusercontent.com/47767202/91118395-d1c01f00-e6cb-11ea-9920-89ab1c04ac22.png" width="30%"><br>
    <img src="https://user-images.githubusercontent.com/47767202/91018050-067b9a00-e62a-11ea-9b3d-a8aa97fb4d22.png" width="60%"><br>
    주로 IoU score threshold 값으로 0.5를 설정함
    > R-CNN에서는 ground truth와 proposed region 사이의 IoU 값을 계산해 0.5 이상인 경우 해당 region을 객체로 바라보고 ground truth와 같은 class로 labelling함.
 
 <br>
 
- __결과__: <br>

  |x_test 원본영상|x_test 정답영상|x_test predict영상|x_test predict_upsampled영상|
  |:---:|:---:|:---:|:---:|
  |<img src="https://user-images.githubusercontent.com/47767202/91633930-60fc6800-ea27-11ea-8b14-fea1cf9864ef.jpg">|<img src="https://user-images.githubusercontent.com/47767202/91634052-51c9ea00-ea28-11ea-87ce-3ea499b1bbf6.jpg">|<img src="https://user-images.githubusercontent.com/47767202/91634102-bedd7f80-ea28-11ea-8185-5b7a351de9b4.jpg">|<img src="https://user-images.githubusercontent.com/47767202/91634118-dae12100-ea28-11ea-9f31-0802a80baf7d.jpg">|


-------------
 ### 참고자료
- 이론참고
   - https://mylifemystudy.tistory.com/87?category=797525
   - https://www.quantumdl.com/entry/%EB%94%A5%EB%9F%AC%EB%8B%9D%EC%9D%84-%EC%9C%84%ED%95%9C-Atrous-Convolution%EA%B3%BC-UNet-%EA%B5%AC%EC%A1%B0-%EA%B0%84%EB%9E%B5%ED%95%9C-%EC%97%AD%EC%82%AC
   - https://www.kakaobrain.com/blog/64
   - https://jetsonaicar.tistory.com/14
   - https://ballentain.tistory.com/12

 - 코드참고
   - https://www.kaggle.com/keegil/keras-u-net-starter-lb-0-277
   - https://www.kaggle.com/eduardomineo/u-net-lung-segmentation-montgomery-shenzhen#4.-Results
  
