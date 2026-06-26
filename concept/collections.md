# Collections
#stage/dft #status/verified
- **一句話定義**: Tessent Shell 對 Tcl 的擴充——代表一組（0 個或多個）設計物件；是 introspection 指令的回傳型別。

## 說明
- 原生 Tcl 指令（`foreach`、`puts`）**不認得** collection。
- 資料留在工具內部結構，Tcl 端只拿到 **string handle**：`@` + 數字 ID（如 `@1`），避免 Tcl 介面被大量資料拖累。
- 在 shell 直接下指令時，顯示前 50 個元素的 `name` 屬性；非互動模式（dofile）不顯示名稱。
- 用變數參照 collection；`unset` 變數、改值、或變數離開 scope 時，collection 會被刪除。

## 範例
```tcl
set var1 [get_instances u* -hierarchical -of_modules MOD1]
puts [get_name_list $var1]        ;# u1 u2 u3 ...
set instCollection [get_instances -of_type cell]
```

## 相關
- [[concept/design-introspection]]、[[command/tessent-get_instances]]、[[command/tessent-get_attribute_value_list]]

## 出處
- [[source/2026-06-25-tessent-shell-user-manual]]（Ch.3, Table 3-1）
