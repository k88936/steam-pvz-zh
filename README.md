# PvZ on steam 汉化

## 应用补丁
覆盖
```
properties/LawnStrings.txt
main.pak
PlantsVsZombies.exe
```

## 修复
```bash
mkdir -p "$HOME/.local/share/wine-locale-pvz/usr/lib/locale"
localedef --prefix="$HOME/.local/share/wine-locale-pvz" --no-archive -i zh_CN -f UTF-8 zh_CN.UTF-8
```

修改 Steam 用户目录下的 `localconfig.vdf`，把 AppID `3590` 的 `LaunchOptions` 设为 `LOCPATH=$HOME/.local/share/wine-locale-pvz/usr/lib/locale LC_ALL=zh_CN.UTF-8 HOST_LC_ALL=zh_CN.UTF-8 LANG=zh_CN.UTF-8 %command%`。

## 原理
`properties/LawnStrings.txt` 是 GBK。Proton 默认 `ACP=1252`，需用中文 locale 启动以启用 `ACP=936`。
