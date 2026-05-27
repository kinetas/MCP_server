---
name: collectorMode
description: Collector AI 실행 시점 설정 — 세그먼트 완료(1, 기본), 프로젝트 완료(2), 태스크 완료(3) 중 선택합니다.
---
<!-- AUTO-GENERATED from SKILL.md.tmpl — do not edit directly -->
<!-- Regenerate: node build.js -->

You are **Boss AI**. The user has invoked `/collectorMode [n]`.

Change when Collector AI is automatically triggered.

---

## Step 1 — Read Current State

Read `doc/company_state.json`

If `doc/company_state.json` does not exist, tell the user:
> "시스템이 초기화되지 않았습니다. 먼저 /startCompany 를 실행해주세요."

---

## Step 2 — Parse Argument

- `1` → Collector AI가 **세그먼트 완료 시** 실행 (기본값)
- `2` → Collector AI가 **프로젝트 전체 완료 시** 실행
- `3` → Collector AI가 **태스크 완료마다** 실행
- No argument → 현재 설정만 출력 후 종료

Invalid argument (not 1, 2, or 3) → tell the user:
> "올바른 값을 입력해주세요: 1(세그먼트), 2(프로젝트), 3(태스크)"

---

## Step 3 — Update State

Update `collectorMode` field in `doc/company_state.json` to the new value (1, 2, or 3).

---

## Step 4 — Report to User

```
📊 Collector AI 실행 시점 변경

이전: [이전 값] → 현재: [새 값]

모드 설명:
  1 (세그먼트) — Manager AI가 세그먼트 완료 시 1회 실행 [기본값]
  2 (프로젝트) — 프로젝트 전체 완료 시 Boss AI가 1회 실행
  3 (태스크)   — Sub AI 태스크 완료마다 실행
```
