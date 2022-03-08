# Image Classification

- Input : 영상
- Output : 해당하는 카테고리, 클래스
- A mapping f(.) that maps an image to a category level

![](https://wikidocs.net/images/page/147017/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2021-09-24_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_3.27.33.png)



### k-NN (k Nearest Neighbors)

- Classifies a query data point according to reference points closest to the query
- 영상간의 유사도 판별이 필요



### CNN (Convolution Neural Networks)

- Locally connected neural networks
- Lower parameters로 효과적인 추출
- Backbone network로 많이 씀

![](https://freecontent.manning.com/wp-content/uploads/sick-dlfild-09.png)



### CNN architectures for image classification

1. LeNet-5
   - a very simple CNN architecture
   - Overall architecture : Conv - Pool - Conv - Pool - FC - FC
2. AlexNet
   - Bigger (7 hidden layers, 60 million parameters, ..)
   - Trained with ImageNet
   - ReLU (Activation Function), Dropout (regularization technique)
3. VGGNet
   - Deeper architecture (16 and 19 layers)
   - Simpler architecture (only 3x3 conv filters blocks, 2x2 max pooling)
   - Better generalization
4. GoogLeNet
   - Inception module
   - Auxiliary classifiers : backpropagation할 때 gradient vanishing을 해결하기 위해
5. ResNet
   - Problem: 네트워크가 깊어질수록 정확도가 포화됨. overfitting이 원인이라면 더 깊은 레이어가 더 높은 에러를 발생해야하는데 그렇지 않음 -> overfitting이 원인이 아님
   - Solution: Shortcut connection
6. DenseNet
   - Every output of each layer is concatenated along the channel axis
   - 훨씬 이전의 layer에 대한 정보도 전달됨
7. SENet
   - Attention across channels
   - Squeeze: by global average pooling
   - Excitation: FC layer를 통해 channel간의 연관성 고려
8. EfficientNet
   - Building deep, wide, and high resolution networks in an efficient way



## Data augmentation

Crop, Shear, Brightness, Perspective, Rotate...

**Brightness adjustment**

```python
img[:,:,:] += 100
```

**Rotate, Flip**

```python
img_rotated = cv2.rotate(image, cv2.ROTATE_90_CLOCKWISE)
img_flipped = cv2.rotate(image, cv2.ROTATE_90)
```

**Crop**

```python
img_cropped = image[y_start : y_start + crop_y_size, x_start : x_start + crop_x_size, :] ## height, width, channels
```

**Affine transformation**

- 'line', 'lenght ratio', 'parallelism' 유지

```python
pts1 = np.float32([[], [], []])
pts2 = np.float32([[], [], []])
M = cv2.getAffineTransform(pts1,pts2) # pts1 to pts2 하는 변환행렬 반환
shear_img = cv2.warpAffine(image, M, (cols,rows)) # 이미지 변환
```

**CutMix**

- Mixing both images and labels

**RandAugment**

- Automatically finding the best sequence of augmentations to apply
- Two parameters
  - Which? How much?



### Transfer Learning

- Knowledge learned from one dataset can be applied to other datasets

**Approach 1.** Transfer knowledge from a pre-trained task to a new task

- Chop off the FC of the pre-trained model, add and only re-train a new FC

**Approach 2.** Fine-tuning the whole model

- 1과 같은 방법이지만 pre-trained model도 같이 학습시킴
- Set learning rates differently



### Knowledge distillation

- 큰 모델(Teacher)에서 작은 모델(student)로 지식 전달 -> model compression에 유용하게 사용
- Also, used for pseudo-labeling
- The student network mimics outputs of the teacher network
- 방법1 (unlabeled data)
  - Teacher Model과 Student Model에 각각 학습 -> 각각의 output에 대해 KL div.Loss 구함 -> backpropagation해서 Student Model만 학습
- 방법2 (labeled data)
  - Distillation Loss
    - KLdiv (Soft label, soft prediction)
    - Learn what teacher networks knows by mimicking
  - Student Loss
    - CrossEntropy(Hard label, Soft prediction)
    - Learn the **right answer**
- 방법3 (Semi-supervised learning)
  - Unsupervised (No label) + Fully Supervised (fully labeled)
  - ![](https://media.vlpt.us/images/blush0722/post/53384dac-7903-4d57-a9ac-78c227d118fd/image.png)





**Hard label (One-hot vector) / Soft label (after softmax)**

**Softmax with temperature(T)**

- control difference in output between small & large input values
- a large T smoothens large input value differences
- 중간값에 몰려있으면 전반적인 분포를 확인하기 쉬움

![](https://miro.medium.com/max/1400/1*LALlbjIIgjlaDnOW3LNULw.png)





## Self-training

Augmentation + Teacher-Student networks + semi-supervised learning

- Self-training with noisy student

  ![](https://media.vlpt.us/images/blush0722/post/eab5dc89-4041-4520-a77f-3b09fbca6cec/image.png)

![](https://media.vlpt.us/images/blush0722/post/ed64f299-18e5-4bc5-9b6e-eee1e71016d1/image.png)
