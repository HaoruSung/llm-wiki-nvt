# Design Data Models（flat / hierarchical / ICL）
#stage/dft #status/verified
- **一句話定義**: Tessent Shell 用來儲存設計資料的記憶體模型；introspection 與 design editing 都作用在其上。

## 三種 data model
- **Hierarchical design data model**：用 [[command/tessent-read_verilog]] 等讀入 netlist 時建立；session 期間常駐記憶體，直到刪除 model 或 exit。
- **Flat design data model**：進入 analysis mode 時自動建立，或用 [[command/tessent-create_flat_model]] 明確建立。由相連的 gate（primitive module 的 instance）組成；`gate_pin` 物件以「gateID.pinIndex」唯一 ID 表示（0 = 輸出，1 = 第一輸入…）。
  - ⚠️ 此 ID **跨 netlist 版本 / 跨 invocation 不穩定**，勿 hard-code 進腳本。
  - 保留 flat model 中的 hierarchical pin：`set_attribute_options -preserve_boundary_in_flat_model`。
- **ICL data model**：IJTAG（IEEE 1687）的 instrument connectivity 表示（詳見 Tessent IJTAG 手冊，本 wiki 待補）。

## Automatic Design Mapping（待深掘）
- ICL / TCD post-synthesis update、port name matching、name mapping 控制——Ch.3 後段，後續再補。

## 相關
- [[concept/design-introspection]]、[[concept/design-editing]]、[[concept/simulation-contexts]]、[[concept/tessent-contexts-and-system-modes]]
- [[concept/graybox-model]] — 精簡的 wrapped core 模型，加速上層載入

## 出處
- [[source/2026-06-25-tessent-shell-user-manual]]（Ch.2–3）
