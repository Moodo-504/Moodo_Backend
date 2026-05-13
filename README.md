# 🐝 Moodo - Backend

Moodo(무두)는 할 일의 완료 결과를 감정으로 표현하는 감성 To-Do List 서비스입니다.  
사용자는 단순히 할 일을 체크하는 데서 그치지 않고, 할 일을 마친 뒤 느낀 감정을 함께 기록하며 하루의 성취와 감정 변화를 확인할 수 있습니다.

현재 로그인 기능은 추후 개발 예정이므로, 개발 초기 단계에서는 공통 더미 사용자 `user_id = 1`을 기준으로 기능을 구현합니다.

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
- Database: MySQL 예정
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

---

## 📌 개발 초기 공통 규칙

로그인 기능 개발 전까지 모든 기능은 아래 더미 사용자를 기준으로 개발합니다.

```text
user_id = 1
```

추후 로그인 기능이 추가되면 실제 로그인 사용자 ID로 교체할 예정입니다.

---

## 😊 기본 감정 목록

```text
뿌듯, 화남, 피폐, 슬픔, 행복, 엄보싶, 불안, 극대노, 정병
```

---

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

### 3단계: 할 일 CRUD 개발

- 할 일 등록
- 할 일 조회
- 할 일 수정
- 할 일 삭제
- 할 일 완료 처리

### 4단계: 감정 유리병 개발

- 날짜별 유리병 조회
- 감정 기록
- 월별 유리병 조회

### 5단계: 통계 개발 예정

- 할 일 완료율
- 감정 기록 통계

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

### Commit Message 예시

```text
✨ feat: 할 일 등록 API 구현
✨ feat: 감정 기록 API 구현
🐛 fix: 할 일 완료 처리 오류 수정
📝 docs: README 수정
🚀 chore: Gradle 설정 수정
♻️ refactor: Todo 서비스 로직 분리
```

---

## 🧩 이슈 예시

```text
[setting] 공통 더미 사용자 설정
[feat] Emotions 기본 데이터 생성
[feat] 할 일 CRUD 기능 개발
[feat] 감정 유리병 기능 개발
```

---

## ⚠️ 주의 사항

- DB 비밀번호, API Key 등 민감 정보는 GitHub에 올리지 않습니다.
- 로그인 기능 개발 전까지는 `user_id = 1`을 사용합니다.
- 프론트엔드와 API 응답 형식을 맞추기 위해 공통 응답 형식을 유지합니다.
- 기능 구현 전 API 명세를 먼저 정리하고 개발합니다.
- 각 기능은 이슈 단위로 브랜치를 생성하여 작업합니다.
