# 🐝 Moodo - Backend

Moodo(무두)는 할 일의 완료 결과를 감정으로 표현하는 감성 To-Do List 서비스입니다.  
사용자는 단순히 할 일을 체크하는 데서 그치지 않고, 할 일을 마친 뒤 느낀 감정을 함께 기록하며 하루의 성취와 감정 변화를 확인할 수 있습니다.

---

## 🔗 관련 링크

- Front-end Repository: [https://github.com/Moodo-504/Moodo_Frontend](https://github.com/Moodo-504/Moodo_Frontend)
- Service URL: 배포 후 주소 예정

---

## 🛠 Tech Stack

- Language: Java 17
- Framework: Spring Boot
- Build Tool: Gradle
- ORM: Spring Data JPA
- Database: MySQL
- API Style: REST API
- IDE: IntelliJ IDEA

---

## 💡 Moodo 주요 기능 및 개발 포인트

### 1. To-Do & Emotion Integration

사용자가 할 일을 완료한 뒤, 그 결과를 감정으로 기록할 수 있습니다.  
단순한 완료 체크를 넘어 할 일을 수행한 후의 성취감, 피로감, 행복감 등을 함께 남길 수 있습니다.

### 2. Emotion Bottle

날짜별로 기록된 감정을 감정 유리병 형태로 조회할 수 있습니다.  
사용자는 특정 날짜 또는 월별 감정 기록을 확인할 수 있습니다.

### 3. Todo Management

사용자는 할 일을 등록, 조회, 수정, 삭제하고 완료 상태를 변경할 수 있습니다.

### 4. Statistics

추후 할 일 완료율과 감정 기록 데이터를 기반으로 통계 기능을 제공합니다.

## 📌 API 설계 초안

### Emotions

| 기능 | Method | URL |
| --- | --- | --- |
| 감정 목록 조회 | GET | `/emotions` |

### To-Do

| 기능 | Method | URL |
| --- | --- | --- |
| 할 일 등록 | POST | `/todos` |
| 할 일 목록 조회 | GET | `/todos` |
| 할 일 단건 조회 | GET | `/todos/{todoId}` |
| 할 일 수정 | PATCH | `/todos/{todoId}` |
| 할 일 삭제 | DELETE | `/todos/{todoId}` |
| 할 일 완료 처리 | PATCH | `/todos/{todoId}/complete` |

### Emotion Records

| 기능 | Method | URL |
| --- | --- | --- |
| 감정 기록 | POST | `/emotion-records` |
| 날짜별 유리병 조회 | GET | `/emotion-records?date=YYYY-MM-DD` |
| 월별 유리병 조회 | GET | `/emotion-records/month?year=YYYY&month=MM` |

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


---

## ⚠️ 주의 사항

- DB 비밀번호, API Key 등 민감 정보는 GitHub에 올리지 않습니다.
- 각 기능은 이슈 단위로 브랜치를 생성하여 작업합니다.
