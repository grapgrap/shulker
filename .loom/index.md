# Shulker

사용자의 개인 맥락을 세션을 넘어 축적하고 재사용하는 마크다운 기반 저장소.

## 컨셉 목록

- [[document]] -- shulker의 유일한 저장 단위. 마크다운 본문과 위키링크로 구성

## 관계

```
document --위키링크-- document
(사람, 날짜, 주제 모두 document)
```

- **document**가 중심이며 유일한 concept이다. 사람, 날짜, 주제 모두 document이고, 위키링크가 유일한 관계 표현 수단이다.
- 서드파티 연동(슬랙, 리니어, 노션 등)은 shulker의 범위 밖이며, 사용자의 MCP 설정이 담당한다.
- 세 개의 스킬(log, recall, digest)이 document의 생명주기를 운용한다.
