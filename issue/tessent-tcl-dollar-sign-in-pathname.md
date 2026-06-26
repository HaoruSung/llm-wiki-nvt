# pathname 含 $ 被 Tcl 當成變數替換
#vendor/siemens #status/verified
- **所屬工具**: [[tool/siemens-tessent-shell]]
- **症狀**: netlist pathname 含 `$`（如 `foo/pin$p7`）時，Tcl 把 `$p7` 當變數替換，導致路徑解析錯誤或報錯。

## 原因
Tessent Shell 是 Tcl 介面；`$` 觸發變數替換。

## 解法 / workaround
用大括號 `{ }` 包住 pathname，停用變數替換：
```tcl
report_gates {foo/pin$p7}
```

## 相關（同源的其他 Tcl / dofile 陷阱）
- **停止 dofile 執行**：用 native Tcl `error ""`（空字串避免輸出訊息）。
- **可選單引號 `' '` 已不支援**：改用無引號 / 雙引號 / 大括號，例如
  `set_design_sources -v MODB.v -v MODC.v`。
- **存取環境變數**：用 `$env(NAME)`。
- **內嵌雙引號**：用 `\"` 跳脫，例如 `puts "Hello \"World\""`。

## 出處
- [[source/2026-06-25-tessent-shell-user-manual]]（Table A-1 Common Dofile Issues and Solutions）
