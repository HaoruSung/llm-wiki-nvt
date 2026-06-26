# Graybox Model
#stage/dft #status/verified
- **一句話定義**: 只保留 wrapped core 的 external-mode 邏輯（wrapper chains + 需一起測的部分 IJTAG）的精簡模型，加速上一層測試時的設計載入。

## 說明
- 移除 wrapped core 的內部邏輯，只留「產生 parent physical block 的 internal-mode ATPG patterns」所需的最小邏輯。
- 測上一個 physical level 時，用 graybox 比載入 full-chip 設計快很多。
- 可有分開的 input/output wrapper chains 與各自的 scan enable；但不強制分開（可用單一 scan enable + 其他機制控制 wrapper chains）。

## 相關
- [[concept/wrapped-cores-and-wrapper-cells]]、[[concept/internal-external-mode]]、[[concept/hierarchical-dft]]、[[concept/design-data-models]]

## 出處
- [[source/2026-06-25-tessent-shell-user-manual]]（Ch.4, Fig 4-5）
