# OpenAI 官方插件全量 · 国内直连镜像

OpenAI Codex 官方插件市场（[`openai/plugins`](https://github.com/openai/plugins)，共 **172** 个）的**完整原样镜像**，托管在国内可直连的 Git 站点上，方便 **Codex 桌面端**在大陆**无需翻墙**即可添加该市场并安装插件。

> 本仓库只做镜像与说明，**不翻译、不改动**任何插件内容，与官方逐一对应。
> 仅改了市场标题（避免与 Codex 内置的同名市场冲突）。详见 [NOTICE.md](./NOTICE.md)。

## 在 Codex 桌面端添加

编辑 `~/.codex/config.toml`（Windows：`C:\Users\<你>\.codex\config.toml`），新增一节：

```toml
[marketplaces.echobird-openai-cn]
source_type = "git"
source = "https://gitcode.com/<账号>/<仓库>.git"
```

然后**完全退出并重启 Codex 桌面端**，它会 clone 本市场并同步；之后在「插件 → 市场下拉 → 安装」中选择即可。

## 国内开箱即用的插件（推荐优先）

官方 172 个里大多数是需要 OpenAI 账号 + OAuth 的托管连接器，国内无账号用户用不了。下列约 **25 个**无需账号、纯本地、**国内可离线直接用**：

`build-web-apps` · `build-macos-apps` · `build-ios-apps` · `build-web-data-visualization` · `game-studio` · `superpowers` · `sentry` · `remotion` · `expo` · `render` · `temporal` · `circleci` · `coderabbit` · `codex-security` · `twilio-developer-kit` · `nvidia` · `openai-developers` · `zotero` · `hyperframes` · `magicpath` · `mixpanel-headless` · `plugin-eval` · `life-science-research` · `ngs-analysis` · `test-android-apps`
