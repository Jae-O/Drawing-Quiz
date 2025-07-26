# Drawing-Quiz
멀티플레이어가 참여 가능한 드로잉퀴즈 (2022.11)

## 📌 프로젝트 개요

- **프로젝트명**: Drawing Quiz  
- **개발 환경**: Java + Socket Programming  
- **DB 환경**: MariaDB  
- **배포 테스트 환경**: 포트포워딩 + 실서버 접속  
- **참여 인원**: 4명  
- **진행 방식**: 팀별 역할 분담 및 통합 테스트

---
▶ 로그인 및 게임 대기 화면
<div align="center"> <img src="https://github.com/user-attachments/assets/0f46b7f2-fb3b-4fad-b380-2e8e3d520440" width="360" /> <img src="https://github.com/user-attachments/assets/683e6718-3bdb-4145-8f3b-71d3ec27caec" width="360" /> </div> <p align="center"><i>로그인 후 닉네임 입력 → 대기방에서 다른 사용자와 매칭 대기</i></p>
▶ 게임 화면
<div align="center"> <img src="https://github.com/user-attachments/assets/94978dc2-c66f-4cc1-ae49-b1ebb1a8faf0" width="360" /> <img src="https://github.com/user-attachments/assets/0057922f-383e-4c65-9aac-a1ddf0a9525c" width="360" /> </div> <p align="center"><i>그림 그리기와 정답 입력이 동시에 진행되는 실시간 게임 플레이 화면</i></p>

## 👨‍💻 담당 역할 (주재오)
| 역할 구분 | 세부 내용 |
|-----------|-----------|
| **데이터베이스 구축** | MariaDB를 사용하여 사용자 및 게임 기록 관리 |
| **DB 설계** | 회원가입, 로그인, 점수 기록, 문제 저장 테이블 구성 |
| **서버 연결** | Java 서버와 MariaDB 연동 (JDBC) |
| **포트 포워딩 설정** | 외부 클라이언트 접속을 위한 공유기 NAT 포트포워딩 구성 |

## 🗄️ 데이터베이스 설계 (MariaDB)

### ✅ 주요 테이블

- `users`  
  - 사용자 ID, 비밀번호, 닉네임, 누적 점수 등 저장  
- `quiz`  
  - 문제 ID, 정답 단어, 난이도 등  
- `score_history`  
  - 게임 결과 저장 (유저 ID, 점수, 일시)

### ✅ MariaDB 연동 구조

```plaintext
Client (Java)
   ↓
Java Server (Socket + JDBC)
   ↓
MariaDB (SQL)

🌐 포트 포워딩 구성
공유기 NAT 설정을 통해 외부 접속 가능한 서버 구축

포트 개방: 5000번 

외부 사용자는 공인IP:5000으로 서버 접속 가능

테스트: 로컬 클라이언트 + 외부 노트북 조합으로 테스트 완료

✅ 실 서버 테스트 중 여러 명이 동시에 접속하여 퀴즈 플레이 가능 확인

🧩 주요 기능 (전체 프로젝트)
실시간 다중 접속 퀴즈 게임

그림 그리기 UI 및 마우스 캡쳐 기능

클라이언트-서버 간 메시지 송수신

점수 기록 및 순위판 구현

🛠 기술 스택
항목	내용
언어	Java
통신	Socket (TCP)
DB	MariaDB
기타	포트 포워딩, JDBC, Swing UI
