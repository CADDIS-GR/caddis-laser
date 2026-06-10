# CADDIS 레이저 — 통합 관리 허브

> Bystronic ByCut Nova 3015 6kW 기반 레이저 절단 임가공 업무 자동화 시스템  
> 배포: [caddis-gr.github.io/caddis-laser](https://caddis-gr.github.io/caddis-laser/)

---

## 모듈 현황

| 모듈 | 파일 | 상태 | 설명 |
|------|------|------|------|
| 허브 메인 | `index.html` | ✅ 운영중 | 전체 모듈 진입 대시보드 |
| 외주관리 | `outsource.html` | ✅ 운영중 | 건명 등록 · 발주 추적 · 납품 현황 |
| 작업 현황판 | `workflow-board.html` | ⚙ Stage 1 | 칸반 보드 (Sheets 연동 예정) |
| 자재관리 | `materials.html` | 🔒 대기 | 장비 가동 후 활성화 |
| 견적 자동화 | `quote.html` | 🔒 대기 | `quote_dxf.py` 연동 후 활성화 |
| 리포트 | `report.html` | 🔒 대기 | GitHub Actions 연동 후 활성화 |

---

## 기술 스택

- **프론트엔드**: Vanilla HTML/CSS/JS · GitHub Pages 정적 배포
- **데이터**: Google Sheets (백엔드) · Apps Script (읽기/쓰기)
- **자동화**: GitHub Actions (리포트 · 알림 — 예정)
- **AI**: Claude Vision API (거래명세서 OCR · DXF 견적)
- **DXF 파싱**: Python `ezdxf`

---

## 외주관리 주요 기능 (`outsource.html`)

- 건명 등록 · 자동 채번 (`JOB-YYYY-NNN`)
- 발주 추적 · PO 자동 발행 (`PO-YYYYMM-NNN`)
- D-Day 자동 계산 · 상태 배지
- Google Drive 파일 링크 관리 (폴더 · DXF · 거래명세표)
- 거래명세서 OCR → 납품금액 자동 추출 (Claude Vision)
- CSV 내보내기

## 작업 현황판 주요 기능 (`workflow-board.html`)

- 대기 → 진행 → 완료 → 납품 4단계 플로우
- 표 / 보드(칸반) / 타임라인 3가지 뷰
- 납기 임박 D-Day 표시
- 작업지시서 파일 링크 연동
- 다크 · 라이트 테마 전환

---

## 번호 체계

```
건명번호  JOB-YYYY-NNN    예) JOB-2026-008
발주번호  PO-YYYYMM-NNN   예) PO-202606-003
업체코드  V00N             예) V005
입고번호  IN-YYYYMM###    예) IN-202606001
```

---

## 로드맵

- [ ] `workflow-board.html` Google Sheets 연동 (Stage 2)
- [ ] `quote_dxf.py` DXF 자동 견적 모듈 구현
- [ ] `quote.html` 견적 웹앱
- [ ] `materials.html` 자재관리 (장비 가동 후)
- [ ] `report.html` 주·월간 자동 리포트
- [ ] GitHub Actions 안전재고 알림 이메일

---

## 장비 정보

| 항목 | 내용 |
|------|------|
| 장비 | Bystronic ByCut Nova 3015 |
| 출력 | 6kW Fiber |
| 작업 크기 | 3,000 × 1,500 mm |
| 제어 S/W | BySoft Cell Control Cut |
| 네트워크 | 192.168.100.x |

---

*CADDIS 레이저 · 2026*
