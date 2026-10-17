## 🚀 lunes host 自动登录续期（GitHub Actions）

这是一个基于 GitHub Actions 的自动化脚本，用于定时登录自动续期[lunes host](https://betadash.lunes.host/) 应用。

⚠️ 有cf盾,太垃圾的机房节点可能过不了，建议用稍微干净点的节点 

━━━━━━━━━━━━━━━━━━━━━━

🔐 Secrets 配置说明(单账号保活，通知改为飞书推送)

| Secret 名称         | 是否必填 | 说明                                              |
|---------------------|----------|---------------------------------------------------|
| LUNES_EMAIL         | ✅ 必填  | lunes 登录邮箱                                     |
| LUNES_PASSWORD      | ✅ 必填  | lunes 登录密码                                    | 
| FEISHU_WEBHOOK_URL  | ❌ 可选  | 飞书自定义机器人 Webhook 地址（用于发送通知）        |
| FEISHU_SECRET       | ❌ 可选  | 飞书机器人签名密钥（机器人未开启签名校验则不填）      |
| NODE_LINK           | ❌ 可选  | 代理链接，如 vless:// vmess:// tuic:// hysteria2:// anttls:// socks5://|

━━━━━━━━━━━━━━━━━━━━━━

### 飞书通知配置方法

1. 在飞书群聊中添加「自定义机器人」（群设置 → 群机器人 → 添加机器人 → 自定义机器人）
2. 复制机器人 Webhook 地址（形如 `https://open.feishu.cn/open-apis/bot/v2/hook/xxxxxxxx`），配置到 Secret `FEISHU_WEBHOOK_URL`
3. 若机器人安全设置勾选了「签名校验」，将签名密钥配置到 Secret `FEISHU_SECRET`；未开启则留空

### 代理格式（确认在v2rayN里使用正常的节点）

`NODE_LINK` 支持以下任意一种代理协议的完整分享链接（不配置则直连）：

- **VLESS**：`vless://uuid@server:port?security=reality&sni=...&type=ws&...`
- **VMess**：`vmess://base64encoded...`
- **Trojan**：`trojan://password@server:port?sni=...&type=ws&...`
- **tuic**：`tuic://uuid:password@server:port...`
- **anytls**：`anytls://uuid@server:port...`
- **hysteria2**：`hysteria2://base64@server:port...`
- **SOCKS5**：`socks5://user:pass@server:port` 或 `socks://user:pass@server:port`

### 注意事项
- 尽量添加一个干净的节点，以免过不了cf盾
