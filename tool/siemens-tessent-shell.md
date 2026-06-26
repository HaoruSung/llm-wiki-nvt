# Tessent Shell
#vendor/siemens #stage/dft #status/verified
- **Vendor**: Siemens EDA（前 Mentor Graphics）
- **Category**: DFT（Design-for-Test）統一命令殼層
- **Latest known version**: 2021.3（本 wiki 已知，見出處）
- **License feature**: 依 context 自動取得對應 license（Tessent Scan / FastScan / TestKompress / LogicBIST / Diagnosis…）；可用 `set_context -license` 指定
- **所屬 flow 階段**: [[concept/dft-design-for-test]]

## 用途 / 在 flow 中的角色
Tessent 工具套件的統一進入點。以 Tcl 殼層整合所有 DFT 任務：instrument insertion（EDT、OCC、LogicBIST、MemoryBIST、boundary scan）、scan insertion、ATPG、fault simulation、defect diagnosis。支援 flat 與 hierarchical 設計流程，並提供 netlist 編輯能力。

## 核心概念
- [[concept/tessent-contexts-and-system-modes]] — 用 context / mode / design level 決定任務
- [[concept/design-data-models]] — flat / hierarchical / ICL 三種記憶體設計模型
- [[concept/design-introspection]] — 用 Tcl 查詢設計物件，回傳 [[concept/collections]]
- [[concept/object-attributes]] — 設計物件的屬性與查詢
- [[concept/design-editing]] — 讀入並修改 netlist
- [[concept/simulation-contexts]] — 對 flat model 取 gate_pin 模擬值
- [[concept/tsdb]] — Tessent Shell Database，flow 資料的中央儲存
- [[concept/hierarchical-dft]] — block-based 設計的階層式 DFT 方法論（含 wrapped cores、OCC、retargeting…）
- IJTAG（IEEE 1687）自動化（預設透過 IJTAG network 控制所插入的 DFT instruments）

## 常用 commands
- [[command/tessent-set_context]] — 設定 context（必須在 setup mode）
- [[command/tessent-read_verilog]] — 讀入 netlist 建立 hierarchical model
- [[command/tessent-create_flat_model]] — 建立 flat model
- [[command/tessent-get_instances]] — 查詢 instance collection
- [[command/tessent-get_attribute_value_list]] — 查詢物件屬性值

## 相關 procedure
- [[procedure/invoke-tessent-shell-and-set-context]]

## 常見問題 / 排錯
- [[issue/tessent-tcl-dollar-sign-in-pathname]]

## 出處
- [[source/2026-06-25-tessent-shell-user-manual]]
