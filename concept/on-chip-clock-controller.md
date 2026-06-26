# On-Chip Clock Controller (OCC)
#stage/dft #status/verified
- **一句話定義**: 插入每個 wrapped core 的本地、自包含時脈控制器，使該 core 的 ATPG patterns 自包含、可被 retarget 到 parent/chip 層。

## 說明
- 沒有 OCC，wrapped core 的 patterns 無法自包含，就無法 retarget。OCC 為某 clock waveform 初始化後，patterns 可獨立於時脈波形被 retarget 並與其他 block patterns 合併。
- 每個進入 core 的 clock domain 插一個 OCC；chip 層的 clock domain 也需要 OCC。
- **Standard OCC** 內建 clock selection、clock-chopping、clock-gating；另有 **parent / child OCC**。
- OCC 型別（standard/parent/child）取決於 clock 如何 balance（CTS / clock mesh）、以及 intest/extest 時的行為需求。

## 相關
- [[concept/internal-external-mode]]、[[concept/pattern-retargeting]]、[[concept/wrapped-cores-and-wrapper-cells]]、[[concept/hierarchical-dft-planning]]

## 出處
- [[source/2026-06-25-tessent-shell-user-manual]]（Ch.4, Fig 4-4；詳見 Tessent Scan and ATPG User's Manual）
