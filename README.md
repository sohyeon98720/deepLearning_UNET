# 딥러닝 U-NET 구현
### 2020.04~2020.06
------------
### U-NET 요약설명
 - U-NET = Convolutional Networks for Biomedical Imae Segmentation
 > <img src="https://user-images.githubusercontent.com/47767202/88923860-50809280-d2ad-11ea-9929-cf3135aa2d8a.png" width="50%"> <br>
 >> 순서대로 FCN과 U-NET의 구조(U-NET은 FCN을 기반으로 구축됨) <br>
 
 
 > <img src="https://user-images.githubusercontent.com/47767202/88924195-e1576e00-d2ad-11ea-9936-5c0cbd9445ac.png" width="50%"> <br>
 >> U-NET이 FCN으로부터 어떻게 변형되었는지를 설명
 
-------------

### keras U-NET with vein data
- data: [deepLearning_GAN에서 사용한 데이터](https://github.com/sohyeon98720/deepLearning_GAN#keras-gan-with-vein-data)의 일부와 이 원본데이터를 **data augmentation**한 데이터를 적절히 섞어 재구성한 지정맥영상 **1880장**<br>
  - 원본데이터

-------------
 ### 참고자료
 - 이론참고<br>
  -  https://mylifemystudy.tistory.com/87?category=797525
  - https://www.quantumdl.com/entry/%EB%94%A5%EB%9F%AC%EB%8B%9D%EC%9D%84-%EC%9C%84%ED%95%9C-Atrous-Convolution%EA%B3%BC-UNet-%EA%B5%AC%EC%A1%B0-%EA%B0%84%EB%9E%B5%ED%95%9C-%EC%97%AD%EC%82%AC
