# Full Description — Wiki 物品数据库

从 [未知伤亡中文维基](https://casualtiesunknown.huijiwiki.com/wiki/) 抓取的物品数据。

## 文件

- `wiki_items.json`：300 个物品的整理后数据，按 `id` 索引。
- `items.sqlite`：同一份数据的 SQLite 数据库，表名 `items`。
- `items_raw.json`：从 `Data:Item/*.json` 抓取的原始 JSON。
- `long_desc.json`：286 个物品的 Wiki「描述」章节长文本。
- `long_desc_v2.json`：修正模板引用后的 290 条长描述（当前 Mod 使用）。
- `normalize.py` / `fetch_long.py`：抓取与整理脚本。

## 字段

| 字段 | 说明 |
| --- | --- |
| `id` | 游戏内物品 ID |
| `en` / `zh` | 英文名 / 中文名 |
| `desc` | 游戏内短描述 |
| `long` | Wiki「描述」章节长文本（部分物品没有） |
| `category` | 游戏分类（food / medical / drug / tool / container / utility / water / custom / unobtainable / trash） |
| `foodType` | 食物类别：0 一般、1 肉类、2 果蔬 |
| `weight` / `value` / `rec` | 重量 / 交易价值 / 辨识等级 |
| `tags` / `decay` | 标签 / 腐坏分钟数 |
| `flags` | 属性和布尔标记 |
| `effects` | 使用/医疗效果（已格式化为中文） |
| `acquisition` | 获取途径 |
| `recipe` | 配方需要 INT 与材料 |
| `container` / `battery` / `wearable` / `capacity` | 容器、电池、穿戴、液体容量 |
| `sounds` | 音效文件名 |

## 来源与许可

- 数据来自未知伤亡中文维基的 `Data:Item/<id>.json` 与物品页「描述」章节。
- 抓取时间：2026-11-21。
- 共 300 个物品；290 个有长描述。
- 维基文字内容采用 [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/cn/legalcode) 许可。

## 液体数据

- `liquids_raw.json`：75 个 `Data:Liquid/*.json` 原始数据。
- `liquids_long_v2.json`：修正模板引用后的 74 条液体长描述（当前 Mod 使用）。
- `liquids.json`：整理后的液体名称、颜色、交易价值、可注射/可医疗、饮用/医疗效果（按 mL 缩放）。
- `items.sqlite` 中的 `liquids` 表：75 条。

## 英文数据

- `long_desc_en.json`：298 条英文物品长描述（Miraheze 英文 Wiki）。
- `liquids_long_en.json`：70 条英文液体长描述。
- `wiki_items.json` 增加 `long_en` / `effects_en` / `flags_en` / `desc_en`。
- `liquids.json` 增加 `desc_en` / `full_desc_en` / `label_en`。
