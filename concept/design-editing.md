# Design Editing
#stage/dft #status/verified
- **一句話定義**: 讀入 RTL 或 gate-level netlist 後，用指令修改設計（module / instance / net / port / pin 的建立、修改、刪除）。

## 說明
- 支援 gate-level 與 RTL 編輯，含 VHDL / Verilog / SystemVerilog、多 logical library、parameterized module。
- 可互動或 Tcl 腳本化；與 [[concept/collections]] / [[concept/design-introspection]] 指令協作。
- ⚠️ **部分 license 不提供**（如 Tessent FastScan、Tessent Scan）→ [[issue/tessent-design-editing-unavailable-under-fastscan-scan-license]]
- ⚠️ 處理 non-unique design scope（同 module 多 instance、generate loop 內部）要特別小心。

## 主要指令（Table 3-6）
- 讀 netlist：[[command/tessent-read_verilog]]、`read_vhdl`、`set_logical_design_libraries`
- 建立：`create_instance`、`create_module`、`create_net`、`create_pin`、`create_port`、`create_connections`
- 刪除：`delete_instances`、`delete_nets`、`delete_pins`、`delete_ports`、`delete_connections`
- 修改：`copy_module`、`replace_instances`、`intercept_connection`

## 相關
- [[concept/design-introspection]]、[[concept/design-data-models]]、[[tool/siemens-tessent-shell]]

## 出處
- [[source/2026-06-25-tessent-shell-user-manual]]（Ch.3, Table 3-6/3-7）
