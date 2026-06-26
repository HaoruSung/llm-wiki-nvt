# Index — CAD Team Wiki 目錄

> 所有頁面的 catalog。每條：`連結 — 一行摘要 — (選用 tag/metadata)`。
> 每次 ingest / 回填都要更新本檔。格式見 [[CLAUDE.md]] §9。

## Tools
- [[tool/siemens-tessent-shell]] — Siemens Tessent DFT 套件的統一 Tcl 命令殼層 · #vendor/siemens #stage/dft

## Concepts
- [[concept/dft-design-for-test]] — DFT：可測試性設計的總稱（scan/ATPG/BIST…）
- [[concept/tessent-contexts-and-system-modes]] — context / system mode / design level 如何界定任務
- [[concept/design-data-models]] — flat / hierarchical / ICL 三種記憶體設計模型
- [[concept/design-introspection]] — 用 Tcl 查詢設計物件，回傳 collection
- [[concept/collections]] — Tessent 對 Tcl 的擴充，一組設計物件（string handle `@N`）
- [[concept/object-attributes]] — 設計物件的屬性與其查詢/設定
- [[concept/design-editing]] — 讀入並修改 netlist（create/delete/modify）
- [[concept/simulation-contexts]] — 對 flat model 取 gate_pin 模擬值（shift/capture…）
- [[concept/tsdb]] — Tessent Shell Database，flow 資料的中央儲存 · #kind/infra
- [[concept/test-procedure-file]] — scan 操作時序的測試程序檔 · #kind/format #status/unverified

### Concepts — Hierarchical DFT（Ch.4）
- [[concept/hierarchical-dft]] — 階層式 DFT 方法論（divide-and-conquer）
- [[concept/wrapped-cores-and-wrapper-cells]] — 包覆 physical block 以隔離、可重用
- [[concept/internal-external-mode]] — intest / extest 兩種測試模式
- [[concept/on-chip-clock-controller]] — OCC，使 core patterns 自包含、可 retarget
- [[concept/graybox-model]] — 精簡 wrapped core 模型，加速上層載入
- [[concept/pattern-retargeting]] — core patterns 重用到 chip 層
- [[concept/test-access-mechanism]] — TAM，平行測多核的 scan data 通道
- [[concept/hierarchical-dft-planning]] — top-down 規劃、bottom-up 實作
- [[concept/edt]] — 測試壓縮（TestKompress）· #status/unverified

## Commands
- [[command/tessent-set_context]] — 設定 Tessent context（只能在 setup mode）
- [[command/tessent-read_verilog]] — 讀入 Verilog netlist 建 hierarchical model
- [[command/tessent-create_flat_model]] — 建立 flat design data model
- [[command/tessent-get_instances]] — 查詢 instance collection
- [[command/tessent-get_attribute_value_list]] — 查詢物件屬性值

## Procedures
- [[procedure/invoke-tessent-shell-and-set-context]] — 啟動 Tessent Shell 並進入正確 context 的步驟

## Issues
- [[issue/tessent-tcl-dollar-sign-in-pathname]] — pathname 含 `$` 被 Tcl 當變數替換的解法
- [[issue/tessent-design-editing-unavailable-under-fastscan-scan-license]] — design editing 指令在 FastScan/Scan license 下不可用

## Sources
- [[source/2026-06-25-tessent-shell-user-manual]] — Tessent Shell User's Manual, v2021.3（tool guide, Siemens, ⚠️NDA）· 已涵蓋 Ch.1–4
