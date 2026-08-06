# 26/08/06


| 순서 | 결정할 것 |
|------|-----------|
| 1 | 기존 Amazon 크롤러가 실제로 어떤 CSV를 생성하는지 확인 |
| 2 | 최종 데이터 컬럼 구조 확정 |
| 3 | 영구 저장 방식 결정 (SQLite 또는 JSONL) |
| 4 | AI 분석 결과(JSON) 저장 구조 확정 |
| 5 | 대시보드 구성 및 차트(3~4개) 확정 |

***


# 📋 AI 리뷰 분석 프로젝트 - 1차 팀 미팅 체크리스트

> **목표:** 개발을 시작하기 전에 팀 전체가 같은 방향을 바라보도록 핵심 사항을 결정한다.

---

# 1. 프로젝트 목표 확인 (5분)

### 최종 목표

Amazon 리뷰 데이터를 AI로 분석하여

* 감정 분석
* 키워드 추출
* 통계 분석
* 시각화
* 리포트 생성

까지 가능한 **CLI 기반 Python 프로그램**을 완성한다.

### 개발 원칙

* 14일까지 완성
* 복잡한 기능보다 안정적인 구현 우선
* 요구사항 충족을 최우선으로 한다.
* 웹 대시보드는 구현하지 않는다.

---

# 2. 데이터 구조 결정 (10분)

### Amazon 리뷰 데이터 확인

기존 크롤링 프로그램에서 어떤 컬럼이 생성되는지 확인한다.

예시

| 컬럼       | 사용 여부 |
| -------- | ----- |
| review   | ✅     |
| rating   | ✅     |
| date     | ✅     |
| product  | ✅     |
| reviewer | 선택    |

### 최종 컬럼 확정

최소 다음 컬럼을 사용한다.

```text
id
review
rating
date
product
sentiment
confidence
```

필요하면 추가 컬럼을 정의한다.

---

# 3. 저장 방식 결정 (5분)

둘 중 하나 선택

* SQLite
* JSONL

또는

* Raw 저장
* Clean 저장

구조를 어떻게 가져갈지 결정한다.

---

# 4. AI 분석 결과 구조 결정 (5분)

AI가 어떤 형식으로 반환할지 통일한다.

예시

```json
{
  "sentiment": "positive",
  "confidence": 0.94
}
```

추가로

* keywords
* summary
* suggestion

등 저장 형식을 함께 결정한다.

---

# 5. 역할 분담 확정 (5분)

### A

* Import
* Clean
* 저장(DB)

---

### B

* AI API
* 감정 분석
* 키워드
* 요약

---

### C

* CLI
* argparse
* config
* logging
* 모듈 연결

---

### D

* 통계 분석
* matplotlib 차트
* Dashboard
* Report
* QA

---

# 6. 대시보드 구성 확정 (5분)

필수 차트

* 감정 분포
* 시간별 감정 변화
* 별점별 감정 분포

추가 가능

* TOP5 부정 키워드

리포트 포함 내용

* 총 리뷰
* 평균 별점
* 감정 비율
* AI 요약
* 개선 제안

---

# 7. Git 협업 방식 결정 (5분)

### Repository

* GitHub Repository 생성 여부

### Branch 전략

예시

```text
main
develop

feature/import
feature/analyze
feature/dashboard
feature/cli
```

### Pull Request 사용 여부

* PR 후 Merge
* 직접 Merge

### Commit 규칙

예시

```text
feat:
fix:
docs:
refactor:
```

---

# 8. 라이브러리 통일

사용 라이브러리

* pandas
* matplotlib
* openpyxl
* requests 또는 OpenAI SDK
* sqlite3
* argparse

requirements.txt 관리 담당도 정한다.

---

# 9. 일정 계획

### Day 1

* 프로젝트 구조 생성
* 역할 분담
* 데이터 구조 확정

### Day 2~3

* 기능 개발

### Day 4

* 기능 연결

### Day 5

* 테스트

### Day 6

* 오류 수정
* README 작성

### Day 7

* 최종 발표 준비

---

# 10. 오늘 회의에서 반드시 결정해야 하는 항목 ✅

* [ ] 프로젝트 목표 공유
* [ ] 기존 Amazon 크롤러 데이터 확인
* [ ] 최종 데이터 컬럼 확정
* [ ] 저장 방식(SQLite / JSONL) 결정
* [ ] AI 결과(JSON 구조) 확정
* [ ] 팀원 역할 확정
* [ ] Git 브랜치 전략 결정
* [ ] 대시보드 차트 종류 확정
* [ ] 사용할 라이브러리 통일
* [ ] 개발 일정 확정

---

# 🎯 오늘 회의의 최종 산출물

회의가 끝났을 때 아래 5가지가 명확해야 한다.

1. **누가 무엇을 개발하는가?**
2. **어떤 데이터 형식을 사용할 것인가?**
3. **각 기능은 어떤 순서로 연결되는가?**
4. **GitHub에서 어떻게 협업할 것인가?**
5. **14일까지 어떤 일정으로 완성할 것인가?**

> 이 다섯 가지가 결정되면 바로 개발을 시작할 수 있다.
