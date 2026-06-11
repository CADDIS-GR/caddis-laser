# CADDIS 레이저 — 통합 관리 허브

> ByCut Nova 3015 6kW 기반 레이저 절단 임가공 업무 자동화 프로젝트  
> **GitHub Pages**: https://caddis-gr.github.io/caddis-laser/

---

## 페이지 현황

| 페이지 | 파일 | 상태 | 설명 |
|--------|------|------|------|
| 허브 | `index.html` | ● LIVE | 전체 메뉴 허브 |
| 외주관리 | `outsource.html` | ● LIVE | 건명 등록 · 발주 추적 · 납품 현황 |
| 서비스 관리 | `service.html` | ● LIVE | 장비 고장 접수 · 조치 이력 · 패턴 분석 |
| 작업 현황판 | `workflow-board.html` | ⚙ Stage 1 | 칸반 보드 (Google Sheets 연동 예정) |
| 설치 준비 일지 | `install-log.html` | ● LIVE | D-Day 카운트다운 · 매일 구상·진행·점검 기록 |
| 자재관리 | — | 🔒 LOCKED | 장비 가동 후 활성화 |
| 견적 자동화 | — | ⚙ DEV | `quote_dxf.py` 연동 후 |
| 리포트 | — | 🔒 LOCKED | GitHub Actions 연동 후 |

---

## 서비스 관리 (`service.html`)

장비 고장·이상 발생 시 접수부터 조치 완료까지 이력을 관리합니다.

### 운영 흐름

```
① 문제 발생
   → 사진 촬영 → Drive SVC 폴더에 업로드

② 서비스 등록
   → service.html 우상단 [+ 서비스 등록]
   → SVC번호 자동 발행 (SVC-YYYY-NNN)
   → 증상분류 · 조치유형 · Drive 링크 입력

③ 바이스트로닉 포털 접수 (수동)
   → 포털 티켓번호 메모

④ 조치 완료
   → 리포트 · 청구서를 Drive에 업로드
   → 상세 수정 → 링크 연결 → 상태 "완료"

⑤ 패턴 분석 자동 반영
   → 증상 유형별 누적 바 차트 확인
```

### SVC번호 체계

```
SVC-YYYY-NNN    예) SVC-2026-001
```

### Drive 폴더 구조

```
📁 CADDIS_레이저_장비관리/
  └── 📁 서비스이력/
        └── 📁 SVC-YYYY-NNN_증상요약/
              ├── 📁 01_증상사진/
              ├── 📄 02_서비스리포트.pdf
              └── 🧾 03_청구서.pdf
```

**루트 폴더**: https://drive.google.com/drive/folders/1C2TPBsvYFI7qxwb3T5emlPCwPLNmLY-g  
**서비스이력 폴더**: https://drive.google.com/drive/folders/1vsnDCtCtb7_jWj4DzXyxiynvw3rW6G-3

### 데이터 저장

브라우저 `localStorage` 기반 (Google Sheets 연동은 2단계 예정)

---

## 설치 준비 일지 (`install-log.html`)

ByCut Nova 3015 장비 설치일(2026.06.23)까지 매일의 구상·진행·점검을 기록합니다.

### 주요 기능

- **D-Day 카운트다운** — 설치일까지 자동 계산, 진행률 바 표시
- **오늘 일지** — 구상/메모, 진행/완료 사항, 점검 체크리스트, 전체 상태 태그
- **체크리스트** — 설치 준비 항목 관리 (전기·접지·가스·바닥·네트워크 등)
- **일지 아카이브** — 날짜별 아코디언 목록으로 누적 보존

### 데이터 저장

브라우저 `localStorage` 기반 (설치 완료 후 업무일지로 전환 예정)

---

## 외주관리 (`outsource.html`)

장비 설치 전 임가공 운영 전용. Google Sheets 연동으로 실시간 데이터 관리.

### 건명번호 체계

```
JOB-YYYY-NNN    예) JOB-2026-006
```

### 발주번호 체계

```
PO-YYYYMM-NNN  예) PO-202606-001
```

### Drive 루트 폴더

https://drive.google.com/drive/folders/1gM-LJ32RAoxyLVje9O-umkyf58p-zHcD

---

## 자재관리 시스템 (장비 가동 후 활성화)

**파일**: `자재관리시스템_CADDIS레이저.xlsx`

- 자재Key = `재질-두께t-규격W×규격H` (예: `SS400-5t-1000×2000`)
- 7개 시트: 자재마스터 · 입고대장 · 재고현황 · 잔재대장 · 사용내역 · 스크랩대장 · 사용방법
- OCR 자동 입고: `inbound_ocr.py` (Claude Vision API)

---

## 기술 스택

| 구분 | 도구 |
|------|------|
| 프론트엔드 | Vanilla HTML/CSS/JS (GitHub Pages) |
| 데이터 저장 | localStorage → Google Sheets (2단계) |
| 파일 저장 | Google Drive |
| 스프레드시트 | openpyxl (Python) |
| DXF 파싱 | ezdxf |
| OCR | Claude Vision API |
| 정기 실행 | GitHub Actions |

---

## 업데이트 이력

| 버전 | 날짜 | 내용 |
|------|------|------|
| v1.2 | 2026-06-11 | 설치 준비 일지 추가 (`install-log.html`), 허브 D-Day 카운터 |
| v1.1 | 2026-06-11 | 서비스 관리 페이지 추가 (`service.html`) |
| v1.0 | 2026-06-07 | 외주관리 · 작업 현황판 · 허브 초기 구축 |

---

*관련 문서: `외주가공관리시스템_프로젝트요약.md` · `레이저절단_자동화시스템_요약.md`*
