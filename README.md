# HUMAN ERROR CHALLENGE 설치 안내

## 먼저 알아둘 점
이 패키지는 GitHub Pages + Firebase Realtime Database용 교육장 프로토타입입니다.
교육생은 GitHub/Firebase 로그인이 필요 없습니다.
현재 database.rules.json은 설치를 쉽게 하기 위한 공개 읽기/쓰기 규칙입니다. 즉, 링크와 데이터 구조를 아는 사용자가 데이터를 수정할 가능성이 있어 실제 공개 서비스용 보안 수준은 아닙니다. 사내 단기 교육용으로 먼저 테스트한 뒤, 필요하면 Firebase Authentication 기반으로 강화하세요.

## 1. Firebase 만들기
1. https://console.firebase.google.com/ 접속 후 프로젝트 추가
2. 프로젝트 생성 후 왼쪽 Build > Realtime Database > Create Database
3. 위치 선택 후 데이터베이스 생성
4. Realtime Database > Rules에서 database.rules.json 내용을 붙여넣고 Publish
5. 프로젝트 설정(톱니바퀴) > 일반 > 내 앱 > Web(</>) 앱 추가
6. 표시되는 firebaseConfig 값을 복사
7. 이 폴더의 firebase-config.js에서 YOUR_... 값을 실제 값으로 교체
8. databaseURL은 Realtime Database 화면에 표시되는 URL과 정확히 같아야 함

## 2. GitHub Pages 올리기
1. https://github.com/ 로그인 후 New repository
2. 예: human-error-challenge 라는 Public 저장소 생성
3. index.html, firebase-config.js 파일을 저장소 최상위(root)에 업로드
4. Settings > Pages
5. Source: Deploy from a branch
6. Branch: main / (root) 선택 후 Save
7. 수 분 후 Pages 화면의 Visit site로 접속

## 3. 사용법
- 교수자와 교육생 모두 같은 URL 접속
- ROOM CODE를 동일하게 입력 (기본 화면 4821)
- 교육생: 게임 참가 > 이름 > 참가
- 교수자: 관리자 > ROOM CODE > 비밀번호 KHNP
- 교수자가 1단계 START를 누르면 참가자 기기가 자동 시작
- 각 단계 60초
- 3단계 결과에는 SCORE RANKING + ERROR RANKING 표시

## 4. 실제 수업 전 필수 테스트
스마트폰 2대 + PC 1대로 테스트하세요.
A/B 스마트폰에서 참가 -> PC 관리자에서 참가자 2명 확인 -> Stage 1 START -> 양쪽 동시 시작 확인 -> 60초 결과 저장 확인 -> Stage 2/3 반복 -> Stage 3 오답순위 -> 최종순위 확인.

## 주의
관리자 비밀번호 KHNP는 index.html에 포함된 클라이언트 UI 잠금이므로 강한 보안이 아닙니다. 현재 DB Rules도 공개형 프로토타입입니다. 외부에 장기간 공개하거나 중요한 데이터를 저장하지 마세요.
