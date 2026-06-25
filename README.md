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
- It restores missing MitM hostnames used by existing rewrite rules.
- It makes several original rewrites more tolerant of optional query strings, omitted `:443`, and missing JSON fields.
- It fixes the original `pSFCHomePage` jq rule so `tab_list` is preserved before filtering.

## Updating Rules

Capture current DiDi traffic with Loon MitM and follow:

```text
docs/capture-and-update.md
```
