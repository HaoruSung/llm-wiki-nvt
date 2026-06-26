# Tessent Context / System Mode / Design Level
#stage/dft #status/verified
- **一句話定義**: Tessent Shell 用 context（任務類別）、system mode（工具狀態）、design level（設計層級）三者，界定當前要執行的 DFT 任務。

## 說明

### Context（功能類別，常對應某 point tool / license）
- `dft` — 設計編輯與 introspection（gate-level / RTL Verilog / SystemVerilog / VHDL）
- `dft -scan` — scan 分析與插入（Tessent Scan / ScanPro；含 X-bounding、test point 等）
- `dft -edt` — [[concept/edt|EDT]] IP 產生/插入（Tessent TestKompress 的 IP 建立階段）
- `dft -logic_bist -edt` — EDT/LBIST hybrid controller IP（Tessent LogicBIST）
- `dft -test_points` — test point 辨識與插入
- `patterns -scan` — ATPG + good/fault simulation（Tessent FastScan / TestKompress）
- `patterns -scan_diagnosis` — 失效診斷（Tessent Diagnosis）
- `patterns -scan_retargeting` → [[concept/pattern-retargeting]]；`patterns -ijtag` / `patterns -silicon_insight` / `patterns -failure_mapping` …

### System Mode（工具狀態）
- 啟動後預設為 **setup mode**（提示字元 `SETUP>`）。
- `set_context` **只能在 setup mode** 使用；設定後可進入 analysis 等模式。
- **analysis mode**（Ch.3 補充）：進入時自動建立 flat [[concept/design-data-models]]；是使用 [[concept/simulation-contexts]] 的前置條件。

### Design Level（設計層級）
- `dft` context **必設、無預設值**：chip / physical block / sub-block。
- flat 設計一律 chip level；hierarchical 設計需區分 top（chip）與 physical/sub-block（見 [[concept/hierarchical-dft]]）。

## 相關指令
- [[command/tessent-set_context]]（搭配 `get_context`、`set_design_level`、`set_system_mode`）

## 相關 procedure
- [[procedure/invoke-tessent-shell-and-set-context]]

## 出處
- [[source/2026-06-25-tessent-shell-user-manual]]
