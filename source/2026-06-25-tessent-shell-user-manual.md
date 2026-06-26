# Tessent Shell User's Manual, v2021.3
#status/verified
- **Type**: tool guide
- **Vendor / 來源**: Siemens EDA
- **Tool & Version**: Tessent Shell 2021.3（Document Revision 23, Sep 2021）
- **PDK / 製程**: N/A（工具操作手冊，與製程無關）
- **Raw file**: [[raw/tshell_user.pdf]]
- **Ingested**: 2026-06-25
- ⚠️ **機密**：含 Siemens trade secrets，受 NDA，限內部使用（見 [[CLAUDE.md]] §11）

## 重點摘要
- Tessent Shell 是 Siemens Tessent DFT 工具套件的統一 **Tcl-based 命令殼層**；所有 DFT 工具都從這裡啟動與管理（不同任務需不同 license）。
- 透過 **context + system mode + design level** 三者，決定要做哪類 DFT 任務、處於哪個狀態、在哪個設計層級。
- 核心基礎設施：Shared Data Models、Attributes、Design Introspection、TSDB（Tessent Shell Database）、IJTAG（IEEE 1687）自動化。
- 涵蓋 DFT 任務：Instrument Insertion（EDT / OCC / LogicBIST / MemoryBIST / boundary scan）、Scan analysis & insertion、ATPG + fault simulation、Defect Diagnosis & yield analysis。
- 工作流分 **flat designs** 與 **hierarchical designs**；另有 automotive workflow、SSN（Streaming Scan Network）、Test Procedure File、Tessent Visualizer、Config Data Visualizer。
- 命令採統一 Tcl 命名（首字分類：`get_` / `set_` / `report_` / `add_`…），可寫 dofile 腳本。

## 章節涵蓋進度
- ✅ **Ch.1** Introduction、**Ch.2** Tool Invocation / Contexts / Modes / Data Models（2026-06-25）
- ✅ **Ch.3** Design Introspection and Editing（2026-06-25）
- ✅ **Ch.4** DFT Architecture Guidelines for Hierarchical Designs（2026-06-25）
- ⬜ **Ch.5** Tessent Shell Workflows（下一步）
- ⬜ Ch.6–13（Automotive、TSDB Data Flow、SSN、Examples、Test Procedure File、Visualizer…）

## 牽動的頁面
**Ch.1–2 ingest**
- 新建：[[tool/siemens-tessent-shell]]、[[concept/dft-design-for-test]]、[[concept/tessent-contexts-and-system-modes]]、[[concept/tsdb]]、[[command/tessent-set_context]]、[[procedure/invoke-tessent-shell-and-set-context]]、[[issue/tessent-tcl-dollar-sign-in-pathname]]

**Ch.3 ingest**
- 新建（concept）：[[concept/design-introspection]]、[[concept/collections]]、[[concept/object-attributes]]、[[concept/design-editing]]、[[concept/simulation-contexts]]、[[concept/design-data-models]]、[[concept/test-procedure-file]]
- 新建（command）：[[command/tessent-get_instances]]、[[command/tessent-get_attribute_value_list]]、[[command/tessent-read_verilog]]、[[command/tessent-create_flat_model]]
- 新建（issue）：[[issue/tessent-design-editing-unavailable-under-fastscan-scan-license]]
- 更新：[[tool/siemens-tessent-shell]]、[[concept/tessent-contexts-and-system-modes]]

**Ch.4 ingest**
- 新建（concept）：[[concept/hierarchical-dft]]、[[concept/wrapped-cores-and-wrapper-cells]]、[[concept/internal-external-mode]]、[[concept/on-chip-clock-controller]]、[[concept/graybox-model]]、[[concept/pattern-retargeting]]、[[concept/test-access-mechanism]]、[[concept/hierarchical-dft-planning]]、[[concept/edt]]
- 更新：[[concept/dft-design-for-test]]（加 hierarchical 方法論）、[[concept/tessent-contexts-and-system-modes]]（context 連到概念）、[[concept/design-data-models]]、[[tool/siemens-tessent-shell]]
- 無新指令 / issue（本章為方法論，命令 defer 至其他手冊）
