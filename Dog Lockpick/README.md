# Dog Lockpick — 开锁大狗叫音效

- 版本：1.0.0
- 适用：Casualties: Unknown（Unity Mono / BepInEx 5.4.x x64）
- GUID：`com.lead.doglocpick`

## 配置

`BepInEx\config\com.lead.doglocpick.cfg`

| 配置项 | 默认值 | 说明 |
| --- | --- | --- |
| `Enabled` | `true` | 总开关 |
| `Loop Volume` | `0.8` | 循环音量基数 |
| `Max Pitch` | `2.2` | 开锁末尾的播放速度/音调（1–4） |
| `Success Volume` | `1.0` | 成功「叫！」音量 |
| `Verbose Log` | `true` | 记录循环开始/音调/成功 |

---

## 安装

1. 安装 BepInEx 5。
2. 把 `DogLockpick.dll` 放到：
   ```
   BepInEx\plugins\DogLockpick\DogLockpick.dll
   ```
3. 启动游戏，按住开锁键即可听到。

---

## 文件

- `DogLockpick.dll`
- `README.md`
