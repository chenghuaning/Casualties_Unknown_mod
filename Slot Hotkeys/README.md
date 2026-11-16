# Slot Hotkeys — 身体 6 槽位快捷键 + 常驻 HUD

《Casualties: Unknown / 未知伤亡》BepInEx 5 插件：

- 屏幕底部常驻显示身体 **6 个栏位**的物品（不用打开背包）；
- `1`–`6` 直接打开对应栏位的容器（背包/袋子）；
- 槽位没有容器时**什么都不做**（默认不会弹出物品栏）；
- 槽位是**工具类道具**（category/tag 为 tool）时，自动换到主手；
- 启用 mod 时把游戏加速键从 `1/2/3` 改到 `F1/F2/F3`，禁用 mod 后自动恢复原键位。

- 版本：1.0.0
- 适用：Casualties: Unknown（Unity Mono / BepInEx 5.4.x x64）
- 纯客户端 UI/快捷键，不改物品、不改存档

![preview](preview.png)

*HUD 底部 6 格：金色边框为当前主手，青色边框/小点为容器。*

---

## 槽位对应

| 按键 | 身体槽位 | 游戏内名称 |
| --- | --- | --- |
| `1` | slots[0] | 主手（HandF） |
| `2` | slots[1] | 副手（HandB） |
| `3` | slots[2] | 嘴部（Head） |
| `4` | slots[3] | 上背部（UpTorso A） |
| `5` | slots[4] | 中背部（UpTorso B） |
| `6` | slots[5] | 下背部（DownTorso） |

---

## 使用

### 常驻 HUD

- 进入游戏后自动显示在屏幕底部中央，共 6 格，对应 1–6。
- 每格显示物品图标和快捷键数字。
- **金色边框** = 当前使用的手（`Q` 切换主副手时同步变化）。
- **青色边框 + 右下角小点** = 该物品是容器（背包/袋子）。
- 空槽显示暗色格子。
- 位置、大小、透明度都可以在配置里调。

### 槽位快捷键

- 按 `1`–`6` 直接打开对应槽位的容器：
  - 有容器（背包/袋子）→ 打开物品栏并展开该容器；
  - 没有容器（空槽或普通物品）→ **不执行任何动作**，不会弹出物品栏。
- 不再需要先点角色身体或按 `Tab` 打开物品栏。
- 如果想让空槽也弹出物品栏，把配置里的 `Open Inventory When Empty` 改为 `true`。

### 工具类道具

- 按下的槽位如果是工具（镐、钻、撬棍、扳手等 `category = tool` 或带 `tool` 标签的道具），会把它换到**主手**：
  - 主手为空：直接换过去；
  - 主手有普通物品：和主手互换位置；
  - 主手是只能手持的物品（枪/重型工具）：先把它放到空的副手，再把工具换到主手；
  - 主手和副手都占用且都不能放下时：提示 `Main hand busy`，不做改动。
- 槽位里是容器时，**优先打开容器**，不会触发工具切换。
- 不想要这个行为：配置里 `Tool To Main Hand = false`。

### 加速键重映射

- 启用 mod 时：`F1` = 正常速度、`F2` = 加速、`F3` = 超快。
- 原版 `1/2/3` 的加速功能被让给槽位快捷键。
- **禁用 mod**（`Enabled = false` 或删除 DLL）后，加速键自动恢复为原来的 `1/2/3`。
- 游戏设置界面里会显示重映射后的 `F1/F2/F3`；但写回 `settings.json` 的仍是原始按键，所以卸载 mod 不会留下 F1/F2/F3。
- 如果 `F1`–`F3` 和其他 mod 冲突，可以在配置里改成别的键，或关闭 `Remap Speed Keys`。

> 关闭 `Remap Speed Keys` 时，`1/2/3` 会保持原版加速；此时槽位快捷键 `1/2/3` 只会在物品栏已经打开时生效，避免误触加速。

---

## 配置

