# get_instances
#vendor/siemens #status/verified
- **所屬工具**: [[tool/siemens-tessent-shell]]
- **語法**: `get_instances [<object_spec>] [-hierarchical] [-of_modules <module>] [-of_type <type>] ...`

## 用途
回傳相對於 current design 的 instance [[concept/collections]]。是最常用的 design introspection 指令之一。

## 重要選項
| 選項 | 說明 | 版本備註 |
|---|---|---|
| `-hierarchical` | 跨層級搜尋 | 2021.3 |
| `-of_modules <m>` | 限定屬於某 module | 2021.3 |
| `-of_type <type>` | 限定物件型別（如 `cell`） | 2021.3 |

## 範例
```tcl
set var1 [get_instances u* -hierarchical -of_modules MOD1]
set instCollection [get_instances -of_type cell]
```

## 注意事項
- 回傳 collection（string handle `@N`），不是一般 Tcl list；取名稱用 `get_name_list`。
- 完整選項見 Tessent Shell Reference Manual。

## 相關
- [[concept/design-introspection]]、[[concept/collections]]

## 出處
- [[source/2026-06-25-tessent-shell-user-manual]]（Ch.3, Table 3-2）
