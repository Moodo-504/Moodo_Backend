# 🐝 Moodo - Backend

Moodo(무도)는 **할 일 기록(To-Do)**과 **감정 일기(Mood Diary)**를 결합한 감성 지능형 생산성 서비스입니다.  
백엔드는 사용자의 할 일, 감정 기록, 감정 유리병, 통계 데이터를 관리하고 프론트엔드와 연동되는 REST API를 제공합니다.

현재 로그인 기능은 추후 개발 예정이므로, 개발 초기 단계에서는 공통 더미 사용자 `user_id = 1`을 기준으로 기능을 구현합니다.

---

## 🔗 관련 링크

- Front-end Repository: [https://github.com/Moodo-Project/Moodo-Frontend](https://github.com/Moodo-Project/Moodo-Frontend)
- Back-end Repository: [https://github.com/Moodo-Project/Moodo-Backend](https://github.com/Moodo-Project/Moodo-Backend)
- Service URL: 배포 후 주소 예정

---

## 🛠 Tech Stack

- Language: Java 17
- Framework: Spring Boot
- Build Tool: Gradle
- Database: MySQL 예정
- ORM: Spring Data JPA
- API Style: REST API
- IDE: IntelliJ IDEA

---

## 💡 Moodo 주요 기능 및 개발 포인트

### 1. 공통 더미 사용자 기반 개발

로그인 기능 개발 전까지 모든 기능은 공통 사용자 ID를 기준으로 동작합니다.

```text
user_id = 1
```

추후 로그인 기능이 추가되면 실제 로그인한 사용자의 ID로 교체할 예정입니다.

---

### 2. Emotions 기본 데이터 관리

사용자가 선택할 수 있는 기본 감정 데이터를 관리합니다.

기본 감정 목록은 다음과 같습니다.

```text
뿌듯, 화남, 피폐, 슬픔, 행복, 엄보싶, 불안, 극대노, 정병
```

---

### 3. To-Do CRUD

사용자의 할 일을 등록, 조회, 수정, 삭제하고 완료 여부를 변경할 수 있습니다.

주요 기능은 다음과 같습니다.

- 할 일 등록
- 할 일 목록 조회
- 할 일 수정
- 할 일 삭제
- 할 일 완료 처리

---

### 4. 감정 유리병

사용자가 날짜별로 감정을 기록하고, 기록된 감정을 유리병 형태로 조회할 수 있습니다.

주요 기능은 다음과 같습니다.

- 감정 기록
- 날짜별 유리병 조회
- 월별 유리병 조회

---

### 5. 통계 기능 예정

할 일 완료율과 감정 기록 데이터를 기반으로 사용자 통계를 제공합니다.

추후 개발 예정 기능은 다음과 같습니다.

- 할 일 완료율 통계
- 감정 기록 통계
- 월별 감정 변화 분석

---

## 🚀 시작하기

### 1. 필수 요구사항

- Java 17 이상
- Gradle
- IntelliJ IDEA 권장
- MySQL 예정

---

### 2. 레포지토리 클론

```bash
git clone https://github.com/Moodo-Project/Moodo-Backend.git
```

```bash
cd Moodo-Backend
```

---

### 3. IntelliJ에서 프로젝트 열기

IntelliJ IDEA 실행 후 다음 순서로 프로젝트를 엽니다.

```text
File → New → Project from Version Control
```

또는 첫 화면에서

```text
Get from VCS
```

를 선택한 뒤 레포지토리 URL을 입력합니다.

```text
https://github.com/Moodo-Project/Moodo-Backend.git
```

프로젝트를 연 뒤 Gradle 프로젝트로 인식되면 의존성 다운로드가 자동으로 진행됩니다.

---

### 4. 로컬 실행

Windows PowerShell 기준:

```powershell
.\gradlew.bat bootRun
```

Mac 또는 Linux 기준:

```bash
./gradlew bootRun
```

정상 실행 시 기본 서버 주소는 다음과 같습니다.

```text
http://localhost:8080
```

---

## ⚙️ DB 설정

현재 프로젝트는 JPA를 사용하므로 DB 연결 설정이 필요합니다.

`src/main/resources/application.properties` 파일에 로컬 DB 정보를 작성합니다.

```properties
spring.datasource.url=jdbc:mysql://localhost:3306/moodo
spring.datasource.username=root
spring.datasource.password=비밀번호
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver

spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
```

DB 비밀번호와 같은 민감 정보는 GitHub에 올리지 않습니다.

---

## 📁 프로젝트 구조

```text
Moodo-Backend
├── src
│   ├── main
│   │   ├── java
│   │   │   └── com.sw8080.moodo
│   │   │       ├── MoodoApplication.java
│   │   │       ├── controller
│   │   │       ├── service
│   │   │       ├── repository
│   │   │       ├── domain
│   │   │       └── dto
│   │   └── resources
│   │       └── application.properties
│   └── test
├── build.gradle
├── settings.gradle
└── README.md
```

---

## 📌 API 설계 초안

### Emotions

| 기능 | Method | URL |
|---|---|---|
| 감정 목록 조회 | GET | `/emotions` |

---

### To-Do

| 기능 | Method | URL |
|---|---|---|
| 할 일 등록 | POST | `/todos` |
| 할 일 목록 조회 | GET | `/todos` |
| 할 일 단건 조회 | GET | `/todos/{todoId}` |
| 할 일 수정 | PATCH | `/todos/{todoId}` |
| 할 일 삭제 | DELETE | `/todos/{todoId}` |
| 할 일 완료 처리 | PATCH | `/todos/{todoId}/complete` |

---

### Emotion Records

| 기능 | Method | URL |
|---|---|---|
| 감정 기록 | POST | `/emotion-records` |
| 날짜별 유리병 조회 | GET | `/emotion-records?date=YYYY-MM-DD` |
| 월별 유리병 조회 | GET | `/emotion-records/month?year=YYYY&month=MM` |

---

## 🧾 공통 응답 형식

```json
{
  "status": 200,
  "message": "요청에 성공했습니다.",
  "data": {}
}
```

---

## ✅ 개발 단계

### 1단계: 공통 더미 사용자 설정

- `user_id = 1` 고정
- 로그인 기능 개발 전까지 모든 기능에서 동일하게 사용

---

### 2단계: Emotions 기본 데이터 생성

- 뿌듯
- 화남
- 피폐
- 슬픔
- 행복
- 엄보싶
- 불안
- 극대노
- 정병

---

### 3단계: 할 일 CRUD 개발

- 할 일 등록
- 할 일 조회
- 할 일 수정
- 할 일 삭제
- 할 일 완료 처리

---

### 4단계: 감정 유리병 개발

- 날짜별 유리병 조회
- 감정 기록
- 월별 유리병 조회

---

### 5단계: 통계 개발 예정

- 할 일 완료율
- 감정 기록 통계

---

### 6단계: 프론트 화면 연결 예정

- 메인
- 리스트
- 달력
- 마이페이지

---

## 🌿 브랜치 전략

```text
main
develop
feature/todo
feature/emotion
feature/statistics
setting/project-config
```

브랜치 생성 예시:

```bash
git checkout -b feature/todo
```

---

## ✏️ Commit Message Convention

| Emoticon | Commit Type | Desc |
| --- | --- | --- |
| ✨ | feat | 새로운 기능 추가 |
| 🐛 | fix | 버그 수정 |
| 📝 | docs | 문서 수정 (md 파일) |
| ♻️ | refactor | 코드 리팩토링 |
| 💄 | style | 코드 formatting, 세미콜론 누락, 코드 자체의 변경이 없는 경우 |
| ✅ | test | 테스트 코드, 리팩토링 테스트 코드 추가 |
| 🚀 | chore | 패키지 매니저 수정 (Dockerfile, gradle, sh, yml) |
| 🚑 | !hotfix | 급하게 치명적인 버그를 고쳐야 하는 경우 |
```

---

## 🧩 이슈 예시

```text
[setting] 공통 더미 사용자 설정
[feat] Emotions 기본 데이터 생성
[feat] 할 일 CRUD 기능 개발
[feat] 감정 유리병 기능 개발
```


