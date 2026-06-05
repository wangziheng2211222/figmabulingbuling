# designfigma-builingbuiling site

基于 Vue / Vite 的 `designfigma-builingbuiling` skill 分发站。

## 本地预览

```bash
npm install
npm run dev -- --port 4173
```

访问 `http://127.0.0.1:4173/`。

## 安装协议

站点提供 `/.well-known/agent-skills/index.json`，因此部署后可以用：

```bash
npx skills add https://your-domain.com -g -y --agent codex --agent claude-code --skill designfigma-builingbuiling
```

安装内容来自 `public/.well-known/agent-skills/designfigma-builingbuiling/`。

页面里的安装命令会自动读取当前部署域名生成。例如本地是
`http://127.0.0.1:4173`，部署到 `https://example.com` 后会自动变成
`npx skills add https://example.com ...`。如果部署在子路径，需要设置 Vite
base，例如 `VITE_BASE_PATH=/my-site/` 并在 `vite.config.js` 中接入。
