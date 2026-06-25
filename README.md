# DiDi Loon AdBlock

Loon plugin for removing DiDi ads and noisy homepage cards.

## Subscribe

Enhanced plugin:

```text
https://raw.githubusercontent.com/Jason-lewis-526/loon/main/Loon/DiDi_remove_ads.lpx
```

Single-rule plugin:

```text
https://raw.githubusercontent.com/Jason-lewis-526/loon/main/Loon/DiDi_fast_widget_card_remove.lpx
```

## Notes

- The enhanced plugin is based on the public DiDi remove-ads plugin from `kelee.one`.
- It adds removal for `data.order_cards.widget_card`.
- It also adds missing MitM hostnames used by existing rewrite rules.

## Updating Rules

Capture current DiDi traffic with Loon MitM and follow:

```text
docs/capture-and-update.md
```
