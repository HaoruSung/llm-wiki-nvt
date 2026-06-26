# Hierarchical DFT
#stage/dft #status/verified
- **一句話定義**: 用階層式設計方法，在 block 層級分別做 test insertion / generation / diagnosis，再整合到 chip 層級，而非整顆晶片從 chip level 一次做。

## 為什麼用（優點）
- divide-and-conquer，任務可平行化
- 降低 memory / CPU 需求
- pattern generation 與 simulation 更快
- DFT 提早在 block 層完成，移出設計關鍵路徑
- 適用 block-based 大型設計（從 chip level 一次做不切實際時）

## 術語（layout regions）
- **Physical block / block / core / child core**：可互換；chip 以下、可被實例化的 layout region；獨立 synthesis，到 tapeout 維持完整。
- **Chip**：top-level physical block（整個設計），含 pad I/O、clock controllers。
- **Parent block / parent level**：>2 層階層時，chip 與上層 block 稱 parent。
- ⚠️ **順序**：必須先對 lower-level 做 DFT，再做上一層（最後才 chip level）；各 region 可平行插入。

## 關鍵組成（各自獨立頁）
- [[concept/wrapped-cores-and-wrapper-cells]]、[[concept/internal-external-mode]]、[[concept/on-chip-clock-controller]]、[[concept/graybox-model]]、[[concept/pattern-retargeting]]、[[concept/test-access-mechanism]]
- 規劃：[[concept/hierarchical-dft-planning]]

## 相關
- [[concept/dft-design-for-test]]、[[concept/edt]]、[[tool/siemens-tessent-shell]]
- two-pass hierarchical insertion flow 詳見 Ch.5「Tessent Shell Flow for Hierarchical Designs」（待 ingest）

## 出處
- [[source/2026-06-25-tessent-shell-user-manual]]（Ch.4）
