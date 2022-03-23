# Instance segmentation

- Semantic segmentation + distinguishing instances

### Mask R-CNN

- RoIAlign : 소수점 pixel level의 pooling 지원
- Faster R-CNN + Mask branch

### YOLACT (You Only Look At CoefficienTs)

<img width="911" alt="스크린샷 2022-03-15 오전 12 43 36" src="https://user-images.githubusercontent.com/56240088/158218439-34f1b08b-90fe-4483-8641-031d521f4142.png">

- Real-time instance segmentation network
- mask prototypes 생성
- Prototype을 적당히 작게 설정하고, 선형결합 후 다양한 마스크를 생성하는 것이 중요

### YolactEdge

- 이전의 keyframe의 feature을 다음 frame에 전달 -> feature map의 계산량을 줄임

# Panoptic segmentation

<img width="911" alt="스크린샷 2022-03-15 오전 12 46 09" src="https://user-images.githubusercontent.com/56240088/158218478-cc1e8189-0db8-45ff-ba3c-6d814997f759.png">



### UPSNet

<img width="911" alt="스크린샷 2022-03-15 오전 12 47 44" src="https://user-images.githubusercontent.com/56240088/158218511-b769dbaa-a4ab-4863-88f3-d06de63aa6b5.png">


### VPSNet

<img width="656" alt="스크린샷 2022-03-15 오전 12 56 39" src="https://user-images.githubusercontent.com/56240088/158218536-4287b03a-c094-42a5-a546-abd8f3047bc6.png">


# Landmark localization

- Keypoint estimation: Predicting the coordinates of keypoints.
- Coordinate regression:  부정확..
- Heatmap classification: 성능이 좋지만 계산량이 많음



### Hourglass network

<img width="910" alt="스크린샷 2022-03-15 오전 1 23 52" src="https://user-images.githubusercontent.com/56240088/158218586-afac21c7-c0df-4c6f-af93-8bbe1dc247bc.png">




### DensePose

<img width="910" alt="스크린샷 2022-03-15 오전 1 27 52" src="https://user-images.githubusercontent.com/56240088/158218603-0364e40f-dfbb-4bb1-b00c-262fab4e7975.png">


- UVmap: a flattened representation of 3D geometry

### RetinaFace

<img width="910" alt="스크린샷 2022-03-15 오전 1 28 37" src="https://user-images.githubusercontent.com/56240088/158218630-8b85adf7-90e2-4531-921d-3cef6da21489.png">

# CornerNet & CenterNet

### CornerNet

- Bounding box = {Top-left, Bottom-right} corners

### CenterNet

- (1) Bounding box = {Top-left, Bottom-right, **Center**} points
- (2) Bounding box = {**Width**, **Height**, Center} points

