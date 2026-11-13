# 猫眼 Loon 去广告插件

根据仓库提供的手机 HAR 抓包及公开的猫眼广告域名规则制作。当前版本处理：

- 拒绝 `ad.maoyan.com` 的请求，用于拦截开屏广告服务请求。原 HAR 未覆盖启动阶段，因此这条规则需要在你的设备上验证。
- 对 `store.maoyan.com/mmall/api/ads/api/position/detail` 返回空 JSON（`reject-dict`）。
- 拦截 `p0.pipi.cn/mediaplus/maoyantong_ads_fe/` 下的广告图片素材（`reject-img`）。

插件不拦截猫眼电影、演出、景点图片，也不处理埋点、风控或登录请求。若开屏广告仍出现，请重新抓取从强制退出猫眼到启动广告显示/消失这一段流量，提供新 HAR 以确认实际广告接口。

## 安装

在 Loon 的插件页面添加：

`https://raw.githubusercontent.com/loiiw/myads/main/maoyan.plugin`

启用插件。广告域名规则无需 MITM；商城接口和素材规则需在 Loon 中允许 HTTPS 解密，并信任 Loon 证书。

## 来源

- Loon 官方插件和 Rewrite 文档：https://nsloon.app/docs/Plugin/ 和 https://nsloon.app/en/docs/Rewrite/
- 猫眼商城请求：仓库提供的 HAR 文件（主机、接口路径和素材路径）
- 开屏广告域名：公开 Loon 广告规则中对 `ad.maoyan.com` 的拦截项
