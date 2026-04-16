# 스킬 이름을 log, recall, digest로 확정한다

## 맥락

세 스킬의 초기 이름은 record, context, curate였다. 스킬 이름은 행위를 나타내는 동사여야 하는데, context는 명사여서 concept처럼 보였다. curate는 현대적 용법에서 "좋은 것을 골라주는" 뉘앙스가 강해 정렬/정리/평가의 역할과 거리가 있었다.

## 결정

스킬 이름을 다음과 같이 확정한다.

- **log**: 맥락을 document로 기록한다. record보다 가볍고 행위에 집중한다
- **recall**: 조건에 맞는 document를 찾아 현재 맥락에 로드한다. 과거 기록을 현재로 되살리는 행위
- **digest**: 로드된 document를 종합, 정제, 평가하여 산출한다. 여러 문서를 소화하여 의미를 추출하는 행위

### 제약 조건

- 스킬 이름은 동사여야 한다: 스킬은 행위이지 개념이 아니다
- loom의 기존 스킬 이름(shape, plan, task, review, calibrate)과 충돌하지 않아야 한다

### 전제 조건

- 세 스킬의 역할이 decision-0003에서 확정되었다: 이름만 변경하고 역할은 유지한다

## 대안

### record, context, curate 유지

- 설명: 초기 이름을 그대로 사용한다
- 트레이드오프: context가 명사, curate의 뉘앙스가 역할과 불일치

### brief (recall 대신)

- 설명: 브리핑한다는 뉘앙스로 상황 파악 요약을 제공
- 트레이드오프: 요약 제공의 뉘앙스가 있어, 맥락 로드보다 산출에 가까워 digest와 경계가 모호해짐

### distill (digest 대신)

- 설명: 증류한다는 뉘앙스로 핵심을 뽑아냄
- 트레이드오프: 정제에 집중하여, 평가/종합의 역할을 충분히 담지 못함

## 영향

- [[document]] - document의 생명주기가 log -> recall -> digest로 표현된다
