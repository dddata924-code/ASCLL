# scoop

Raisin55 / Raisin55 的 Scoop bucket —— 羽翼城（Dogfight360）软件合集，全部清单基于官方最新版实算 SHA256。

## 安装本 bucket

```powershell
scoop bucket add scoop https://github.com/Raisin55/scoop
```

## 安装应用

```powershell
scoop install scoop/steamcommunity302
scoop install scoop/usbeam-hosts-editor
```

## 应用列表

| 包名 | 版本 | 架构 | 说明 |
|---|---|---|---|
| `bf6-region-lock` | 1.2 | x64 | 战地6 匹配区域锁定工具 —— 锁定匹配区域降低延迟（羽翼城 Dogfight360） |
| `steam-card-farmer` | 2.0.6 | x64 + arm64 | Steam 挂卡助手 —— 自动挂机掉卡（羽翼城 Dogfight360） |
| `steamcommunity302` | 15.0.9 | x64 + arm64 | Steam 社区/商店/创意工坊 反代加速工具（羽翼城 Dogfight360） |
| `usbeam-download-manager` | 1.0.5 | x64 + arm64 | UsbEAm Download Manager —— 多线程下载管理器（羽翼城 Dogfight360） |
| `usbeam-game-downloader` | 261007 | x64 + arm64 | UsbEAm 游戏下载助手 —— 加速各大平台游戏下载（羽翼城 Dogfight360） |
| `usbeam-hosts-editor` | 5.0.1 | x64 | UsbEAm Hosts Editor —— 多平台 hosts 修改/反代加速工具（羽翼城 Dogfight360） |
| `usbeam-launcher` | 1.0.12 | x64 | UsbEAm Launcher —— 多平台游戏启动器/加速配置工具（羽翼城 Dogfight360） |

## 常用命令

```powershell
scoop search --bucket scoop          # 看本 bucket 有哪些应用
scoop info scoop/<app>               # 看清单详情
scoop update scoop/<app>             # 更新单个应用
scoop update *                       # 更新全部
scoop uninstall scoop/<app>          # 卸载
```

## 说明

- 全部为免费软件，版权归 [羽翼城 Dogfight360](https://www.dogfight360.com/blog/) 所有，本 bucket 仅做 Scoop 打包分发，不改动原始二进制。
- `hash` 均为下载后实算的 SHA256，未使用跳过校验。
- 清单带 `checkver` + `autoupdate`，作者发新版后可 `scoop checkver` 自动跟进。
- 部分工具（Steamcommunity 302、UsbEAm Hosts Editor、战地6 区域锁定）需要**管理员权限**改 hosts / 装证书 / 改防火墙，Scoop 装的只是文件与快捷方式，权限提升请自行以管理员身份启动。

## 添加新应用

1. 复制 `templates/app.json` 到 `bucket/<应用名>.json`
2. 填 `version` / `url` / `hash` / `bin`
3. 校验：`scoop install scoop/<应用名>` → `scoop uninstall <应用名>`
4. 提交推送
