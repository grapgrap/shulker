# 세 개의 스킬(log, recall, digest)로 운용한다

## 맥락

shulker의 스킬 구성을 검토하면서 CODE(Capture/Organize/Distill/Express) 기법을 참조했다. 초기에는 daily/weekly를 문서 유형으로 간주했으나, 이들은 문서가 아닌 스킬(동작)임이 확인되었다. daily는 현재 활성 문서의 맥락을 로드하는 렌즈이고, weekly는 세션 간 패턴을 발굴하는 분석이다.

CODE의 네 단계와 사용자의 실제 사용 시점을 대조한 결과, Express는 기록 행위 자체에 포함되고 Organize는 사후 정제에 포함되어 별도 스킬이 불필요했다. 모든 사용 시점이 recall -> digest 파이프라인을 따른다.

## 결정

세 개의 스킬로 shulker를 운용한다.

- **log**: 맥락을 document로 기록한다
- **recall**: 조건(시간, 사람, 주제)에 맞는 document를 검색하고 맥락을 로드한다. 우선순위 파악을 지원한다
- **digest**: 로드된 document를 목적에 맞게 종합, 정제, 평가, 산출한다. 문서 간 관계 정리와 패턴 발견을 포함한다

### 제약 조건

- 사용자의 모든 사용 시점이 recall -> digest 파이프라인을 따른다: 두 스킬의 분리가 사용 패턴에 부합한다

### 전제 조건

- log가 Express를 흡수한다: 기록 행위 자체가 문서로의 표현이므로 별도 Express 스킬이 불필요하다
- digest가 Organize와 Distill을 흡수한다: 분류, 정제, 패턴 발견이 동일한 맥락에서 수행된다

## 대안

### CODE 4단계를 그대로 4개 스킬로

- 설명: Capture, Organize, Distill, Express를 각각 스킬로 구현한다
- 트레이드오프: Organize와 Distill의 경계가 실제 사용에서 모호하고, Express가 독립 스킬로 존재할 이유가 없다

### daily/weekly를 별도 스킬로

- 설명: 일간/주간 리듬에 맞춘 전용 스킬을 둔다
- 트레이드오프: daily의 본질은 recall(맥락 로드)이고 weekly의 본질은 digest(패턴 발견)이므로, 이름만 다른 중복이 된다

## 영향

- [[document]] - document의 생명주기가 log(생성) -> recall(검색) -> digest(종합)로 정의된다
