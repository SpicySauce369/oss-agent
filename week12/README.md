# boxoffice — KOBIS 박스오피스 조회 스킬

## 하는 일
영화진흥위원회(KOBIS) 일별 박스오피스를 조회한다. 특정 날짜의 박스오피스 1위 영화나 그 영화의 관객 수를 물을 때 사용한다.

## 들어 있는 파일
- .claude/skills/boxoffice/SKILL.md
- .claude/skills/boxoffice/scripts/boxoffice.py
- .claude/skills/boxoffice/LICENSE

## 필요한 것
request 라이브러리가 필요하므로 설치된 폴더에서 가상화 후 install하기 바람.

## 설치
boxoffice 폴더를 영문으로 된 경로 내에 설치 후 claude code나 terminal에서 claude code 설치 후 /reload-skill로 
/boxoffice skill을 import 한다.

## 바깥으로 요청하는 곳
https://www.kobis.or.kr에서 date와 해당 날짜의 1위 영화와 관객수를 요청함.

## 키
이 저장소나 boxoffice.py에는 key를 저장하는 곳이 없으며,
secret.py를 생성해 API_KEY="KOBIS에서 생성한 API키 삽입" 바람.

## 권한
Bash command를 이행할 때 1~2번의 요청이 있으며
파일을 수정/삭제하는 지시문이나 코드는 코드 원문에는 없으니 관련 권한을 요청한다면 거절해야한다.

## 라이선스
MIT License, boxoffice 폴더 최상위에 LICENSE 파일명으로 위치함.
