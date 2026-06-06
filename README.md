# OpenAI 官方插件全量 · 国内线路镜像

OpenAI Codex 官方插件市场（[`openai/plugins`](https://github.com/openai/plugins)，共 **172** 个）的**完整原样镜像**，托管在腾讯 CNB（国内主线），方便 **Codex 桌面端**在大陆**无需翻墙**直连添加并安装插件。

> 本仓库只做镜像，**不翻译、不改动**任何插件内容；仅改了市场标题（避免与 Codex 内置同名）。详见 [NOTICE.md](./NOTICE.md)。
>
> EchoBird 提供两条线路，内容相同，任选其一：
> - **国内线路**（本仓，腾讯 CNB，主线）：`https://cnb.cool/echobird/codex-plugins.git`
> - **川渝线路**（备线，重庆节点）：`https://gitcode.com/edison7009/EchoBird.git`

## 在 Codex 桌面端添加（国内线路）

编辑 `~/.codex/config.toml`（Windows：`C:\Users\<你>\.codex\config.toml`），新增一节：

```toml
[marketplaces.echobird-cn]
source_type = "git"
source = "https://cnb.cool/echobird/codex-plugins.git"
```

然后**完全退出并重启 Codex 桌面端**，市场「**OpenAI 官方插件(国内线路)**」会出现并带全部 172 个插件。

## 国内开箱即用的插件（推荐优先）

官方 172 个里大多数是需要 OpenAI 账号 + OAuth 的托管连接器，国内无账号用户用不了。下列约 **25 个**无需账号、纯本地、**国内可离线直接用**：

`build-web-apps` · `build-macos-apps` · `build-ios-apps` · `build-web-data-visualization` · `game-studio` · `superpowers` · `sentry` · `remotion` · `expo` · `render` · `temporal` · `circleci` · `coderabbit` · `codex-security` · `twilio-developer-kit` · `nvidia` · `openai-developers` · `zotero` · `hyperframes` · `magicpath` · `mixpanel-headless` · `plugin-eval` · `life-science-research` · `ngs-analysis` · `test-android-apps`
