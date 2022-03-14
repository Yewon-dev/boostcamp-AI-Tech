# Object Detection

## 1. What is Object Detection?

- Classification + Box localization

#### 1.1 What are the applications of object detection

- Autonomous driving
- OCR (Optical Character Recognition)

## 2. Two-stage detector (R-CNN family)

- Traditional methods
  - Gradient-based detector: 영상안의 경계선들의 특징을 이용하여 설계
  - Selective search: over-segmentation -> 비슷한 영역끼리 merge -> segmentation을 포함하는 bounding box를 물체의 후보군으로 지정

#### 2.1 R-CNN

<img width="400" alt="스크린샷 2022-03-14 오후 11 04 09" src="https://user-images.githubusercontent.com/56240088/158196648-3b63f779-f025-4cc2-b999-a9fea8f30398.png">


- 단점 : 속도가 느리고 성능 향상에 한계가 있음

#### 2.2 Fast R-CNN

<img width="400" alt="스크린샷 2022-03-14 오후 11 06 53" src="https://user-images.githubusercontent.com/56240088/158196715-b69ece13-fae0-48ea-b076-649d88dee21e.png">


- Conv feature map: 영상 전체에 대한 feature을 한번에 추출
- RoI layer을 이용해서 각각의 region에 대해 feature 정보 추출

#### 2.3 Faster R-CNN

<img width="400" alt="스크린샷 2022-03-14 오후 11 17 49" src="https://user-images.githubusercontent.com/56240088/158196875-8e0845ef-364f-44d4-96e5-f26e7e7dd679.png">


- End-to-end object detection by neural region proposal

- Anchor boxes: A set of pre-defined bounding boxes

- RPN (Region Proposal Network)
- <img width="400" alt="스크린샷 2022-03-14 오후 11 17 39" src="https://user-images.githubusercontent.com/56240088/158196976-77d08004-d815-4deb-84a5-a6d6d815b56c.png">

- NMS (Non-Maximum Suppression)

  - bounding box를 filtering하는 알고리즘

  

**Summary of the R-CNN family**

<img width="400" alt="스크린샷 2022-03-14 오후 11 20 45" src="https://user-images.githubusercontent.com/56240088/158197059-4a11bc5c-562b-4b1f-9e3d-611776082c0a.png">


## 3. Single-stage detector

- 목적 : real time detection

#### 3.1 YOLO

<img width="599" alt="스크린샷 2022-03-14 오후 11 24 13" src="https://user-images.githubusercontent.com/56240088/158196587-a4f8a786-faea-4c80-9007-df6fccb1ae7f.png">


#### 3.2 SSD

<img width="810" alt="스크린샷 2022-03-14 오후 11 29 32" src="https://user-images.githubusercontent.com/56240088/158197160-001a5b7c-7c9d-47c9-9ada-ee27c9584926.png">

- multi-scale의 각각의 Multiple feature map에 따라서 다양한 bounding box의 shape을 고려

## 4. Single-stage detector vs. two-stage detector

#### 4.1Focal loss

- Cross entropy loss의 확장
  - Over-weights hard or misclassified examples
  - Down-weights easy examples
- Class imbalance을 다룸

#### 4.2 RetinaNet

- Feature Pyramid Networks(FPN) + class/box prediction branches
- Class head와 box head를 따로 구성 -> classification과 box regresstion을 dense하게 수행

## 5. Detection with Transformer

- DETR (Detection TRansformer)
  - ![](https://rauleun.github.io/assets/images/200914-DETR/detr.png)
- Detecting objects as points
  - Bounding box 표현 대신 물체의 중심점을 이용한다던지..
  - CornerNet/CenterNet
