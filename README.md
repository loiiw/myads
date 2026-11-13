# 猫眼 Loon 去广告插件

根据仓库提供的手机 HAR 抓包制作。当前版本只处理抓包中能明确识别的猫眼商城广告资源：

- 对 `store.maoyan.com/mmall/api/ads/api/position/detail` 返回空 JSON（`reject-dict`）。
- 拦截 `p0.pipi.cn/mediaplus/maoyantong_ads_fe/` 下的广告图片素材（`reject-img`）。

插件不拦截猫眼电影、演出、景点图片，也不处理埋点、风控或登录请求。HAR 只覆盖一次手机会话，因此其他页面和开屏广告尚未验证；若要补齐，请再提供对应页面的抓包。

## 安装

在 Loon 的插件页面添加：

`https://raw.githubusercontent.com/loiiw/myads/main/maoyan.plugin`

启用后需在 Loon 中允许 HTTPS 解密，并信任 Loon 证书，插件声明的 MITM 主机才会生效。

## 来源

- Loon 官方插件和 Rewrite 文档：https://nsloon.app/docs/Plugin/ 和 https://nsloon.app/en/docs/Rewrite/
- 猫眼请求依据：仓库提供的 HAR 文件（主机、接口路径和素材路径）
