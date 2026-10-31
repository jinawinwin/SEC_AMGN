# Amgen (NASDAQ: AMGN) — SEC Financial Dashboard

<p align="center"><a href="https://jinawinwin.github.io/SEC_AMGN/"><b>🔗 대시보드 바로가기</b></a></p>

SEC EDGAR의 Amgen Inc. (CIK 0000318154) 10-K 및 10-Q XBRL 자료를 바탕으로 2010년 이후 재무 데이터를 수집하고 연간·반기·분기별 성과와 재무비율을 분석합니다. 본 저장소는 **단일 기업 분석**이며 peer 기업 비교는 포함하지 않습니다.

**대시보드:** https://jinawinwin.github.io/SEC_AMGN/

마지막 데이터 갱신: <!-- UPDATED:START -->2026-10-31 (latest 10-K/10-Q on file: 2026-08-05)<!-- UPDATED:END -->

## 대시보드 구성
- 상단: Revenue, Operating income, Net income, Free cash flow, 최근 분기 매출 KPI
- Figures: 매출·수익성·현금흐름·재무구조·R&D/Revenue·CapEx/Revenue 시각화
- 하단: 연간 / 반기 / 분기 재무자료와 재무비율 테이블
- PDF 내보내기 및 기간 선택형 Excel 내보내기
- 월별 자동 수집 및 GitHub Pages 배포

## 데이터 및 방법
- 회사: Amgen Inc. (NASDAQ: AMGN), CIK 0000318154
- 회계연도: 매년 12월 31일 종료
- 데이터 출처: SEC EDGAR XBRL companyfacts 및 submissions API
- 범위: 2010년 이후 10-K 및 10-Q 자료
- 금액 단위: USD millions (EPS는 USD); 비율은 %
- FCF = 영업현금흐름 − 유형자산 취득(PP&E). 회사 발표 FCF와 리스·분류 차이로 다를 수 있습니다.
- 재작성된 기간은 최신 SEC XBRL 공시 값이 반영될 수 있습니다. 이 자료는 투자 자문이 아닙니다.

## 자동 업데이트
`.github/workflows/update.yml`은 **매월 1일 00:00 UTC (한국시간 09:00)** 에 테스트, SEC 자료 수집, CSV 및 대시보드 데이터 갱신, GitHub Pages 배포를 수행합니다. Actions 탭에서 수동 실행도 가능합니다.

## Repository Secret
`Settings → Secrets and variables → Actions → Secrets`에 다음 Repository Secret이 필요합니다.
- 이름: `SEC_USER_AGENT`
- 값 형식: `SEC_AMGN Dashboard contact@실제이메일주소`

연락 가능한 이메일을 포함해야 합니다. Secret 값은 공개 저장소의 코드에 저장하지 않습니다.

## 주요 파일
- `scripts/fetch_sec.py`: SEC 데이터 수집 및 대시보드 데이터 생성
- `scripts/sec_pipeline.py`: 기간 집계 및 재무비율 계산
- `tests/test_pipeline.py`: 기간 계산 로직 테스트
- `data/annual.csv`, `data/half_year.csv`, `data/quarterly.csv`: 처리된 테이블
- `data/raw/amgn_selected_facts.json`, `data/raw/amgn_filings.json`: 원천 데이터의 선택 집합
- `docs/data/dashboard.json`: 대시보드가 읽는 데이터
