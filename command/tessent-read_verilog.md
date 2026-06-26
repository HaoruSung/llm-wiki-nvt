# read_verilog
#vendor/siemens #status/verified
- **所屬工具**: [[tool/siemens-tessent-shell]]
- **語法**: `read_verilog <files> ...`

## 用途
讀入 Verilog netlist，把設計轉成記憶體中的 hierarchical [[concept/design-data-models]]。是 design editing / DFT flow 載入設計的起點之一。

## 注意事項
- 對應有 `read_vhdl`；多 logical library 用 `set_logical_design_libraries`。
- 屬 design editing 指令；部分 license（FastScan / Scan）不提供 → [[issue/tessent-design-editing-unavailable-under-fastscan-scan-license]]
- 設計資料常駐記憶體至 delete model 或 exit。

## 相關
- [[concept/design-editing]]、[[concept/design-data-models]]

## 出處
- [[source/2026-06-25-tessent-shell-user-manual]]（Ch.2–3）
