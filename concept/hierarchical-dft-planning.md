# Hierarchical DFT Planning（top-down 規劃，bottom-up 實作）
#stage/dft #status/verified
- **一句話定義**: hierarchical DFT 雖從最低層 block 由下而上插入，但事前應由上而下（從 chip level）規劃，因為 chip 層的實作會影響 core 層。

## 要優化 / 權衡的目標
- 降低 pattern count（縮短 test time）
- 控制 scan volume（塞進 tester memory）
- 降低 chip pin 需求（塞進 tester pin allocation）
- 優先序權衡：test time、test quality、flow 相容性、設計時程

## 三個規劃面向
- **Clocking architecture**：clock 如何 balance（CTS / clock mesh）決定 OCC 型別（standard/parent/child）、以及 intest/extest 時 OCC 行為 → [[concept/on-chip-clock-controller]]。
- **Resource availability**：chip 可用 pin 限制 EDT channel pin 數；tester memory 決定是否切 pattern set 或平行測多核；是否需要 [[concept/test-access-mechanism]]。
- **Test scheduling**：哪些 wrapped cores 同時（平行）測，取決於 pattern 數、chip pin、tester 儲存限制等。

## 相關
- [[concept/hierarchical-dft]]、[[concept/pattern-retargeting]]、[[concept/internal-external-mode]]

## 出處
- [[source/2026-06-25-tessent-shell-user-manual]]（Ch.4, Top-Down Planning / DFT Implementation Strategy）
