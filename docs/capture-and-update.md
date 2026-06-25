# DiDi Loon Ad Capture And Update Plan

## Goal

Maintain a GitHub-hosted Loon plugin URL that removes current DiDi ads based on real captured traffic.

## Capture Checklist

1. Enable Loon MitM and install/trust the Loon CA certificate.
2. Add the current DiDi plugin and make sure MitM includes these hosts:

```text
conf.diditaxi.com.cn
res.xiaojukeji.com
common.diditaxi.com.cn
api.udache.com
ct.xiaojukeji.com
lion.didialift.com
as.xiaojukeji.com
poi.map.xiaojukeji.com
daijia.kuaidadi.com
htwkop.xiaojukeji.com
```

3. In Loon, open the HTTP capture/log view.
4. Fully quit DiDi, clear it from the app switcher, then reopen it.
5. Visit these pages in DiDi:

```text
Home page
My/Profile page
Coupons/Wallet page
Ride-hailing main page
Intercity page
Bike page
Designated driver page
Any page where an ad still appears
```

6. Export matching captured requests and responses for these host/path patterns:

```text
conf.diditaxi.com.cn/homepage/v1/core
conf.diditaxi.com.cn/homepage/v1/other/fast
conf.diditaxi.com.cn/homepage/v1/other/slow
conf.diditaxi.com.cn/dynamic/conf
res.xiaojukeji.com/resapi/activity/mget
common.diditaxi.com.cn/common/v5/usercenter/layout
api.udache.com/gulfstream/porsche/v1/dache_homepage_layout
api.udache.com/gulfstream/porsche/v1/pSFCHomePage
api.udache.com/intercity/ticket/api/v1/core/getFullPageInfoLayout
ct.xiaojukeji.com/agent/v3/feeds
poi.map.xiaojukeji.com/mapapi/recommend
daijia.kuaidadi.com/gateway
htwkop.xiaojukeji.com/gateway
as.xiaojukeji.com/ep/as/toggles
```

## What To Send Back

Send any of these formats:

```text
HAR export
Raw JSON response body
Loon request/response export text
Screenshots showing the ad and the matching request URL
```

Best case: one folder or zip containing response bodies before and after enabling the plugin.

## Update Workflow

1. Compare captured JSON fields against current rewrite rules.
2. Identify surviving ad fields, usually keys containing:

```text
ad
ads
banner
marketing
popup
dialog
promotion
feed
card
widget
member
activity
coupon
```

3. Prefer precise `response-body-json-del` paths for simple deletions.
4. Use `response-body-json-jq` when filtering arrays or keeping only allowed cards.
5. Add every HTTPS rewrite host to `[MitM]`.
6. Commit the updated `.lpx` to GitHub.
7. Use the GitHub Raw URL in Loon for ongoing updates.
