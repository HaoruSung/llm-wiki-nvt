# Internal Mode / External Mode（intest / extest）
#stage/dft #status/verified
- **一句話定義**: hierarchical test 的兩種模式——internal mode 測 wrapped core 內部邏輯；external mode 測 wrapper chains 外部邏輯。

## 說明
- **Internal mode（intest）**：測 wrapped core 內部。chip 層的 OCC 與 EDT 壓縮邏輯**不作用**。可同時測幾個 core，受 chip pin、tester channel/memory、功耗等限制。
- **External mode（extest）**：測 wrapper chains 外部的邏輯。core 內部的 OCC/EDT **不作用**，core 外部的 OCC/EDT **作用**；通常用一個 EDT logic block 測 wrapper chains 外的邏輯。external mode 也涵蓋 core 內的 wrapper chains。

## 相關
- [[concept/wrapped-cores-and-wrapper-cells]]、[[concept/on-chip-clock-controller]]、[[concept/edt]]、[[concept/hierarchical-dft]]

## 出處
- [[source/2026-06-25-tessent-shell-user-manual]]（Ch.4, Fig 4-2/4-3）
