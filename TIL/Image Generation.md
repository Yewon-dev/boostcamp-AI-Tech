# Conditional Generative Model

- 일반 Generative model과 차이점

<img width="831" alt="스크린샷 2022-03-16 오전 12 22 40" src="https://user-images.githubusercontent.com/56240088/158432604-c860da16-6294-480d-a867-0f52ae2e5850.png">

<img width="831" alt="스크린샷 2022-03-16 오전 12 26 06" src="https://user-images.githubusercontent.com/56240088/158432619-71bf251e-bcfa-4333-ab18-7823c165273b.png">


### Conditional GAN and image translation

- Image-to-Image translation
- Style transfer, Super resolution, Colorization ...

### Example: Super resolution

- low resolution to high resolution
- SRGAN generates more **realistic** and sharp images than SPResNet (MSE loss)



# Image translation GANs



### Pix2Pix

- Loss function = GAN loss + L1 loss

  - L1 loss를 사용하여 기대하고 있는 결과인 y와 비슷한 영상 출력
  - GAN loss를 더해 조금 더 realistic하게 출력
  - GAN loss만 사용하기엔 불안정하여 L1으로 가이드 제시 (보조)

<img width="444" alt="스크린샷 2022-03-16 오전 12 55 53" src="https://user-images.githubusercontent.com/56240088/158432680-17cc6a7e-9184-4a8e-8bc5-7be4a0c7686b.png">


### CycleGAN

- Pix2Pix는 pairwise data가 필요 -> 어렵거나 불가능

- CycleGAN: **non-pairwise** datasets으로 translation 가능

- CycleGAN loss = GAN loss (in both direction) + **Cycle-consistency loss**

  - GAN loss = ![](https://latex.codecogs.com/svg.image?\inline&space;L(D_x)&plus;L(D_Y)&plus;L(G)&plus;L(F))

<img width="288" alt="스크린샷 2022-03-16 오전 1 02 58" src="https://user-images.githubusercontent.com/56240088/158432733-a86ab840-9bc3-4575-9c1b-71a59bc6cbdf.png">

  - GAN loss만 사용한다면 Mode Collapse 발생 = input에 상관없이 하나의 output만 출력

  - Solution: **Cycle-consistency loss**

    - X(or Y)로 다시 돌아왔을 때, 차이가 있으면 안됨! content가 유지되도록 유도
    
<img width="653" alt="스크린샷 2022-03-16 오전 1 07 35" src="https://user-images.githubusercontent.com/56240088/158432837-38341ccf-1dfd-436d-944b-401f41737cdf.png">


### Perceptual loss

- Another way to get a high-quality image without GAN
- Image Transform Net: input image를 transform하여 output 출력
- Loss Network: pre-trained VGG model (Fixed during training Image Transform Net)

<img width="653" alt="스크린샷 2022-03-16 오전 1 21 53" src="https://user-images.githubusercontent.com/56240088/158432897-44cf5fb7-b895-45c8-bd46-b51f2852ac49.png">


- **Feature reconstruction loss**: ![](https://latex.codecogs.com/svg.image?\hat{y})의 feature map과 Content target (X)의 feature map의 L2 loss 계산

- **Style reconstruction loss**: ![](https://latex.codecogs.com/svg.image?\hat{y})과 Style target의 feature map을 구한 후, Gram matrix으로 변환 -> ![](https://latex.codecogs.com/svg.image?\hat{y})의 Gram matrices가 Style target의 Gram matrices를 따르도록 연산

- Gram matric: 공간적인 정보를 제외한 feature map의 통계적인 특성

    



# Various GAN applications

- Deepfake
- Face de-identification
- Face anonymization with passcode
