# scoop

Raisin55 的 Scoop bucket —— 存放自建 / 常用应用清单。

## 安装这个 bucket

```powershell
scoop bucket add scoop https://github.com/Raisin55/scoop
```

## 安装里面的应用

```powershell
scoop install scoop/<app>
```

## 查看有哪些应用

```powershell
scoop bucket list
scoop search --bucket scoop
```

## 目录结构

| 路径 | 作用 |
|---|---|
| `bucket/` | 应用清单，每个应用一个 `<app>.json` |
| `templates/app.json` | 新建清单时的模板，复制到 `bucket/` 改名使用 |

## 添加一个应用

1. 复制 `templates/app.json` 到 `bucket/<应用名>.json`
2. 填好 `version` / `url` / `hash` / `bin`
3. 本地校验（强烈建议）：

```powershell
scoop install scoop/<应用名>      # 装一次
scoop uninstall <应用名>          # 再卸载，确认干净
```

4. 提交推送：

```bash
git add bucket/<应用名>.json
git commit -m "add <应用名>"
git push
```

> `hash` 必须是真实 SHA256，否则安装会被拒绝。取法：`Get-FileHash <文件> -Algorithm SHA256`
