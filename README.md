# CLIProxy 插件商店源

为 CLIProxyAPI 分发符合插件商店安装格式的第三方插件。当前提供 Qoder 的 Linux amd64 单插件包。

## Qoder

| 项目 | 内容 |
| --- | --- |
| 插件 ID | `qoder` |
| 发布版本 | `0.8.68` |
| 平台 | Linux amd64 / x86_64 |
| 上游 | [mmqz/cpa-multi-plugins](https://github.com/mmqz/cpa-multi-plugins) |
| 认证能力 | 上游插件提供 Qoder CN / Intl 设备授权和 PAT 登录 |

包中的 `qoder.so` 从上游 v0.8.68 发布的 Linux amd64 合集 ZIP 提取，二进制没有修改。每个安装 ZIP 的根目录只包含 Qoder 动态库，同时保留 MIT LICENSE 和来源记录。

## 通过应用商店安装

在 CLIProxy 管理中心的「第三方插件源 / registry URL」中加入以下普通源，保存并刷新商店：

```text
https://raw.githubusercontent.com/KaverinX/cliproxy-plugin/main/registry.json
```

搜索 **Qoder**，确认来源仓库为 **KaverinX/cliproxy-plugin**，选择最新稳定版并安装。此来源使用 CLIProxy 原生 GitHub Release 安装协议，发布包遵循 `qoder_<version>_<goos>_<goarch>.zip` 命名，并附带 `checksums.txt`。

如果 CLIProxy 支持 schema v2 / direct 安装，也可改用下面的源。它固定下载地址、大小和 SHA-256，无需在安装时解析 GitHub 最新版本：

```text
https://raw.githubusercontent.com/KaverinX/cliproxy-plugin/main/registry-v2.json
```

两个地址任选其一即可。若仍保留上游 mmqz 商店源，商店可能显示两个 Qoder 条目；选择 **KaverinX/cliproxy-plugin** 这个来源。

安装后确认全局插件开关及 Qoder 开关均已启用，状态为已注册 / 生效，再通过插件登录入口选择账号地区并完成设备授权。若宿主提示需要重启，请重启 CLIProxy。

插件运行在已有 CLIProxy 服务进程内，不需要在个人电脑额外启动代理或监听端口。

## 校验与运行边界

- 下载合集包时验证了上游 GitHub Release 资产 SHA-256。
- 验证 Qoder 文件为 ELF 64-bit x86-64 共享库。
- 重新打包后验证动态库与原文件字节一致，ZIP 内只有一个动态库。
- 商店源经过 CLIProxy 官方 registry 解析器校验。
- 安装 ZIP 的 SHA-256 保存在 `checksums.txt` 和 schema v2 registry 中。
- 当前只提供 Linux amd64 产物；CLIProxy 服务端应使用支持原生插件的构建。
- 用户 CLIProxy 服务端的 ABI 兼容性、插件加载、OAuth 登录和模型调用仍需在该环境验证。

## 来源与许可证

此仓库用于分发上游插件及商店元数据。上游源代码、许可证和二进制来源见 [NOTICE.md](NOTICE.md) 与 [provenance](provenance/)。发布包包含原项目 MIT LICENSE。
