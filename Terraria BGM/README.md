# Terraria BGM — 泰拉瑞亚环境 BGM 替换

《Casualties: Unknown / 未知伤亡》BepInEx 5 插件：

- 按游戏当前层自动播放对应的泰拉瑞亚环境 BGM；
- 曲目循环播放，不等待原版 `trackInterval`；
- 没有对应文件时自动回退原版 BGM。

- 版本：1.0.0（embedded）
- 适用：Casualties: Unknown（Unity Mono / BepInEx 5.4.x x64）
- GUID：`com.lead.terrariabgm`

---

## 安装

只需要：

```
BepInEx\plugins\TerrariaBGM\TerrariaBGM.dll
```

启动日志：

```
[TBGM] embedded music extracted: 13 new file(s) -> ...\BepInEx\cache\TerrariaBGM
[TBGM] loaded 01-gravel-wasteland.ogg -> depth 0
[TBGM] loaded 13 custom track(s).
[TBGM] playing '01-gravel-wasteland' for depth 0
```

音频会解压到 `BepInEx\cache\TerrariaBGM` 供 Unity 读取，之后启动直接复用缓存。


---

## 游戏层级与曲目

| 文件编号 | biomeDepth | 游戏内名称 | 泰拉瑞亚建议曲 |
| --- | --- | --- | --- |
| `00` | Tutorial | 地球（训练实验室） | Title Screen |
| `01` | 0 | 砾石荒原 | Overworld Day |
| `02` | 1 | 深层砾石带 | Underground |
| `03` | 2 | 干旱沙漠 | Desert |
| `04` | 3 | 辐射废土 | Underground Corruption |
| `05` | 4 | 深林丛渊 | Jungle |
| `06` | 5 | 覆冰断崖 | Snow |
| `07` | 6 | 真菌洼地 | Glowing Mushroom |
| `08` | 7 | 晶蚀空穴 | Hallow |
| `09` | 8 | 地热喷口 | Underworld |
| `10` | 9 | 必须抵达之地 | Boss 2 / Lunar Boss |
| `11` | 10 | 猩红长阶 | Crimson |
| `12` | 11 | 地球/实验室 | Title Screen / Surface Night |

---

## 配置

`BepInEx\config\com.lead.terrariabgm.cfg`

| 配置项 | 默认值 | 说明 |
| --- | --- | --- |
| `Enabled` | `true` | 总开关 |
| `Replace Tutorial` | `false` | 是否替换教程/实验室层 |
| `Loop Custom Tracks` | `true` | 自定义曲目循环 |
| `Verbose Log` | `true` | 记录加载/切换 |

---

## 版本

- 1.0.0 — 12 层 + 教程映射、13 首 OGG 内嵌、循环播放、缺失回退。
