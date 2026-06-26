# Design Introspection
#stage/dft #status/verified
- **一句話定義**: 用 Tcl introspection 指令檢視 design data model 裡的設計物件（instance / pin / net / module / port…）；重運算留在工具後端，回傳 collection。

## 說明
- introspection 指令吃 **object specification**，回傳 [[concept/collections]]。
- **Object specification format**：可以是物件名、名稱的 Tcl list、或 collection；有唯一 ID 的物件（如 instance）可直接用 ID。
  - 例：`add_schematic_objects [get_instances u*] -display hierarchical_schematic`
- 所有對「使用者指定物件」操作的 Tessent 指令都接受 object spec。

## 主要指令（Table 3-2 / 3-3）
> granularity：僅常用/有選項者獨立成頁，其餘列為 bullet。
- 物件查詢：[[command/tessent-get_instances]]、`get_pins`、`get_nets`、`get_modules`、`get_ports`、`get_fanins`、`get_fanouts`、`get_gate_pins`、`get_current_design`、`get_design_level`、`get_common_parent_instance`
- 屬性查詢：[[command/tessent-get_attribute_value_list]]、`get_name_list`、`get_attribute_list`、`report_attributes`、`register_attribute`、`set_attribute_value`（詳見 [[concept/object-attributes]]）
- 進階：bundle object / complex signal 的 fanin/fanout 與 connectivity 追蹤

## 相關
- [[concept/collections]]、[[concept/object-attributes]]、[[concept/design-data-models]]、[[concept/design-editing]]、[[tool/siemens-tessent-shell]]

## 出處
- [[source/2026-06-25-tessent-shell-user-manual]]（Ch.3）
