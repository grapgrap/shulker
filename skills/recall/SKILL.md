---
name: recall
description: 조건에 맞는 document를 검색하고 맥락을 로드한다.
---

# Recall

조건(시간, 사람, 주제)에 맞는 document를 ~/.claude/shulker/에서 검색하고, 그래프를 탐색하여 맥락을 구성한다.

## 흐름

### 1. 입력 파악

사용자의 발화에서 검색 축을 식별한다.

- **시간**: "이번 주", "지난 목요일", "4월 첫째 주" 등
- **사람**: "김철수", "박영희" 등
- **주제**: "auth-module", "온보딩" 등

축이 모호하면 무엇을 찾는지 물어본다.

### 2. 검색

시간 축이 있으면 시간 축을 먼저 쿼리한다.

#### 시간 축 쿼리

시간 범위를 날짜 목록으로 변환하고, 각 날짜 document의 neighbors를 탐색한다.

```bash
# 예: "이번 주" -> 2026-04-13 ~ 2026-04-17
aeira graph neighbors -s ~/.claude/shulker/ "2026-04-13"
aeira graph neighbors -s ~/.claude/shulker/ "2026-04-14"
# ... 각 날짜에 대해 반복
```

날짜 document가 존재하지 않으면 해당 날짜는 건너뛴다 (기록이 없는 날).

시간 축의 결과를 기점 집합으로 삼고, 나머지 축(사람, 주제)이 있으면 이 집합 내에서 필터링한다.

#### 비시간 축 쿼리

시간 축이 없으면 aeira search로 직접 검색한다.

```bash
aeira search -s ~/.claude/shulker/ "{사람 또는 주제}"
```

### 3. 그래프 탐색

검색 결과 document들을 기점으로 neighbors를 탐색한다.

- 기본 깊이: 3홉
- 문서 수 제약 없음
- 각 홉에서 발견된 document를 다음 홉의 탐색 기점에 추가한다

```bash
# 1홉
aeira graph neighbors -s ~/.claude/shulker/ "{기점 document}"
# 2홉 -- 1홉에서 발견된 document들에 대해
aeira graph neighbors -s ~/.claude/shulker/ "{1홉 결과 document}"
# 3홉 -- 2홉에서 발견된 document들에 대해
aeira graph neighbors -s ~/.claude/shulker/ "{2홉 결과 document}"
```

사용자가 더 넓은 탐색을 요청하면 홉을 늘린다.

### 4. 맥락 구성

탐색된 document들을 읽어 맥락을 구성한다.

- 기점에 가까운 document를 먼저 배치한다 (홉 순서)
- 사용자가 추가 탐색을 요청하면 범위를 확장한다

## 제약

- document 접근은 aeira search/graph를 통한다
- 검색 결과를 임의로 필터링하거나 요약하지 않는다 -- 원문을 그대로 맥락으로 제공한다
- 시간 축이 있으면 반드시 시간 축을 먼저 쿼리한다
