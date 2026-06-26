# EDT (Embedded Deterministic Test)
#stage/dft #status/unverified
- **一句話定義**: Tessent 的測試壓縮技術；EDT logic block 內含壓縮邏輯，大幅降低 scan pattern 資料量與 test time。

## 說明（多處引用；詳述待 ingest 其他章節 / Tessent TestKompress 手冊）
- 對應 context：`dft -edt`（IP 產生/插入，TestKompress）、`dft -logic_bist -edt`（EDT/LBIST hybrid，LogicBIST）。
- hierarchical test 中，wrapped core 內可含一或多個 EDT logic block；[[concept/internal-external-mode|internal/external mode]] 各有不同的 EDT 配置。

## 相關
- [[concept/hierarchical-dft]]、[[concept/internal-external-mode]]、[[concept/dft-design-for-test]]、[[concept/tessent-contexts-and-system-modes]]

## 出處
- [[source/2026-06-25-tessent-shell-user-manual]]（Ch.1/2/4 引用）
