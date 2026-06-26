# 啟動 Tessent Shell 並設定 context
#stage/dft #status/verified
- **目標**: 從零啟動 Tessent Shell，進入正確的 DFT 任務狀態。
- **前置需求**: Tessent 安裝與環境變數、對應 license、（dft context 需）設計檔
- **相關工具**: [[tool/siemens-tessent-shell]]

## 步驟
1. 啟動 Tessent Shell → 工具進入 **setup mode**（提示字元 `SETUP>`）。
2. （選用）在 startup file 放好「設定 context 前」可用的少數 setup 命令。
3. 設定 context，例如 `set_context dft -scan`（自動取得對應 license；或加 `-license` 指定）。
4. （`dft` context 必做）設定 design level：`set_design_level chip | physical_block | sub_block`。
5. 用 `get_context` 確認；之後即可使用該 context/mode 對應的命令集。

## 驗證方式 / 預期輸出
- `get_context` 回傳剛設定的 context。
- 可用命令與提示字元會隨 context / system mode 改變。

## 常見踩雷
- [[issue/tessent-tcl-dollar-sign-in-pathname]]
- `set_context` 在非 setup mode 會失敗。

## 出處
- [[source/2026-06-25-tessent-shell-user-manual]]
