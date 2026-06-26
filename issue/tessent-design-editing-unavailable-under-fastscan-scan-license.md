# design editing 指令在 FastScan / Scan license 下不可用
#vendor/siemens #status/verified
- **所屬工具**: [[tool/siemens-tessent-shell]]
- **症狀**: 執行 `create_instance`、`read_verilog`、`delete_*` 等 design editing 指令時不可用 / 報錯。

## 原因
部分 product license（如 Tessent FastScan、Tessent Scan）不提供 design editing 指令。

## 解法 / workaround
- 改用具備 design editing 的 context / license 來做 netlist 編輯。
- 確認 [[command/tessent-set_context]] 取得的 license feature 是否涵蓋 design editing。

## 相關
- [[concept/design-editing]]、[[concept/tessent-contexts-and-system-modes]]

## 出處
- [[source/2026-06-25-tessent-shell-user-manual]]（Ch.3, Design Editing 之 Note）
