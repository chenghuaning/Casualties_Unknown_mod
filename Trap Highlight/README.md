# CU Trap Highlight — 陷阱高亮

《Casualties: Unknown / 未知伤亡》BepInEx 5 插件：把玩家附近的危险陷阱用**红色描边 + 脉冲色层**标出来，可穿墙、穿黑暗显示（可关）。

- 版本：1.0.0
- 适用：Casualties: Unknown（Unity Mono / BepInEx 5.4.x x64）
- 纯客户端视觉，不改陷阱判定、不改存档；联机时只有自己可见

---

## 安装

1. 确认游戏目录已安装 **BepInEx 5.4.x（x64, Mono）**。
2. 把 `CUTrapHighlight.dll` 放到：
   ```
   ...\Casualties Unknown\BepInEx\plugins\CUTrapHighlight\CUTrapHighlight.dll
   ```
   直接放在 `BepInEx\plugins\` 根目录也可以。
3. 启动游戏。日志出现下面这行即加载成功：
   ```
   [Info   :CU Trap Highlight] CU Trap Highlight v1.0.0 loaded.
   ```
4. 首次启动会自动生成配置：
   ```
   BepInEx\config\com.lead.cutraphighlight.cfg
   ```

---

## 使用

- 进游戏后默认**自动开启**，附近陷阱会自动标红，不需要按键。
- `F6`：游戏内临时开/关高亮，屏幕上方会显示 `Trap Highlight: ON / OFF`。
- 默认只处理玩家周围 **22 米**内的陷阱，距离越远颜色越淡。
- 高亮分两层：陷阱边缘的红色描边 + 覆盖在陷阱上的半透明脉冲色层。
- `Through Walls` 开启时，色层会画在世界最上层，隔着墙和黑暗也能看到陷阱轮廓。

---

## 配置

配置文件：`BepInEx\config\com.lead.cutraphighlight.cfg`
**修改后重启游戏生效。**

### 常规

| 配置项 | 默认值 | 说明 |
| --- | --- | --- |
| `Enabled` | `true` | 总开关；`false` 时完全不工作 |
| `Toggle Key` | `F6` | 游戏内临时开关的快捷键，可改成其他键 |
| `Radius` | `22` | 高亮半径（世界单位），范围 2–80 |
| `Refresh Interval` | `0.25` | 重新扫描附近陷阱的间隔（秒） |
| `Max Highlights` | `120` | 同时高亮的陷阱数量上限（性能保护） |

### 陷阱识别

| 配置项 | 默认值 | 说明 |
| --- | --- | --- |
| `Trap Ids` | 见下方列表 | 要识别的陷阱 ID，英文逗号分隔；可自行增删 |

匹配时会自动忽略 `(Clone)`、` (1)` 这类实例后缀、路径前缀和空格，大小写不敏感。

默认列表（27 种）：

```
beartrap, spikestabber, landmine, gunmine, sawblade,
ceilingturret, ceilingturretslim, turret, piston, pistonleft, pistonright,
skullcrusher, coil, soundcannon, drillpod, drillpodbroken,
geyser, lavageyser, spentfuel, radbarrel, icestalagmite,
mushroomdropper, barbedwirefence, grabberplant, grabbershroom,
spicevineceiling, spicevine
```

### 外观

| 配置项 | 默认值 | 说明 |
| --- | --- | --- |
| `Color` | `#FF3B30` | 高亮颜色，`#RRGGBB` 格式 |
| `Outline Alpha` | `0.90` | 描边不透明度，0 为关闭描边 |
| `Overlay Alpha` | `0.35` | 覆盖色层不透明度，0 为关闭色层（也就不能穿墙） |
| `Outline Scale` | `1.15` | 描边相对陷阱贴图的放大比例 |
| `Pulse` | `true` | 是否呼吸闪烁 |
| `Pulse Speed` | `1.2` | 闪烁频率（次/秒），范围 0.1–5 |
| `Through Walls` | `true` | 色层是否画在世界最上层（穿墙/穿黑暗可见） |

### 其他

| 配置项 | 默认值 | 说明 |
| --- | --- | --- |
| `Show Toggle Message` | `true` | 按快捷键时是否在屏幕上方显示提示 |
| `Verbose Log` | `false` | 是否在 BepInEx 日志里输出每个新高亮的陷阱（排错用） |

---

## 常用调整

**觉得太显眼 / 挡视线**

```ini
Outline Alpha = 0.7
Overlay Alpha = 0.15
Pulse = false
```

**只保留描边，不要整片红色覆盖**

```ini
Overlay Alpha = 0
Through Walls = false
```

**想看得更远**

```ini
Radius = 35
```

**想把风扇、跳板、仙人掌也标出来**

在 `Trap Ids` 末尾追加（逗号分隔）：

```
fan, jumppad, cactus, ceilingrye
```

**换成更醒目的颜色**

```ini
Color = #FF0000
```

---

## 注意事项

- 只识别**带 2D 碰撞体**的陷阱；`grabberplant`、`grabbershroom` 只有 LineRenderer，扫不到。
- 一个陷阱有多个贴图时，只描边主贴图。
- `Through Walls = true` 属于“透视提示”，单人使用最合适；联机时其他玩家看不到，但请自行判断是否使用。
- 游戏大更新后如果模组失效，通常是游戏程序集变动导致，需要等对应版本更新。
- 本插件只改显示，不改变陷阱伤害、触发逻辑和掉落。

---

## 卸载

删除以下两项即可：

```
BepInEx\plugins\CUTrapHighlight\
BepInEx\config\com.lead.cutraphighlight.cfg
```
