# Test Access Mechanism (TAM)
#stage/dft #status/verified
- **一句話定義**: 把 scan data 送進/送出 chip 的機制，讓多組 wrapped cores 能平行測試；chip pin 有限、需重用 pin 連到多個 core EDT 時必需。

## 說明
- TAM 為「要平行跑的每組 wrapped cores」載運 scan data 進出 chip。
- 在 top level 排程 wrapped cores 的測試，並開放 chip-level 存取以執行這些測試。
- 依賴 floorplan / placement：要考量平行測試的 core 之間的鄰近性、以及連到它們的 chip pin 位置，避免 routing congestion。

## 相關
- [[concept/internal-external-mode]]、[[concept/hierarchical-dft-planning]]、[[concept/hierarchical-dft]]

## 出處
- [[source/2026-06-25-tessent-shell-user-manual]]（Ch.4, Resource Availability）
