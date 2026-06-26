# Object Attributes
#stage/dft #status/verified
- **一句話定義**: 與設計物件（library cell、pin、module…）關聯、存在 data model 裡的特性；部分預定義，也可自訂。

## 說明
用 attribute 提升對設計的可視性，可查詢與操作設計物件的特徵。屬性可註冊（自訂）、設值、查值、報表、重設。

## 屬性 introspection 指令（Table 3-3）
- 查：[[command/tessent-get_attribute_value_list]]、`get_attribute_list`、`get_attribute_option`、`report_attributes`、`get_name_list`、`get_single_name`
- 設 / 管理：`register_attribute`、`unregister_attribute`、`set_attribute_value`、`reset_attribute_value`、`set_attribute_options`

## 相關
- [[concept/design-introspection]]、[[concept/collections]]

## 出處
- [[source/2026-06-25-tessent-shell-user-manual]]（Ch.3）
