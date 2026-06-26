# Pattern Retargeting
#stage/dft #status/verified
- **一句話定義**: 保留 core 的 ATPG patterns，於 chip（parent）層重用而不需重新產生——把 core-level patterns retarget 到 chip level。

## 說明
- 流程：為所有 core 產 patterns → 把 core-level patterns retarget 到 chip level → 只為 top-level chip 邏輯產 patterns。
- 每個 core 的 instantiation 都帶其 ATPG patterns。亦稱 ATPG / scan pattern retargeting。
- 需要 core 內有 [[concept/on-chip-clock-controller]] 讓 patterns 自包含、可獨立於時脈波形被合併。
- 對應 context：`patterns -scan_retargeting`（見 [[concept/tessent-contexts-and-system-modes]]）。

## 相關
- [[concept/wrapped-cores-and-wrapper-cells]]、[[concept/on-chip-clock-controller]]、[[concept/hierarchical-dft]]

## 出處
- [[source/2026-06-25-tessent-shell-user-manual]]（Ch.4；詳見 Tessent Scan and ATPG User's Manual）
