# DMIT 出口集成（zhostev）

Pages 连的是这个仓库。出站不要写进 Git，只放 Cloudflare 变量。

## Pages 生产环境变量

| Name | Value |
|---|---|
| `ADMIN` | 你的后台密码 |
| `UUID` | `3be0e28f-fbd0-41c4-935b-48cfac7cf724` |
| `GO2SOCKS5` | `*` |
| `DMIT_SOCKS` | `socks5://edtnY7b95:密码@45.59.186.107:10808` |

KV 绑定名必须是 `KV`。改变量后重新部署。

密码见 VPS `/root/socks5-edt.txt`，不要 commit。

## `_worker.js` 补丁

主程序里去掉公共 proxyip 域名兜底；若设了 `DMIT_SOCKS`，全局走该 SOCKS，白名单为 `*`。

`反代参数获取`：默认反代若是 `socks5://...`，直接当成全局链式代理。

部署后打开 `/admin`，用 `cdn-cgi/trace` 确认出口 IP 是 `45.59.186.107` 或 `2605:52c0:3:6a7:be24:11ff:fea2:929a`。
