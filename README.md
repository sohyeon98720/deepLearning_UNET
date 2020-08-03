# 딥러닝 U-NET 구현
### 2020.04~2020.06
------------
### U-NET 요약설명
 - U-NET = Convolutional Networks for Biomedical Image Segmentation
 > <img src="https://user-images.githubusercontent.com/47767202/88923860-50809280-d2ad-11ea-9929-cf3135aa2d8a.png" width="50%"> <br>
 >> 순서대로 FCN과 U-NET의 구조(U-NET은 FCN을 기반으로 구축됨) <br>
 
 
 > <img src="https://user-images.githubusercontent.com/47767202/88924195-e1576e00-d2ad-11ea-9936-5c0cbd9445ac.png" width="50%"> <br>
 >> U-NET이 FCN으로부터 어떻게 변형되었는지를 설명
 
-------------

### keras U-NET with vein data
- **x train** data: [deepLearning_GAN에서 사용한 데이터](https://github.com/sohyeon98720/deepLearning_GAN#keras-gan-with-vein-data)의 일부와 이 원본데이터를 **augmentation**한 데이터를 적절히 섞어 재구성한 지정맥영상 **1880장**<br>
  - 원본데이터 2610장을 그대로 사용하지않은 이유는 한 명의 사람이 한 손가락에 대해 10장씩 영상이 획득되었기때문에 비슷한 영상이 너무 많아 학습이 잘 이루어지지 않을 것을 고려한 것임
  - data augmentation은 데이터의 특성(의료데이터)을 고려하여 flip, crop등의 원본 데이터를 해칠 수 있는 연산을 제외하고 brightness와 contrast만 조절하였음
- **y train** data: x_train에서 직접 지정맥 부분에 선을 그려 이진화처리한 영상 1880장<br>
- **test** data: deepLearning_GAN에서 사용한 데이터의 일부와 이 원본데이터를 augmentation한 데이터를 적절히 섞어 재구성한 지정맥 영상 **600장** <br>

> <img src="https://user-images.githubusercontent.com/47767202/89186561-f34f4e80-d5d6-11ea-9fe0-7bc4b1fe2eba.png"> <br>
>> 순서대로 x_train, y_train(이진화하기 전), test data

-------------
 ### 참고자료
- 이론참고
   - https://mylifemystudy.tistory.com/87?category=797525
   - https://www.quantumdl.com/entry/%EB%94%A5%EB%9F%AC%EB%8B%9D%EC%9D%84-%EC%9C%84%ED%95%9C-Atrous-Convolution%EA%B3%BC-UNet-%EA%B5%AC%EC%A1%B0-%EA%B0%84%EB%9E%B5%ED%95%9C-%EC%97%AD%EC%82%AC
   - https://www.kakaobrain.com/blog/64
