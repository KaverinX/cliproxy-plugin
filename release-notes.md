# Qoder 0.8.68 — Linux amd64

首个 CLIProxy 插件商店分发版本，来源为 mmqz/cpa-multi-plugins 上游 v0.8.68。

## 安装

将以下地址添加到 CLIProxy 插件商店的第三方插件源，然后选择 KaverinX/cliproxy-plugin 来源的 Qoder 安装：

https://raw.githubusercontent.com/KaverinX/cliproxy-plugin/main/registry.json

支持 schema v2 / direct 的宿主也可使用：

https://raw.githubusercontent.com/KaverinX/cliproxy-plugin/main/registry-v2.json

## 发布资产

- qoder_0.8.68_linux_amd64.zip：ZIP 根目录包含未修改的 qoder.so、原始 MIT LICENSE 和来源记录。
- checksums.txt：安装包 SHA-256。

上游合集包的 GitHub 资产摘要、ELF x86-64 类型、单插件 ZIP 结构及动态库字节一致性均已验证。此发布不代表已经在用户的 CLIProxy 服务端完成 OAuth 或模型调用验证。
