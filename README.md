# 남선초 감정체크

남선초등학교 학생용 감정 체크 앱. 학생들이 등교/하교 시 자신의 감정, 목표, 대인관계, 활동 참여를 기록합니다. Google Sheet를 백엔드로 사용하며, 학생 명단과 응답 데이터를 모두 시트에서 관리합니다.

## 파일 구성

- `emotion_check_3.html` — 메인 앱 (등교·하교 체크)
- `special-mission.html` — 5회 체크마다 열리는 특별 미션
- `index.html` — 메인 앱으로 리디렉션
- `dashboard.gs` — Google Apps Script (시트 백엔드 + 관리 Dashboard)
- `images/`, `assets/` — 여우 캐릭터 이미지

## 초기 설정 (최초 1회)

### 1. Google Sheet 준비

이미 준비된 시트: [남선초 감정체크 시트](https://docs.google.com/spreadsheets/d/1wk3WHhfNhjfxh1UEOxdp-aA22549TrPU6xsvyrWn11Y/edit)

### 2. Apps Script 배포

1. 시트에서 `확장 프로그램 → Apps Script` 열기
2. `dashboard.gs` 전체 내용을 복사해서 붙여넣기
3. 저장(Ctrl+S)
4. `배포 → 새 배포 → 웹 앱` 선택
5. 액세스 권한: **모든 사용자**
6. 배포 후 나온 웹 앱 URL 복사

### 3. 앱에 GAS URL 연결

두 가지 방법:

**A) 코드에 직접:**
- `emotion_check_3.html`의 `DEFAULT_SCRIPT_URL = ''` 를 복사한 URL로 교체
- `special-mission.html`도 동일하게 교체
- GitHub Pages에 커밋 & 푸시

**B) 앱 실행 후:**
- 학생 기기에서 앱 열기 → 우측 상단 ⚙️ 버튼
- URL 붙여넣기 & 저장 (각 기기마다 개별 저장됨)

### 4. 학생 명단 초기화

1. Apps Script 에디터에서 `setupStudentSheet` 함수 실행
2. 시트에 `학생 관리` 탭 생성됨
3. A열에 학생 이름 추가 (예: 김민준, 이서연)
4. 자동으로 앱에 반영됨

### 5. Dashboard 셋업

1. `setupDashboard` 함수 실행
2. 시트에 `Dashboard` 탭 생성됨
3. B2 셀에서 학생 이름 선택 → 해당 학생의 모든 기록 표시

## 주요 기능

- **감정 휠**: 12가지 감정 중 선택 → 감정 정의 표시
- **한국어/영어 전환**: 우측 상단 🌐 버튼
- **매일 회전 질문**: 등교/하교 마지막 질문이 4가지 중 하나로 매일 바뀜
- **특별 미션**: 감정체크 5회 완료마다 열림
- **주간 요약**: AI가 학생 응답 패턴을 요약
- **관리자 패널**: ⚙️ → 관리자 패널에서 학생별 체크 횟수 조정 가능

## 용어 (FoxLC 원본과의 차이)

| 원본 (FoxLC) | 남선초 버전 |
|---|---|
| 연구원 | 선생님 |
| 연구소 활동 | 활동 / 수업 |
| 입실 / 퇴실 | 등교 / 하교 |
| SEL/AI/영어/미술/수리 연구소 | SEL/AI 활동 + 영어·수학·과학·사회·미술·음악·체육 수업 |
| 폭스 (센터) | 학교 |
| Fox LC 로고 | 남선초 로고 |
| 간식 신청 버튼 | 제거 |
