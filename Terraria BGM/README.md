# Terraria BGM

《Casualties: Unknown / 未知伤亡》按层替换泰拉瑞亚环境 BGM 的插件。

## 功能

- 按当前层自动播放对应的泰拉瑞亚环境音乐。
- 13 首 OGG 已内嵌进 DLL，单文件安装，不需要 Music 文件夹。
- 教程层与 12 个游戏层分别映射。
- 原版没有 BGM 的层也会循环播放。
- 随层切换自动换曲并循环。
- 可选外部 `Music\` 文件夹覆盖内嵌曲目。

## 安装

1. 安装 BepInEx 5.4.x（x64, Mono）。
2. 把 `TerrariaBGM.dll` 放到：
   `BepInEx\plugins\TerrariaBGM\TerrariaBGM.dll`
3. 启动游戏即可。

## 配置

`BepInEx\config\com.lead.terrariabgm.cfg`

- `Enabled`
- `Replace Tutorial`：是否替换教程/实验室层
- `Loop Custom Tracks`
- `Verbose Log`
