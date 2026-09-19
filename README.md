# 📝 React & FastAPI 기반 메모 서비스 프로젝트
 
React 기반 프론트엔드와 FastAPI 기반 백엔드를 구축하고 Vercel과 Render를 통해 배포를 완료했습니다.

---

## 🔗 주요 프로젝트 링크

* **프론트엔드 배포 주소:** [https://memo-frontend-ouq536q1c-jihwan4.vercel.app](https://memo-frontend-ouq536q1c-jihwan4.vercel.app)
* **백엔드 API 문서 (Swagger):** [https://memo-backend-2.onrender.com/docs](https://memo-backend-2.onrender.com/docs)


---

## 🛠 기술 스택 (Tech Stack)

* **Frontend:** React, HTML5, CSS3, JavaScript (ES6+)
* **Backend:** Python, FastAPI, REST API
* **Deployment & Hosting:** Vercel (Frontend), Render (Backend)
* **Tools:** Git, GitHub, Chrome DevTools

---

## 💡 개발 & 트러블슈팅 여정 (Troubleshooting Log)

개발 및 배포 진행 과정에서 발생했던 주요 문제와 해결 방안을 기록한 트러블슈팅 일지입니다.

### 1. JavaScript 호이스팅 및 Temporal Dead Zone (TDZ) 에러
* **문제:** `useEffect` 내부에서 비동기 함수 `i()`를 호출할 때 `Cannot access 'i' before initialization` 에러 발생.
* **원인:** `let` 키워드로 작성된 함수가 `useEffect`보다 아래에 정의되어 있어, 초기화 전 접근(TDZ) 문제 발생.
* **해결:** `useEffect` 내부에서 비동기 데이터 패칭 함수를 직접 선언하거나 호출 위치 상단으로 이동하여 해결.

### 2. Base URL 끝 슬래시(`/`) 중복으로 인한 404 Not Found
* **문제:** 백엔드 통신 중 `GET https://memo-backend-2.onrender.com//memos 404` 에러 발생.
* **원인:** 환경변수/Base URL 끝에 붙은 `/`와 Fetch 요청 시 붙인 `/memos`가 중복되어 `//memos`라는 잘못된 경로로 요청이 전달됨.
* **해결:** Chrome DevTools(Overrides)를 통해 인라인 테스트 후, API Base URL 변수의 끝 `/`를 제거하여 `https://memo-backend-2.onrender.com` 형태로 수정.

### 3. 응답 데이터 타입 미일치로 인한 `TypeError: e.map is not a function`
* **문제:** 화면 전체가 검은색/흰색으로 멈추며 `e.map is not a function` 예외 발생.
* **원인:** API 요청 실패(404) 시 서버에서 배열이 아닌 에러 객체/HTML이 반환되었고, 프론트엔드 State가 배열로 갱신되지 않아 `.map()` 함수 호출 시 런타임 에러 발생.
* **해결:** `fetch` 통신 시 `Array.isArray(data)` 검증 로직 및 `try-catch` 예외 처리를 추가하여 비정상 응답 시 빈 배열(`[]`)로 세팅되도록 방어 코드 작성.

---

## 👤 개발자 소개

* **이름:** 김지환
* **소속:** 종합상사 자금팀 / 디지털금융 MBA
* **관심 분야:** 업무 자동화, 블록체인
* **목표:** 사내 품의 내용 및 자금 흐름을 한눈에 파악할 수 있는 업무 자동화 프로그램 구축
* **이메일:** jake6051@gmail.com