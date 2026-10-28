# week09 - 박스오피스 1위 조회

## 무엇을 하는 코드인가
날짜(8자리, 예: `20260824`)를 주면 KOBIS(영화진흥위원회) 오픈 API로 그 날의 일별 박스오피스 1위 영화 제목을 알려줍니다. 함수는 `tools.py`의 `get_boxoffice_rank_1(date)`입니다.

## 설치
Python 3와 `requests` 등 필요한 패키지를 설치합니다.

```
pip install -r requirements.txt
```

KOBIS 오픈 API 키도 필요합니다. `week09` 폴더에 `secret.py`를 만들고 아래처럼 적습니다.

```python
API_KEY = "발급받은_키"
```

## 실행
`week09` 폴더에서 실행합니다.

```
python main.py
```

`main.py`는 `20260824`의 1위 영화 제목을 출력합니다. 다른 날짜를 보려면 `main.py`의 날짜를 바꾸세요.
