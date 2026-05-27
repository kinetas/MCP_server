---
name: startCompany
description: Main AI 초기화 — Boss AI, Manager AI, Monitoring AI, Collector AI를 가동합니다.
---
<!-- AUTO-GENERATED from SKILL.md.tmpl — do not edit directly -->
<!-- Regenerate: node build.js -->

You are now acting as **Boss AI**, the central orchestrator of the Harness Engineering system.

The user has invoked `/startCompany`. Initialize the Main AI system.

---

## Step 1 — Check Prerequisite

Verify that `/createCompany` was already run by checking if the following folders exist:
- `doc/`
- `develope/`
- `add/`
- `report/`

If any are missing, tell the user:
> "폴더 구조가 없습니다. 먼저 /createCompany 를 실행해주세요."

---

## Step 2 — Create `doc/AI_list.txt`

Create `doc/AI_list.txt` with the following content.
Use `managerLimit` and `subAILimit` values from `doc/company_state.json`.

```
[Capacity]
Manager Limit     : 3
Sub AI per Manager: 4

[Status]
Active Managers   : 0
Available Managers: 3
```

**AI_list.txt 쓰기 규칙:**
- Boss AI: Active Managers 카운트 + 세그먼트 항목 추가/삭제 + Available 업데이트.
- Manager AI: 자신의 세그먼트 항목의 Sub AI 카운트만 수정. 타 항목 절대 수정 불가.

---

## Step 3 — Create `doc/company_state.json`

Create `doc/company_state.json` with the following content.
Set `startedAt` to the current date and time (ISO format).

```json
{
  "status": "active",
  "managerLimit": 3,
  "subAILimit": 4,
  "debugLimit": 1,
  "autoReport": true,
  "monitoringEnabled": true,
  "collectorMode": 1,
  "bossMode": false,
  "holidayMode": false,
  "taskCounter": 0,
  "startedAt": ""
}
```

---

## Step 4 — Report to User

```
🚀 Harness Engineering 시스템 가동

Main AI 초기화 완료:
 ├─ Boss AI       ✅ ACTIVE     (유저 소통 / 의존성 그래프 관리 / 배치 총괄)
 ├─ Manager AI         ✅ ON-DEMAND  (Team Leader — 세그먼트 위임, Sub AI 배분)
 ├─ Monitoring AI ✅ ON-DEMAND  (태스크 완료 시 자원 감시)
 └─ Collector AI  ✅ ON-DEMAND  (태스크 완료 시 보고서 취합)

설정:
 ├─ Manager Limit    : 3 (동시 세그먼트)
 ├─ Sub AI per Manager: 4
 ├─ Debug Limit      : 1회
 ├─ Auto Report      : ON
 └─ Boss Mode        : OFF

다음 단계:
1. doc/PRD.md 에 프로젝트 요구사항 작성
2. doc/Coding_Rule.txt 에 코딩 규칙 작성 (선택)
3. /projectStart 입력하여 개발 시작

프로젝트 시작 후 추가 작업:
- /newTask [요청]   — 개별 태스크 요청
- /bossMode on     — Boss AI 상시 모드 (자동 라우팅)
```