配置文件：`BepInEx\config\com.lead.slothotkeys.cfg`
**修改后重启游戏生效。**

### 常规

| 配置项 | 默认值 | 说明 |
| --- | --- | --- |
| `Enabled` | `true` | 总开关 |
| `Slot 1 Key ...` | `Alpha1` | 主手槽位快捷键 |
| `Slot 2 Key ...` | `Alpha2` | 副手槽位快捷键 |
| `Slot 3 Key ...` | `Alpha3` | 嘴部槽位快捷键 |
| `Slot 4 Key ...` | `Alpha4` | 上背部槽位快捷键 |
| `Slot 5 Key ...` | `Alpha5` | 中背部槽位快捷键 |
| `Slot 6 Key ...` | `Alpha6` | 下背部槽位快捷键 |

### 行为

| 配置项 | 默认值 | 说明 |
| --- | --- | --- |
| `Open Inventory When Empty` | `false` | 槽位没有容器时是否改为打开物品栏（默认关闭，什么都不做） |
| `Tool To Main Hand` | `true` | 槽位是工具类道具时自动换到主手 |
| `Remap Speed Keys` | `true` | 是否把加速键改为 F1/F2/F3（禁用 mod 时自动恢复） |
| `Speed 1 Key` | `F1` | 正常速度的新按键 |
| `Speed 2 Key` | `F2` | 加速的新按键 |
| `Speed 3 Key` | `F3` | 超快速度的新按键 |
| `Suppress Speed Keys In Inventory` | `true` | 仅当关闭重映射时生效：物品栏打开时阻止 1/2/3 触发加速 |

### HUD

| 配置项 | 默认值 | 说明 |
| --- | --- | --- |
| `Show Slot HUD` | `true` | 是否显示常驻 6 格 HUD |
| `Position` | `BottomCenter` | 位置：`BottomCenter` / `TopCenter` / `TopLeft` |
| `Scale` | `1.0` | HUD 缩放（0.5–3） |
| `Opacity` | `0.9` | HUD 不透明度（0.2–1） |
| `Offset X` | `0` | 相对锚点的水平像素偏移 |
| `Offset Y` | `0` | 相对锚点的垂直像素偏移 |
| `Highlight Active Hand` | `true` | 金色边框标出当前手 |
| `Hide When Inventory Open` | `false` | 打开物品栏时隐藏 HUD |
| `Show Hotkey Numbers` | `true` | 显示 1–6 数字 |

### 其他

| 配置项 | 默认值 | 说明 |
| --- | --- | --- |
| `Show Messages` | `true` | 打开容器时在屏幕上方显示短提示 |
| `Verbose Log` | `false` | 输出每次按键处理（调试用） |

---

## 安装

1. 确认游戏目录已安装 **BepInEx 5.4.x（x64, Mono）**。
2. 把 `SlotHotkeys.dll` 放到：
   ```
   ...\Casualties Unknown\BepInEx\plugins\SlotHotkeys\SlotHotkeys.dll
   ```
3. 启动游戏。日志出现 `Slot Hotkeys v1.0.0 loaded` 即成功。
4. 首次启动生成配置：
   ```
   BepInEx\config\com.lead.slothotkeys.cfg
   ```

---

## 注意事项

- 只读取 `Body.slots` 里的物品，不改变物品位置、重量或容器逻辑。
- HUD 是纯客户端 IMGUI 绘制，联机时不影响其他玩家。
- 如果你同时使用 **Cu-Hotbar**（数字键切主手），两者都会响应 1–6；建议把其中一个的按键改掉。
- `F1`–`F3` 若与其他 mod（例如开发者菜单）冲突，可在配置里改 `Speed 1/2/3 Key`，或关闭 `Remap Speed Keys`。
- 游戏大更新若改动槽位/UI 相关类，可能需要更新插件。
- 卸载：删除 `BepInEx\plugins\SlotHotkeys\` 和 `com.lead.slothotkeys.cfg`；加速键会自动回到原版。
