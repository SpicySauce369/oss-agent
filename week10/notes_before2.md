# notes_before2.md - week09/tools.py 분석

## 개요
`tools.py`는 KOBIS(영화진흥위원회) 오픈 API로 박스오피스 정보를 가져오는 도구 모음이다.
`requests`로 API를 호출하고, API 키는 `secret.py`의 `API_KEY`에서 가져온다.

## 모듈 수준 변수
| 이름 | 설명 |
|---|---|
| `BASE_URL` | 일별 박스오피스 API 주소 (`.../boxoffice/searchDailyBoxOfficeList.json`) |

## 함수 목록

### `get_boxoffice_rank_1(date)`
- **역할**: 해당 날짜의 박스오피스 1위 영화 제목을 알려준다.
- **입력**: `date` (문자열) - 8자리 날짜. 예: `"20260824"`
- **출력**: (문자열) 1위 영화 제목. 예: `"오디세이"`
- **동작**
  1. `{"key": API_KEY, "targetDt": date}` 로 파라미터를 만든다.
  2. `requests.get(BASE_URL, params=params, timeout=10)` 으로 API를 호출한다.
  3. 응답 JSON의 `boxOfficeResult.dailyBoxOfficeList` 목록을 꺼낸다.
  4. 첫 번째 항목(1위)의 `movieNm` 을 반환한다.

## 참고 / 잠재적 문제
- `BASE_URL`이 `{ ... }` 중괄호로 감싸져 있어 문자열이 아니라 **set**이다. 이대로 `requests.get`에 넘기면 오류가 날 가능성이 높다. 중괄호를 없애야 한다.
- 에러 처리가 없다 (HTTP 오류, 날짜 형식 오류, 빈 결과 등).
- 함수는 현재 1개뿐이다.
