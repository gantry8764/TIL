###### 0725

## AI 인공지능 API  

### Naver AI API 서비스
- Naver CLOVA
- 네이버에서 개발한 인공지능 기술로 AI Service 제공
- API 형태로 이용 가능
- 네이버 클라우드 플래폼에서 이용할 수 있는 서비스
- Naver Cloud Platform(NCP)

### Naver AI API
- CLOVA Facec Recognition(CFR)
  - 얼굴 인식
  - 유명인 얼굴 인식
- CLOVA OCR(Optical Character Recognition)
- CLOVA Speech Recognition(CSR)
- CLOVA Voice - Premium
- CLOVA Chatbot
- Pose Estimation
- Object Detection / Papago

---

### CLOVA Face Recognition(CFR)
- 이미지 속의 얼굴을 감지하고 인삭하여 얻은 다양한 정보를 제공하는 API 서비스
- 입력된 비전 데이터(이미지 파일)를 통해 얼굴을 인식하거나 얼굴을 감지
- **유명인 얼굴 인식** : 닮은 유명인 이름, 닮은 정도
- **얼굴 감지**
  - 감지된 얼굴을 분석한 정보
  - 성별, 추정 나이, 감정, 얼굴 방향 등

### CLOVA OCR(Optical Character Recognition)
- 광학 문자 인식 API 서비스
- 사진(이미지) 속에서 텍스트 정보를 찾고 의미를 판별하는 기술
- 언어와 이미지 데이터를 입력 받고, 그에 맞는 인식 결과를 텍스트로 반환
- 텍스트 : 이미지 내에서 텍스트 추출 반환
- 영수증 : 영수증을 읽어서 추출 항목 반환  

### CLOVA Speech Recognition(CSR)
- 음성 합성 API 서비스
- 텍스트를 음성으로 변환
- TTS(Text-to-Speech)
- 텍스트 파일을 입력 받아서 변환된 음성 파일 반환 - mp3 / wav
- 언어, 음색 선택 가능

### CLOVA Voice - Premium
- CLOVA Speech Recognition(CSR)
- 서비스 통합

### CLOVA Chatbot
- 챗 봇 제작 API 서비스
- 사용자의 질문 의도를 이해하여 고객 대응 등 다양한 서비스에 활용할 수 있는 챗 봇 제작 지원

### Pose Estimation
- 입력된 비전 데이터를 통해 사람을 인식하고 포즈 분석
- 이미지 속의 사람을 감지하고 주요 신체부위(18개)의 좌표정보와 정확도를 얻을 수 있음  

### Object Detection
- 이미지 내에 사람, 자동차, 동물 등 객체의 타입과 위치를 감지하여 정보 제공  
- 탐지된 객체명, 객체 수, 바운딩 박스용 좌표, 객체별 확률 값

---

### Spring AI API 사용
1) 서비스 요청(뷰 페이지 : index.jsp)
2) 컨트롤러
3) 서비스
   1) API 요청 코드를 서비스 클래스의 메소드 작성
   2) JSON 파싱 및 결과 반환
   3) VO / 리스트 사용
4) 컨트롤러
5) 뷰 페이지로 결과 출력

### Naver API 등록/사용
1) AI Platform 계정으로 접속(1인 1계정)
2) 첫 접속 시 비밀번호 변경(필수)
3) Console로 이동
4) Service
5) AI-NAVER API / Application
6) \+ Application 등록

---

### 스프링 부트 프로젝트 예제 생성
- 프로젝트명 : naver_ai_platform
- 패키지명 : com.ai.project
- Dependencies
  - JDBC API
  - MySQL Driver
  - MyBatis Framework
  - Spring web
- JSP 설정
- application.properties 파일에 설정 추가
- org.json <Dependency> 추가
  - ```
    <dependency>
        <groupId>org.json</groupId>
        <artifactId>json</artifactId>
        <version>20220320</version>
    <dependency>
    ```
- index.jsp 생성
- controller 패키지 생성
  - APIController.java 생성 - index 열기
    - @ComponentScan(basePackages = {"com.ai.project"})

---

### 얼굴 인식
- celebrity : 유명인 얼굴 인식 API
  - 전송 : 이미지(얼굴 사진)
  - 결과   
    - JSON 형태로 반환
    - JSON 데이터 파싱해서 추출 및 출력
    - JSON 파싱 결과를 VO에 저장
  - face : 얼굴 감지 API
  - model 패키지 / CelebrityVO 생성
    - value : 유명인 이름
    - confidence : 정확도
    - service 패키지 생성
      - CelebrityFaceRecogService 클래스 생성
      - celebrityFaceRecog() 메소드 생성
      1) 이미지 파일 보내고 결과 받아서 콘솔에 출력
       - 자바 API 코드 복사해서 붙여 넣기
       - ``import java.io.File;``
       - ``import java.net.URL;``
       - Client ID / Client Secret 입력
      2) JSON 결과 파싱
      3) 파일 업로드 / 이미지 출력(서비스 제공)