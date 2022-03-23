**Problems**

- 실험 추적의 어려움
- 코드 재현의 어려움
- 모델 패키징 및 배포의 어려움
- 모델 관리를 위한 중앙 저장소 부재



# MLflow

- 머신러닝 실험, 배포를 쉽게 관리할 수 있는 오픈소스

### 핵심 기능

1. Experiment Management & Tracking
   - 머신러닝 관련 실험들 관리 및 기록
   - 각 실행에 사용한 소스 코드, 하이퍼 파라미터, Metric, 부산물 등을 저장
2. Model Registry
   - 모델 저장소에 모델이 저장될 때마다 해당 모델에 버전이 자동으로 올라감
3. Model Serving
   - Model Registry에 등록한 모델을 REST API 형태의 서버로 Serving
   - Input = Model의 Input
   - Output = Model의 Output



-----

### MLflow Component

1. MLflow Tracking
   - 머신러닝 코드 실행, 로깅을 위한 API, UI 제공
   - Tracking 결과를 Local, Server에 기록하여 비교 가능
2. MLflow Project
   - 머신러닝 프로젝트 코드를 패키징하기 위한 표준
   - Entry point 를 같이 저장
3. MLflow Model
   - Model 파일과 코드로 저장하여 재현가능하도록 함
4. MLflow Registry
   - MLflow Model 전체의 Lifecycle에서 사용할 수 있는 중앙 모델 저장소

----

**MLflow Download**

```bash
pip install mlflow
```

-----

### Experiment

- MLflow에서 제일 먼저 Experiment 생성
- 정해진 Metric로 모델 평가
- 하나의 Experiment는 여러 Run(실행)을 가짐

**Experiment 생성**

```bash
mlflow experiments create --experiment-name my-first-experiment
```

`ls -al`을 하게 되면 **mlruns**라는 폴더가 생김

- run에 대한 기록을 저장

**Experiments list 출력**

```bash
mlflow experiments list
```

-----

**ML code 작성**


<img width="808" alt="스크린샷" src="https://user-images.githubusercontent.com/56240088/154527393-50eb0c1b-d2c1-425b-a0db-1d8cde68d48e.png">

-----

### MLProject

MLProject 폴더 생성 후, 파일 생성

<img width="808" alt="스크린샷" src="https://user-images.githubusercontent.com/56240088/154527525-b49acb76-c7be-4019-8c66-ee82e18d162e.png">

-----

### Run

- 하나의 Run은 코드를 한번 실행하는 것을 의미
- Logging
  - Source : 실행한 Project의 이름
  - Version : 실행 Hash
  - Start & end time
  - Parameters
  - Metrics : 모델 평가 지표
  - Tags
  - Artifacts : 실행 과정에서 생기는 다양한 파일들 (image, model Pickle)

```bash
mlflow run logistic_regression --experiment-name my-first-experiment --no-conda
```

-----

### MLflow UI

- MLflow web UI 생성

```bash
mlflow ui
```

<img width="787" alt="스크린샷" src="https://user-images.githubusercontent.com/56240088/154527669-6750ae4a-9c44-47ad-bd36-38ac11bb9516.png">


**Local host : 5000 port**

<img width="787" alt="스크린샷" src="https://user-images.githubusercontent.com/56240088/154527749-dd6f9c50-b316-4e43-8f36-4daf8c3e4b91.png">


살펴보면 실행한 run 기록과 model 관련 Artifacts 등이 표시된다.



----

### MLflow autolog

**❗️주의사항❗️**

- 모든 프레임워크에서 사용가능하지 않음
- https://mlflow.org/docs/latest/tracking.html#id2



----

### MLflow Architecture

- **Python Code** w/ MLflow package
  - 모델을 만들고 학습하는 코드
  - mlflow run으로 실행
- **Tracking Server**
  - 파이썬 코드가 실행되는 동안 **Parameter, Metric, Mode**l 등 메타 정보 저장
  - 파일 혹은 DB에 저장
- **Artifact Store**
  - 파이썬 코드가 실행되는 동안 생기는 **Model File, Image** 등의 Artifact 저장
  - 파일 혹은 스토리지에 저장

