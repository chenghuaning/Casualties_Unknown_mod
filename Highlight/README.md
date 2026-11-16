# Highlight — 陷阱 / 敌对生物高亮

《Casualties: Unknown / 未知伤亡》BepInEx 5 插件：把玩家附近的**危险陷阱标红**、**敌对生物标黄**，红色/黄色描边 + 脉冲色层，可穿墙、穿黑暗显示（可关）。

- 版本：1.2.0（原 `CU Trap Highlight`，自 1.2.0 起更名为 `Highlight`）
- 适用：Casualties: Unknown（Unity Mono / BepInEx 5.4.x x64）
- 纯客户端视觉，不改陷阱/生物判定、不改存档；联机时只有自己可见
- 后续会继续增加其他高亮类别（掉落物、容器、商人等）

---

## 安装

1. 确认游戏目录已安装 **BepInEx 5.4.x（x64, Mono）**。
2. 把 `Highlight.dll` 放到：
   ```
   ...\Casualties Unknown\BepInEx\plugins\Highlight\Highlight.dll
   ```
   直接放在 `BepInEx\plugins\` 根目录也可以。
3. 启动游戏。日志出现下面这行即加载成功：
   ```
   [Info   : Highlight] Highlight v1.2.0 loaded.
   ```
4. 首次启动会自动生成配置：
   ```
   BepInEx\config\com.lead.highlight.cfg
   ```

> 从旧版 `CU Trap Highlight` 升级：删除 `BepInEx\plugins\CUTrapHighlight\` 和 `com.lead.cutraphighlight.cfg`，再按上面安装。旧配置项名称不变，可以直接把旧 cfg 的内容复制到新 cfg。

---

## 使用

- 进游戏后默认**自动开启**，附近陷阱和敌对生物会自动高亮，不需要按键。
- 颜色区分：
  - **红色** = 危险陷阱（捕兽夹、地雷、电锯、炮塔、尖刺等）
  - **黄色** = 敌对生物（爬行者、荆棘背、雪地行者、激光无人机、守卫等）
- `F6`：游戏内临时开/关全部高亮，屏幕上方会显示 `Highlight: ON / OFF`。
- 默认只处理玩家周围 **22 米**内的目标，距离越远颜色越淡。
- `Through Walls` 开启时，色层会画在世界最上层，隔着墙和黑暗也能看到轮廓。

---

## 配置

配置文件：`BepInEx\config\com.lead.highlight.cfg`
**修改后重启游戏生效。**

### 常规

| 配置项 | 默认值 | 说明 |
| --- | --- | --- |
| `Enabled` | `true` | 总开关；`false` 时完全不工作 |
| `Toggle Key` | `F6` | 游戏内临时开关的快捷键，可改成其他键 |
| `Radius` | `22` | 高亮半径（世界单位），范围 2–80 |
| `Refresh Interval` | `0.25` | 重新扫描附近目标的间隔（秒） |
| `Max Highlights` | `120` | 同时高亮的目标数量上限（性能保护） |

### 陷阱 / 敌对生物识别

| 配置项 | 默认值 | 说明 |
| --- | --- | --- |
| `Trap Ids` | 见下方列表 | 要识别的陷阱 ID，英文逗号分隔 |
| `Highlight Enemies` | `true` | 是否同时高亮敌对生物（黄色） |
| `Enemy Ids` | 见下方列表 | 要识别的敌对生物 ID，英文逗号分隔 |

匹配时会自动忽略 `(Clone)`、` (1)` 这类实例后缀、路径前缀和空格，大小写不敏感。

默认陷阱列表（27 种）：

```
beartrap, spikestabber, landmine, gunmine, sawblade,
ceilingturret, ceilingturretslim, turret, piston, pistonleft, pistonright,
skullcrusher, coil, soundcannon, drillpod, drillpodbroken,
geyser, lavageyser, spentfuel, radbarrel, icestalagmite,
mushroomdropper, barbedwirefence, grabberplant, grabbershroom,
spicevineceiling, spicevine
```

默认敌对生物列表（11 种）：

```
shadecrawler, wallbiter, thornbackyoung, thornbackelder,
overgrowntick, cavetick, snowstrider, laserdrone,
crystalenemy, guard, bloodsuckerden
```

### 外观

| 配置项 | 默认值 | 说明 |
| --- | --- | --- |
| `Color` | `#FF3B30` | 陷阱高亮颜色（红色），`#RRGGBB` 格式 |
| `Enemy Color` | `#FFD400` | 敌对生物高亮颜色（黄色），`#RRGGBB` 格式 |
| `Outline Alpha` | `0.90` | 描边不透明度，0 为关闭描边 |
| `Overlay Alpha` | `0.35` | 覆盖色层不透明度，0 为关闭色层（也就不能穿墙） |
| `Outline Scale` | `1.15` | 描边相对贴图的放大比例 |
| `Pulse` | `true` | 是否呼吸闪烁 |
| `Pulse Speed` | `1.2` | 闪烁频率（次/秒），范围 0.1–5 |
| `Through Walls` | `true` | 色层是否画在世界最上层（穿墙/穿黑暗可见） |

### 其他

| 配置项 | 默认值 | 说明 |
| --- | --- | --- |
| `Show Toggle Message` | `true` | 按快捷键时是否在屏幕上方显示提示 |
| `Verbose Log` | `false` | 是否在 BepInEx 日志里输出每个新高亮的目标（排错用） |

---

## 常用调整

**只要陷阱，不要敌对生物高亮**

```ini
Highlight Enemies = false
```

**换个敌对生物颜色（例如橙色）**

```ini
Enemy Color = #FF8C00
```

**觉得太显眼 / 挡视线**

```ini
Outline Alpha = 0.7
Overlay Alpha = 0.15
Pulse = false
```

**只保留描边，不要整片颜色覆盖**

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

---

## 注意事项

- 只识别**带 2D 碰撞体**的陷阱和生物；`grabberplant`、`grabbershroom` 只有 LineRenderer，扫不到。
- 一个目标有多个贴图时，只描边主贴图。
- 敌对生物列表按对象名匹配；如果游戏新增敌人，把它的对象名加进 `Enemy Ids` 即可。
- `Through Walls = true` 属于“透视提示”，单人使用最合适；联机时其他玩家看不到，但请自行判断是否使用。
- 游戏大更新后如果模组失效，通常是游戏程序集变动导致，需要等对应版本更新。
- 本插件只改显示，不改变陷阱伤害、生物 AI 和掉落。

---

## 卸载

删除以下两项即可：

```
BepInEx\plugins\Highlight\
BepInEx\config\com.lead.highlight.cfg
```
