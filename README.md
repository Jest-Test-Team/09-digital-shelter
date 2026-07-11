# Digital Shelter

**中文名稱：** 數位避難與最低可生存服務  
**建築學來源：** Refuge, Fire Compartment and Life Safety（避難與防火區劃）

## 核心問題

> 故障、攻擊或資源枯竭時，哪些最低服務必須保留，哪些功能應主動卸載？

## Problem statement

許多系統只有 full service 與 total outage，缺少安全的 degraded/read-only/emergency mode。

## Inputs

- critical user journeys
- dependency graph
- feature flags
- capacity limits
- DR plans
- incident scenarios


## Outputs

- Minimum Viable Service profile
- feature shedding order
- survival test results
- containment boundaries


## Primary metrics

| Metric ID | 初始用途 |
|---|---|
| `critical_journey_availability` | 建立 baseline、趨勢與 review trigger；正式公式見後續 metric registry。 |
| `degradation_time` | 建立 baseline、趨勢與 review trigger；正式公式見後續 metric registry。 |
| `dependency_survivability` | 建立 baseline、趨勢與 review trigger；正式公式見後續 metric registry。 |
| `containment_score` | 建立 baseline、趨勢與 review trigger；正式公式見後續 metric registry。 |
| `recovery_point_gap` | 建立 baseline、趨勢與 review trigger；正式公式見後續 metric registry。 |


## MVP scope

1. 定義 survival profile
2. 模擬依賴失效
3. 自動關閉非必要功能
4. 驗證核心旅程


## Out of scope for MVP

- 自動執行高風險變更
- 以單一分數取代專業審查
- 未經授權蒐集個人、員工、病患或客戶敏感資料
- 宣稱已建立普遍適用的因果關係

## Repository contract

- `project.yaml`：machine-readable project manifest
- `api/openapi.yaml`：最小 ingestion / assessment API
- `schemas/event.schema.json`：事件資料契約
- `docs/architecture.md`：邊界、資料流與 implementation slices
- `docs/threat-model.md`：安全、隱私與濫用風險
- `examples/sample-event.json`：合成資料範例

## First implementation milestone

先完成 **single-tenant, synthetic-data, read-only analysis**。在證據追溯、權限、資料保留與人工覆核尚未建立前，不進入真實組織或個人資料環境。
