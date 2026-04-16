# document 저장 경로를 ~/.claude/shulker/로 한다

## 맥락

plan에서는 저장소 내부에 `documents/` 디렉토리를 두는 구조를 제시했다. 그러나 shulker는 claude-code 플러그인이고, 사용자의 개인 맥락 데이터는 플러그인 소스코드와 성격이 다르다. 소스코드는 버전 관리 대상이지만 개인 문서는 아니다.

## 결정

document 저장 경로를 `~/.claude/shulker/`로 한다.

- 플러그인 소스코드(`.claude-plugin/`, `skills/`, `.loom/`)는 리포에 존재한다
- 사용자의 document는 `~/.claude/shulker/`에 플랫하게 저장된다
- 리포의 `documents/` 디렉토리는 사용하지 않는다

### 제약 조건

- 소스코드와 사용자 데이터의 관심사가 다르다: 소스는 버전 관리, 데이터는 개인 영속 저장
- `~/.claude/`는 claude-code의 사용자 설정 디렉토리다: 플러그인의 사용자 데이터가 위치하기에 자연스러운 경로

### 전제 조건

- 스킬이 `~/.claude/shulker/` 경로를 알고 있어야 한다: 각 스킬의 SKILL.md에서 이 경로를 document 저장소로 참조한다

## 대안

### 리포 내부 documents/ 디렉토리

- 설명: plan 원안대로 저장소 루트에 `documents/`를 둔다
- 트레이드오프: 개인 문서가 소스코드와 섞여 버전 관리 대상이 되거나, .gitignore로 제외해야 한다

## 영향

- [[document]] - document의 물리적 저장 위치가 `~/.claude/shulker/`로 확정된다
