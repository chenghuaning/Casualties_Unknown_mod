# Full Description — F9 全局显示完整物品描述

《Casualties: Unknown / 未知伤亡》BepInEx 5 插件：

- **按 F9 全局开启/关闭完整描述**，；
- 开启后**全局**把所有 `ItemInfo.rec.min` 设为 `int.MinValue`：即使物品需要 99 INT，也会显示真实名称和完整描述；
- 同时关闭低智力/脑损伤导致的描述乱码；
- 开启/关闭时**屏幕上方**会弹出 `Full Description: ON/OFF` 提示（不再挡在屏幕中央）。

- 版本：1.0.0
- 适用：Casualties: Unknown（Unity Mono / BepInEx 5.4.x x64）
- GUID：`com.lead.fulldescription`

---

## 使用

1. 进游戏后按 **F9**：
   - 日志：`[FD] Always Show = True`
   - 游戏内提示：`Full Description: ON`
2. 鼠标悬停任意物品，即可看到：
   - 真实物品名；
   - 完整描述；
   - 不因 INT 不足变成“某种东西/你无法理解”。
3. 再按 **F9** 关闭：
   - `Full Description: OFF`
   - 恢复原版按智力显示。

> 不再检测 Shift，也不需要按住任何键。

---

## 配置

`BepInEx\config\com.lead.fulldescription.cfg`

| 配置项 | 默认值 | 说明 |
| --- | --- | --- |
| `Enabled` | `true` | 总开关 |
| `Bypass Recognition` | `true` | 开启时无视智力识别限制 |
| `Bypass Text Distortion` | `true` | 开启时关闭低智力乱码 |
| `Always Show (no Shift)` | `false` | 当前是否处于开启状态；F9 会切换并写回 |
| `Toggle Key` | `F9` | 全局切换键 |


---

## 安装

1. 安装 BepInEx 5。
2. 把 `FullDescription.dll` 放到：
   ```
   BepInEx\plugins\FullDescription\FullDescription.dll
   ```
3. 启动游戏，按 F9 开启。

---

## 文件

- `FullDescription.dll`
- `README.md`

---

## 版本

- 1.0.0 — F9 全局切换、真实名称/完整描述
