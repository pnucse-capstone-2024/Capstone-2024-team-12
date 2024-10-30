### 1. 프로젝트 소개

팬데믹을 거치며 성인 남성의 비만율은 46.3%까지 증가하였고, 남학생과 여학생의 비만율은 각각 17.5%, 9.1%로 10년 전 대비 2배 이상 증가하였습니다.
체중 감량이나 증량을 원하는 사람들에게 개인의 목표에 맞는 일일 섭취 칼로리와 영양소를 정확하게 계산해 제공함으로써 목표 달성을 보다 쉽게 도울 수 있는 서비스가 요구됩니다.

### 2. 팀소개

이혁재, jeuss385@naver.com, 프론트앤드 개발, 데이터 수집

김상해, pelikan@pusan.ac.kr, 백앤드 개발, 데이터 수집

문성재, paulmoon00@naver.com, 모델 학습, FastAPI 서버 개발

### 3. 시스템 구성도

![구성도_이미지](https://github.com/user-attachments/assets/306ef462-213c-4208-b65a-45763354c70e)

### 4. 소개 및 시연 영상

[![작품_소개_영상](http://img.youtube.com/vi/1qgnZnbgKTY/0.jpg)](https://www.youtube.com/watch?v=1qgnZnbgKTY)


### 5. 설치 및 사용법

본 프로젝트는 python 3.8이상과 java 21, springboot 3.0이상의 환경에서 동작 가능합니다.\
다음의 과정으로 관련 패키지의 설치와 실행이 가능합니다.

**웹서버 빌드 및 실행**
```
cd ./src/web_server
./gradlew build clean
cd /build/libs
cp ../../FoodNutrient.csv .
java -jar SmartPlate-0.0.1-SNAPSHOT.jar
```
**인공지능 서버 빌드 및 실행**
```
cd ./src/ai_server
pip install -r requirements.txt
nohup uvicorn main:app --host=0.0.0.0 --port=8000 &
```

### 6. 데이터 수집

기존 AI-Hub 음식 양 추정 데이터는 식판에서 사용하기 어렵다고 판단되었습니다. 따라서 직접 식판 위에 음식을 올려 무게를 측정하면서 직접 촬영하여 데이터를 수집하였습니다. 밥류의 음식들은 50g씩 무게를 측정하여 촬영하였고 반찬류는 25g씩 무게를 맞추어 촬영하였습니다.

| 이미지 | <img src="./src/Images/100.jpg" width="200" hieght="300"/> | <img src="./src/Images/150.jpg" width="200"/> | <img src="src/Images/200.jpg" width="200"/> | <img src="src/Images/250.jpg" width="200"/> |
|-----|------------------------------------------------------------|-----------------------------------------------|---------------------------------------------|---------------------------------------------|
| 중량  | 100g                                                       | 150g                                          | 200g                                        | 250g                                        |

### 7. 디렉토리 구조
**Food-Ai-Server**
```
ai_server
├─ .gitignore
├─ .idea
│  ├─ .gitignore
│  ├─ ai.iml
│  ├─ aws.xml
│  ├─ checkstyle-idea.xml
│  ├─ google-java-format.xml
│  ├─ libraries
│  │  └─ ai_server.xml
│  ├─ misc.xml
│  ├─ modules.xml
│  └─ workspace.xml
├─ README.md
├─ ai.py
├─ ai_server.zip
├─ amount_model
│  └─ rice_model.pkl
├─ food-detection.pt
├─ main.py
├─ requirements.txt
└─ tray-detection.pt

```

**Web Server**
```
web_server
├─ .github
│  └─ pull_request_template.md
├─ .gitignore
├─ FoodNutrient.csv
├─ HELP.md
├─ LICENSE
├─ README.md
├─ gradle
│  └─ wrapper
│     ├─ gradle-wrapper.jar
│     └─ gradle-wrapper.properties
├─ gradlew
├─ gradlew.bat
├─ settings.gradle
└─ src
   ├─ main
   │  ├─ java
   │  │  └─ pnu
   │  │     └─ project
   │  │        └─ smartplate
   │  │           ├─ Application.java
   │  │           ├─ config
   │  │           │  └─ AppConfig.java
   │  │           ├─ controller
   │  │           │  └─ FoodAnalysisController.java
   │  │           ├─ model
   │  │           │  ├─ FoodClass.java
   │  │           │  ├─ FoodInfo.java
   │  │           │  └─ FoodNutrient.java
   │  │           └─ service
   │  │              └─ FoodAnalysisService.java
   │  └─ resources
   │     ├─ application-dev.properties
   │     ├─ application-prod.properties
   │     ├─ application.properties
   │     ├─ static
   │     │  ├─ javascript
   │     │  │  ├─ index.es6
   │     │  │  ├─ progressbar.es6
   │     │  │  ├─ result.es6
   │     │  │  └─ upload.es6
   │     │  └─ style
   │     │     ├─ index.css
   │     │     ├─ progressbar.css
   │     │     ├─ result.css
   │     │     └─ upload.css
   │     └─ templates
   │        ├─ index.html
   │        ├─ progressbar.html
   │        ├─ result.html
   │        └─ upload.html
   └─ test
      └─ java
         └─ pnu
            └─ project
               └─ smartplate
                  └─ SmartPlateApplicationTests.java

```