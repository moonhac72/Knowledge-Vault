---
date: 2026-04-26
time: 11:15
tags:
  - 공적
  - AI
  - 테크
  - IT시스템
  - 인문학
  - 철학
  - 독서
---
# 📋 Claude 텔레그램 좀비 프로세스 해결 — tmux + 자동재시작 구조 완성

## 문제

장시간 미사용 후 claude 프로세스가 좀비 상태 (살아있지만 무응답)가 되어 텔레그램 봇이 응답 안 함.

## 해결 구조

tmux 세션 "telegram"이 전체를 감싼다. 그 안에서 `claude-telegram.sh`가 실행되고, perl로 6시간 타이머를 걸어 claude 프로세스를 강제 재시작한다. while 루프가 재시작 후 3초 대기 뒤 자동 재실행한다.

- tmux — 맥미니가 켜진 한 세션 유지 (네트워크 끊겨도 살아있음)
- perl 타이머 — 6시간마다 강제 재시작 (좀비 상태 예방)
- while 루프 — 재시작 후 3초 대기 후 자동 재실행

## 평소 운영

아무것도 안 해도 됨. 텔레그램이 무응답일 때만 아래 명령으로 상태 확인:

```
tmux attach -t telegram
```

대부분은 자동 복구됨.

## 맥미니 재부팅 후 복구

```
tmux new-session -s telegram
~/claude-telegram.sh
```

실행 후 Ctrl+B → D 로 빠져나오면 끝.
