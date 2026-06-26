# Wrapped Cores and Wrapper Cells
#stage/dft #status/verified
- **一句話定義**: 把 physical block「包覆」起來以隔離其內部邏輯，使其可透過 pattern retargeting 重用；包覆用的邊界 flop 即 wrapper cells。

## 說明
- 在 hierarchical DFT 中，必須 wrap physical block 才能透過 [[concept/pattern-retargeting]] 重用 → 稱 **wrapped cores**。目的：隔離 core 內部邏輯。
- **Shared wrapper cells**：利用 block 邊界既有的 functional flop（同時擔任原本 I/O flop 與「隔離 core」兩種責任）。
- **Dedicated wrapper cells**（選用）：加在 primary input/output、fan in/out 到大 logic cone 處，使該 logic cone 能在 core 的 internal test 時被測。
- shared + dedicated wrapper cells 組成 **wrapper chains**。

## 相關
- [[concept/hierarchical-dft]]、[[concept/internal-external-mode]]、[[concept/graybox-model]]、[[concept/pattern-retargeting]]

## 出處
- [[source/2026-06-25-tessent-shell-user-manual]]（Ch.4, Fig 4-1）
