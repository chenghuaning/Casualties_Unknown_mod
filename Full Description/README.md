# Full Description 2.1.0

《Casualties: Unknown / 未知伤亡》物品与液体详细信息增强。

按 `F9` 全局开启：

- 低智力时显示真实物品名与描述；
- 中英文自适应：中文环境用中文 Wiki 长描述与效果名，英文环境用英文 Wiki 长描述与英文效果名；
- 追加原版没有的**单次效果**：饥饿、口渴、情绪、反胃、体重、耐久、治疗等；
- 液体容器追加液体名称、Wiki 描述与按容量换算的饮用/医疗效果；
- 食物效果按角色食性调整：草食角色吃肉营养减半并额外反胃，肉食角色吃果蔬会立即呕吐；
- 所有内容都是补充，不重复原版已有的重量/价值/腐坏/辨识。

---

## 功能

- **F9 全局开关**，不需要按住 Shift。
- **识别绕过**：低 INT 时也能看到真实名称与完整描述。
- **长描述替换**：有 Wiki `full_desc` 时替换原版短描述，避免重复。
- **单次效果**：食物/药品的使用效果，数值最多保留 2 位小数。
- **角色食性**：
  - 草食角色 + 肉类：饥饿减半，额外反胃；
  - 肉食角色 + 果蔬：立即呕吐，不显示营养效果。
- **液体效果**：
  - 读取容器运行时 `WaterContainerItem.stack`；
  - 支持转移、混合、空瓶；
  - 每种液体按自身 mL 数计算效果；
  - 最多显示 5 种，超出提示“另有 N 种液体”。
- **原版字段不重复**：重量、价值、腐坏、辨识、使用方式仍由游戏原生提示显示。

---

## 数据库

- 300 个物品
- 75 种液体
- 中文长描述：290 条物品 + 74 种液体
- 英文长描述：298 条物品 + 70 种液体（英文 Wiki 覆盖）

数据文件在 GitHub 的 `wiki/` 目录：

- `wiki_items.json` / `items.sqlite`
- `liquids.json` / `liquids_raw.json` / `liquids_long_v2.json`

DLL 内嵌 `wiki_items.json` 与 `liquids.json`，安装时不需要额外文件。

---

## 安装

1. 安装 BepInEx 5.4.x（x64, Mono）。
2. 把 `FullDescription.dll` 放到：
   ```
   BepInEx\plugins\FullDescription\FullDescription.dll
   ```
3. 启动游戏，按 `F9` 开启。

---

## 配置

`BepInEx\config\com.lead.fulldescription.cfg`

| 配置 | 默认 | 说明 |
| --- | --- | --- |
| `Enabled` | `true` | 总开关 |
| `Bypass Recognition` | `true` | 低智力时绕过识别 |
| `Bypass Text Distortion` | `true` | 关闭低智力文字乱码 |
| `Always Show (no Shift)` | `false` | 当前开关状态，F9 会写回 |
| `Toggle Key` | `F9` | 全局切换键 |
| `Show Wiki Details` | `true` | 追加单次效果/容器等补充信息 |
| `Show Liquid Details` | `true` | 追加液体描述与效果 |
| `Replace Description` | `true` | 用 Wiki 长描述替换原版短描述（中英文环境） |

安装 **Lead Keybinds** 后，可在游戏 **设置 → 输入** 中直接改键。

---

## 兼容性

- 纯客户端 UI，不修改世界、物品属性或存档。
- 与 QoL Unknown、CUCoreLib、Casualties Together 共存。
- 如果其他工具提示 Mod 在本 Mod 之后整体覆盖 tooltip，建议只保留一个。

---

## 许可

## 2.1.0 中英文适配

- 中文环境显示中文长描述与中文效果名；
- 英文环境显示英文 Wiki 长描述与英文效果名（Hunger / Thirst / Mood / Sickness 等）；
- 新增英文 Wiki 抓取数据：298 条物品、70 种液体；
- 英文缺失条目自动回退到游戏原版短描述。

## 2.0.2 修复

- 统一换行符为 `\n`，移除 `AppendLine` 产生的 `\r\n`，修正提示框行距不一致；

## 2.0.1 修复

- 修复 Wiki 模板引用（如 `{{物品|canvas}}`）被清空导致的长描述缺字；
- 绷带、撕裂的绷带等描述已恢复“帆布”等引用名称；
- 重新生成 290 条物品长描述与 74 条液体长描述。

---

Wiki 文字内容来自 [未知伤亡中文维基](https://casualtiesunknown.huijiwiki.com/wiki/)，采用 CC BY-SA 4.0。
