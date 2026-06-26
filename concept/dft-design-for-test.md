# DFT (Design-for-Test)
#stage/dft #status/verified
- **一句話定義**: 在晶片設計中加入可測試性硬體與流程，讓製造後能有效偵測缺陷。

## 說明
DFT 涵蓋 scan、ATPG、BIST（LogicBIST / MemoryBIST）、boundary scan、壓縮測試（EDT, embedded deterministic testing）、OCC（on-chip clock controller）、defect diagnosis 等。在 Siemens 流程中，這些任務統一由 Tessent 工具套件、經 [[tool/siemens-tessent-shell]] 執行。

## 實作方法論
- [[concept/hierarchical-dft]] — 大型 block-based 設計的階層式 DFT（divide-and-conquer）
  - 關鍵組成：[[concept/wrapped-cores-and-wrapper-cells]]、[[concept/internal-external-mode]]、[[concept/on-chip-clock-controller]]、[[concept/pattern-retargeting]]、[[concept/graybox-model]]、[[concept/test-access-mechanism]]
  - 規劃：[[concept/hierarchical-dft-planning]]
- [[concept/edt]] — 測試壓縮（降低 pattern 資料量）

## 相關工具
- [[tool/siemens-tessent-shell]]

## 相關概念
- [[concept/tessent-contexts-and-system-modes]]、[[concept/tsdb]]、[[concept/design-data-models]]

## 出處
- [[source/2026-06-25-tessent-shell-user-manual]]
