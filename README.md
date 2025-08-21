# Mihomo (Clash Meta) 配置文件

这是一个针对 Mihomo (Clash Meta) 定制的高效配置文件，支持多种应用场景的智能分流方案。

## 特点

- 启用 TUN 模式，实现系统级透明代理
- 完善的 DNS 配置，针对国内外网站分别使用不同 DNS 服务器
- 完善的 DNS 防泄露
- 智能分流规则，包含常用应用与服务（OpenAI、Claude、Grok、Binance等）
- 节点自动测速与选择，提供最佳网络体验
- 内置图标支持，美化 UI 界面
- 域名嗅探功能，提高域名解析准确性

### 图标支持

配置包含丰富的图标资源，位于 `icons` 目录下：

- **地区图标**：HK, US, JP, SG, TW 等国家/地区图标
- **应用图标**：OpenAI, Claude, Grok, Binance, OKX, Netflix, TikTok 等
- **服务图标**：Manual(手动选择), Auto(自动选择), ISP(家宽) 等功能图标

图标在配置文件中通过以下方式引用（已自动同步Gitee进行国内加速）：

```yaml
proxy-groups:
  - {name: 默认, <<: *a2, icon: https://gitee.com/hoofei/clash/raw/main/icons/Manual.png }
  - {name: OpenAI, type: select, proxies: [家宽], icon: https://gitee.com/hoofei/clash/raw/main/icons/OpenAI.png }
```

### 核心功能

- **TUN 模式**：实现系统级全局代理，无需为每个应用单独设置
- **DNS 分流**：针对国内外网站使用不同 DNS 服务器，加速访问
- **智能分流**：预设多种应用场景的分流规则，无需手动调整
- **节点自动测速**：自动选择延迟最低的节点，提供最佳体验

## 使用方法

1. 下载 Mihomo (Clash Meta) 客户端
2. 将 `config.yaml` 文件放入 Mihomo 配置目录
3. 将 `icons` 目录中的图标文件复制到相应位置，或者将图标托管到个人网站上并修改配置中的图标URL
4. 重启 Mihomo 客户端，加载配置

## 节点订阅

配置中的节点订阅地址需要替换为您自己的订阅链接：

```yaml
proxy-providers:
  Subscribe:
    <<: *a1
    url: $suburl # 替换为您的订阅地址
    path: ./proxy_providers/SelfHost.yaml
```

## 自定义

如需自定义配置，可以修改以下部分：

- 代理端口：修改 `mixed-port` 等端口配置
- DNS 服务器：修改 `dns` 部分的 `nameserver` 和 `fallback`
- 分流规则：修改 `rules` 部分，调整规则顺序和目标代理组
- 图标引用：修改 `proxy-groups` 中的 `icon` 链接地址

## 其他

- 部分规则可能需要根据个人使用习惯调整
- 如果自托管图标，请确保图标服务器可以正常访问
