# get_attribute_value_list
#vendor/siemens #status/verified
- **所屬工具**: [[tool/siemens-tessent-shell]]
- **語法**: `get_attribute_value_list <object_spec> -name <attribute>`

## 用途
回傳指定物件的某屬性值。常與 introspection 指令（如 `get_pins`）串接：把回傳的 collection 傳進來查屬性。

## 範例
```tcl
get_attribute_value_list [get_pins ...] -name <attr>
```

## 注意事項
- 接受 collection 作為 object spec（會參照該 collection）。
- 屬性需已註冊；自訂屬性用 `register_attribute`。

## 相關
- [[concept/object-attributes]]、[[concept/design-introspection]]、[[concept/collections]]

## 出處
- [[source/2026-06-25-tessent-shell-user-manual]]（Ch.3, Table 3-3）
