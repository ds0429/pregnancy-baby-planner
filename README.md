# Pregnancy & Baby Planner

한국어 개인용 임신·출산 관리 PWA입니다. 사용자 데이터는 IndexedDB에 저장하고 localStorage 호환 백업을 함께 유지하며 외부 서버로 전송하지 않습니다. 조리원 검색용 외부 API 키는 필요하지 않으며, 사용자가 지도/검색 결과를 확인한 뒤 정보를 직접 입력합니다.

## 실행

- Node.js 20 이상 권장
- `npm install`
- `npm run dev`
- 배포 빌드: `npm run build`, 미리보기: `npm run preview`

## 데이터 구조

`pregnancyProfile` 성격의 임신 정보(profile), 주차별 체크리스트(checklist), 신청 항목(applications), 산후조리원(centers), 지출 기록(expenses)을 IndexedDB `pregnancy-baby-planner` 데이터베이스의 `appData` 스토어에 단일 버전 키 `pregnancy-baby-planner-v1`로 저장합니다. 각 레코드는 고유 ID를 가집니다. 조리원별 비용을 중복 없이 지출 예정 항목과 연결할 수 있으며, 전체 JSON 내보내기/복원과 CSV 지출 내보내기를 제공합니다.

## 로컬 테스트

개발 서버를 실행해 대시보드, 항목 추가/수정/삭제, 체크 상태 변경, 조리원 등록/비교, 지출 유형별 합계, CSV 및 JSON 가져오기/내보내기를 확인하세요. 브라우저 개발자 도구의 Application > Service Workers에서 서비스 워커 등록 상태를 확인할 수 있습니다. PWA 오프라인 동작은 최초 온라인 접속 후 확인합니다.

## iPhone Safari 홈 화면 추가

1. 앱을 HTTPS로 제공하고 iPhone Safari에서 엽니다.
2. 공유 버튼을 누르고 **홈 화면에 추가**를 선택합니다.
3. 추가 후 홈 화면 아이콘으로 열어 독립 실행과 오프라인 캐시를 확인합니다.

브라우저 데이터 삭제/기기 변경에 대비해 설정 버튼의 JSON 내보내기로 정기 백업하세요. 지원 정책, 자격 및 의료 일정은 공식기관과 담당 의료진의 최신 안내를 확인하세요.

## GitHub Pages 배포

이 저장소의 `main` 브랜치에 push하면 GitHub Actions가 빌드하고 Pages로 배포합니다. GitHub 저장소 Settings > Pages > Build and deployment에서 Source를 **GitHub Actions**로 선택하세요. 배포 사이트는 인터넷에서 공개 접근 가능한 URL이 됩니다. 앱 데이터는 각 기기의 IndexedDB에 저장됩니다.
