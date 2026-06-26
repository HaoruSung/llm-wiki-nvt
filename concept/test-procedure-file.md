# Test Procedure File
#stage/dft #kind/format #status/unverified
- **一句話定義**: 描述 scan 操作時序（setup / shift / capture / load_unload 等 procedure）的測試程序檔；模擬與 ATPG 會讀入它。
- **分類備註**: artifact（檔案格式）候選；暫歸 `concept/` + `#kind/format`（見 [[CLAUDE.md]] §2）。

## 說明（Ch.3 僅引用，詳見 Ch.10，待 ingest）
- [[concept/simulation-contexts]] 需要讀入 test procedure file，其 setup / shift / capture / load_unload procedure 的值會套用到設計後再設模擬 context。

## 相關
- [[concept/simulation-contexts]]

## 出處
- [[source/2026-06-25-tessent-shell-user-manual]]（Ch.3 引用；Ch.10「Test Procedure File」詳述，待 ingest）
