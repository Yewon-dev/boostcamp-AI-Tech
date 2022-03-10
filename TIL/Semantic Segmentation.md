# Semantic segmentation

### FCN (Fully Convolutional Networks)

![](https://production-media.paperswithcode.com/methods/new_alex-model.jpg)

- End-to-end architecture
- Fully connected layer VS Fully convolutional layer
  - Fully connected layer : 영상의 공간정보를 고려하지 않고 하나의 벡터로 표현됨
 
 <img width="987" alt="스크린샷 2022-03-09 오후 3 10 23" src="https://user-images.githubusercontent.com/56240088/157565113-09311a71-5c5e-453f-8e2c-32bf8459b81e.png">

  - Fully convolutional layer
 
 <img width="987" alt="스크린샷 2022-03-09 오후 3 12 36" src="https://user-images.githubusercontent.com/56240088/157565148-2f9fa665-7b74-4b5b-a891-6d50ddc0f93d.png">




**Upsampling**

- Input image의 사이즈로 맞춰주기 위해 사용
- Transposed convolution
- Upsample and convolution

<img width="1656" alt="스크린샷 2022-03-09 오후 3 40 34" src="https://user-images.githubusercontent.com/56240088/157565171-27db7225-fb95-442b-aefa-d7e7df22701e.png">




### U-Net

- 높은 층의 feature과 낮은 층의 feature을 잘 결합하는 방법을 제시

```python
def double_conv(in_channels, out_channels):
  return nn.Sequential(
  	nn.Conv2d(),
  	nn.ReLU(),
    nn.Conv2d(),
  	nn.ReLU()
  )
```



### DeepLab

- CRFs (Conditional Random Fields)

- Dilated convolution

  ![](https://miro.medium.com/max/790/0*3cTXIemm0k3Sbask.gif)

- Pyramid Structure

- Separable Convolution
