# set_context
#vendor/siemens #status/verified
- **所屬工具**: [[tool/siemens-tessent-shell]]
- **語法**: `set_context <context> [sub-context ...] [-license <feature>]`

## 用途
設定 Tessent Shell 的 context（任務類別）。是 invoke 之後、能下大多數命令之前的**必要步驟**；**只能在 setup mode** 使用。設定 context 時，工具會自動取得對應 license（若可用）。

## 重要選項
| 選項 | 說明 | 預設 | 版本備註 |
|---|---|---|---|
| `<context>` | 任務大類，如 `dft`、`patterns` | 無 | 2021.3 |
| sub-context | 如 `-scan`、`-edt`、`-logic_bist`、`-test_points`、`-rtl` | 無 | 2021.3 |
| `-license <feature>` | 直接指定要取得的 license feature | 自動 | 2021.3 |

## 範例
```tcl
SETUP> set_context dft -scan
SETUP> set_context dft -rtl
SETUP> get_context        ;# 查看目前 context
```

## 注意事項 / 陷阱
- 設定 context **前**只能執行一小組 setup 命令（通常放在 startup file）。
- 在非 setup mode 呼叫會失敗。
- 完整選項見 Tessent Shell Reference Manual。

## 相關
- [[concept/tessent-contexts-and-system-modes]]、[[procedure/invoke-tessent-shell-and-set-context]]

## 出處
- [[source/2026-06-25-tessent-shell-user-manual]]
