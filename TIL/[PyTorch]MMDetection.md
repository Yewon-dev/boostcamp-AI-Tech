# MMDetection

- Object Detection OpenSource Library



### Pipeline

![](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fcxcbrs%2Fbtra9WN0Q1s%2FhkPC0TYXjQMtZZUQKbRJLK%2Fimg.png)

- Backbone : 입력 이미지를 feature map으로 변환
- Neck : Backbone 과 Head 연결, Feature map 재구성 (FPN)
- DenseHead : feature map의 dense location 수행
- RoIHead : RoI 특징을 입력으로 받아 box 분류, 좌표 회귀 등을 예측

</br>

config 파일을 통해 dataset, model, schduler, optimizer 수정할 수 있으므로 틀이 갖춰진 config를 상속 받고, 필요한 부분만 수정하면 된다.

Baseline code 기준으로 config 파일을 예를 들면,
<img width="805" alt="스크린샷 2022-03-22 오후 8 36 21" src="https://user-images.githubusercontent.com/56240088/159505847-b4dbf58f-0c7d-4d31-b01b-0157dec8fff7.png">

총 네개의 파일을 상속받은 것을 볼 수 있다.

</br>

상속된 파일들을 살펴보면,



위치 : `mmdetection/configs/_base_`

- `models` : 기본적으로 사용가능한 모델 정의
  - Type: 모델 유형 (ex. FasterRCNN, ...)
  - Backbone: ResNet, ...
    - `__init__`에 원하는 backbone model이 없다면 만들면 됨
    - <img width="805" alt="스크린샷 2022-03-22 오후 8 48 15" src="https://user-images.githubusercontent.com/56240088/159506103-e6637a51-e6cd-4679-838d-f0f0fa867087.png">
    - 새로운 backbone 등록 -> `__init__`에 모듈 Import -> 등록한 backbone 사용
  - Neck: FPN, ...
  - RPN Head: Region Propasal Network (ex. RPNHead, ...)
  - RoI Head: StandardRoIHead, CascadeRoIHead, ...
- `datasets` : 데이터셋 정의.
  - Train, val, test dataset에 대해 정의되어있고, pipeline도 정의되어 있음.

<img width="805" alt="스크린샷 2022-03-22 오후 8 41 42" src="https://user-images.githubusercontent.com/56240088/159505953-28cc702c-5c2f-47b4-9434-68fddf11a9fe.png">

  - 초록색 글씨는, 추가된 parameters
  - 주황색 글씨는, 영향을 받는 parameters

- `schedules` 
  - Optimizer: SGD, Adam, ...
  - Training Schedules: 
    - lr, runner



