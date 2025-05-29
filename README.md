
# ⚾ SSG 랜더스 팬 커뮤니티 (2025.04)

> 팀 프로젝트 / 역할: 경기 일정, 날씨, 경기 요약, AI 한줄평 담당

---

## 📌 프로젝트 개요

SSG 랜더스를 위한 팬 커뮤니티 플랫폼으로, 경기 일정, 날씨, 경기 요약, AI 요약 등 다양한 기능을 제공합니다.
외부 사이트에서 데이터를 크롤링하고, 이를 사용자에게 보기 좋게 제공하며, 일부 정보는 OpenAI API를 통해 AI 한줄평으로 자동 요약됩니다.

---

## ✅ 담당 기능 정리

### 1️⃣ 경기 일정 크롤링 및 달력 표시
- `statiz.sporki.com`에서 SSG 경기일정 크롤링 (Jsoup)
-  SSG가 포함된 경기만 필터링
- `game_schedule` 테이블에 저장 후 FullCalendar에 표시
- 경기 결과가 존재하면 해당 날짜 클릭 시 상세 요약 페이지 이동

### 2️⃣ 경기장별 날씨 위젯
- 기상청 단기 실황 API(`getUltraSrtNcst`) 연동
- 당일 SSG 경기장 기준 날씨 요약 및 온도 표시
- 마커 UI + 경기장 이름 + 날씨 정보 연동
- `weather` 테이블 저장 구조: `stadium_id`, `game_date`, `weather_summary`, `temperature`, `fetched_at`

### 3️⃣ 네이버 스포츠 경기기록 크롤링 + AI 요약
- SSG 경기 기록을 네이버 스포츠에서 크롤링 (Jsoup)
- `etcRecords` 기준 경기 요약 정리
- OpenAI GPT API 호출로 **AI 한줄평 자동 생성**
- `review` 테이블에 경기 요약, 한줄평 저장

### 4️⃣ 선수별 AI 한줄평 생성 (데이터는 타 팀원이 수집)
- 직접 크롤링은 하지 않았으며, 수집된 선수 스탯 기반 요약 담당
- GPT API를 통해 시즌 기록을 한줄평으로 요약
- 각 선수 페이지에서 AI 요약 결과 노출

---

## 🛠 사용 기술 스택

| 항목       | 기술                        |
|------------|-----------------------------|
| Backend    | Spring Boot, Java           |
| Crawling   | Jsoup                       |
| AI API     | OpenAI GPT-4.5              |
| DB         | MySQL                       |
| API 연동   | 기상청 API, Statiz, Naver   |
| Frontend   | Thymeleaf, FullCalendar     |

---

## 📎 기타 정보

- 팀 프로젝트 중 실제 서비스 수준으로 구현한 실전 경험 기반
- 크롤링, 비동기 API 호출, 외부 데이터 가공 경험 확보
- 협업 및 역할 분담을 명확히 하여 효율적 개발 경험

