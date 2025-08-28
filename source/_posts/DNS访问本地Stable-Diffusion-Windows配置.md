---
title: 外部访问本地Stable Diffusion

date: 2025-08-28 22:57:19
cover: https://admin.esports.gg/wp-content/uploads/2025/02/Castorices-kit-leaks-make-her-OP-in-Honkai-Star-Rail-968x544.jpg
keywords: Stable Diffusion Cloudflared NAT_Traversal Windows
---
本文基于Windows实现。使用前提：已安装Stable Diffusion webui,且已有自己的域名（放在了cloudflared上）。利用cloudflared内网穿透，将本地的7860端口开放到指定网址（比如sd.你的域名）

### 下载cloudflared内网穿透
``` powershell
winget install --id Cloudflare.cloudflared
cloudflared tunnel login
#选择域名后生成一个Certification-file(JSON)
cloudflared tunnel create sdtunnel
cloudflared tunnel route dns sdtunnel foreverxiaoyu.xyz

@"
tunnel: sd-tunnel
credentials-file: C:\Users\<User-name>\.cloudflared\<Certification-file>.json

ingress:
  - hostname: <target-website>
    service: http://localhost:7860
  - service: http_status:404
"@ | Set-Content -Path "C:\Users\<User-name>\.cloudflared\config.yml" -Encoding UTF8

cloudflared tunnel run sdtunnel

```
#### 打开网站测试即可



