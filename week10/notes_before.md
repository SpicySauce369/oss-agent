# notes_before.md

week09/tools.py 분석 노트

## 개요
KOBIS(영화진흥위원회) 오픈 API로 박스오피스 정보를 가져오는 도구 모음.

- 사용 라이브러리: `requests`
- `secret.py`의 `API_KEY`를 import해서 사용
- `BASE_URL`: 일별 박스오피스 조회 API 주소 (`searchDailyBoxOfficeList.json`)

## 함수 목록

### `get_boxoffice_rank_1(date)`
| 항목 | 내용 |
|---|---|
| 역할 | 해당 날짜의 박스오피스 1위 영화 제목을 알려준다 |
| 입력 | `date` (str) - 8자리 날짜. 예: `"20260824"` |
| 반환 | (str) 1위 영화 제목. 예: `"오디세이"` |

동작 순서:
1. `key`(API_KEY)와 `targetDt`(date)를 파라미터로 구성
2. `requests.get`으로 KOBIS API 호출 (timeout 10초)
3. 응답 JSON의 `boxOfficeResult.dailyBoxOfficeList`에서 첫 번째 항목의 `movieNm` 반환

## 확인된 문제점 / 주의사항
- `BASE_URL`이 `{ ... }` 중괄호로 감싸져 있어 문자열이 아니라 **set**이다. `requests.get`에 넘기면 오류가 날 가능성이 높다. 중괄호를 제거해야 한다.
- HTTP 상태 코드/예외 처리가 없다 (`raise_for_status` 없음). 잘못된 날짜나 API 오류 시 `KeyError` 등이 발생할 수 있다.
- 해당 날짜에 데이터가 없으면 `movies[0]`에서 `IndexError`가 발생한다.
- `secret.py`는 저장소에 없을 수 있으므로 실행 전에 준비되어야 한다.
