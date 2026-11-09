# scoop

Raisin55 的 Scoop bucket —— 按分类存放常用应用清单，所有 hash 基于官方最新版实算/官方校验和核对。

## 安装本 bucket

```powershell
scoop bucket add scoop https://github.com/Raisin55/scoop
```

## 目录分类

清单按功能分在 `bucket/` 的子目录里（Scoop 递归扫描，分类不影响安装）：

| 分类 | 目录 | 内容 |
|---|---|---|
| AI 工具 | `bucket/ai/` | magpie-ai |
| 游戏工具 | `bucket/game/` | Steam 挂卡、战地6 匹配区域锁定、UsbEAm 游戏下载助手/启动器 |
| 网络加速 | `bucket/network/` | Steamcommunity 302、UsbEAm Hosts Editor |
| 工具 | `bucket/tools/` | UsbEAm Download Manager |

## 应用列表

### AI 工具

| 包名 | 版本 | 架构 | 说明 |
|---|---|---|---|
| `magpie-ai` | 0.1.3403 | x64 + arm64 | Magpie —— 面向 AI 编码代理的统一模型/供应商/网关管理器（跟踪 yetone/magpie 最新发布） |

### 游戏工具

| 包名 | 版本 | 架构 | 说明 |
|---|---|---|---|
| `bf6-region-lock` | 1.2 | x64 | 战地6 匹配区域锁定工具 —— 锁定匹配区域降低延迟（羽翼城 Dogfight360） |
| `steam-card-farmer` | 2.0.6 | x64 + arm64 | Steam 挂卡助手 —— 自动挂机掉卡（羽翼城 Dogfight360） |
| `usbeam-game-downloader` | 261007 | x64 + arm64 | UsbEAm 游戏下载助手 —— 加速各大平台游戏下载（羽翼城 Dogfight360） |
| `usbeam-launcher` | 1.0.12 | x64 | UsbEAm Launcher —— 多平台游戏启动器/加速配置工具（羽翼城 Dogfight360） |

### 网络加速

| 包名 | 版本 | 架构 | 说明 |
|---|---|---|---|
| `steamcommunity302` | 15.0.9 | x64 + arm64 | Steam 社区/商店/创意工坊 反代加速工具（羽翼城 Dogfight360） |
| `usbeam-hosts-editor` | 5.0.1 | x64 | UsbEAm Hosts Editor —— 多平台 hosts 修改/反代加速工具（羽翼城 Dogfight360） |

### 工具

| 包名 | 版本 | 架构 | 说明 |
|---|---|---|---|
| `usbeam-download-manager` | 1.0.5 | x64 + arm64 | UsbEAm Download Manager —— 多线程下载管理器（羽翼城 Dogfight360） |

## 常用命令

```powershell
scoop search --bucket scoop          # 看本 bucket 有哪些应用
scoop info scoop/<app>               # 看清单详情
scoop install scoop/magpie-ai        # 安装
scoop update scoop/<app>             # 更新单个应用
scoop update *                       # 更新全部
scoop uninstall scoop/<app>          # 卸载
```

## 说明

- **分类目录**：Scoop 的 `search`/`info`/`install`/`manifest_path` 全部递归扫描 bucket 目录，所以子目录分类不影响任何命令，`scoop install scoop/magpie-ai` 照常工作。
- **magpie-ai**：跟踪 [yetone/magpie](https://github.com/yetone/magpie) 的**最新发布**（latest channel），不是 stable 通道；清单带 `checkver`（github）+ `autoupdate`（hash 取自 `$baseurl/SHA256SUMS`）。首次安装会写入 `data/settings.json` 关闭应用内自动更新（避免与 Scoop 更新冲突），数据目录持久化到 `persist/data`。
- 其余应用版权归 [羽翼城 Dogfight360](https://www.dogfight360.com/blog/) 所有，本 bucket 仅做 Scoop 打包分发，不改动原始二进制。
- 部分工具（Steamcommunity 302、UsbEAm Hosts Editor、战地6 区域锁定）需**管理员权限**改 hosts / 装证书 / 改防火墙，Scoop 只装文件与快捷方式，权限提升请自行以管理员身份启动。

## 添加新应用

1. 选好分类目录（`bucket/ai|game|network|tools/`，也可新建），复制 `templates/app.json` 到 `bucket/<分类>/<应用名>.json`
2. 填 `version` / `url` / `hash` / `bin`（hash 用 `Get-FileHash <文件> -Algorithm SHA256` 实算）
3. 校验：`scoop install scoop/<应用名>` → `scoop uninstall <应用名>`
4. 提交推送
