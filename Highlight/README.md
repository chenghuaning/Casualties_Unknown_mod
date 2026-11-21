# Highlight

《Casualties: Unknown / 未知伤亡》纯客户端陷阱与敌对生物高亮插件。

## 功能

- 自动高亮附近陷阱（红色）和敌对生物（黄色），带描边与脉冲光晕。
- 可穿墙/穿黑暗显示，也可关闭只保留自然描边。
- 陷阱、敌人各有一份可编辑 ID 列表，可单独关闭敌人高亮。
- 开锁小游戏显示绿色有效角度与容错范围。
- 游戏内 `F6` 开关（可改键），切换时屏幕上方短提示。
- 可配置扫描半径、刷新间隔、最大数量、颜色、透明度、描边大小与脉冲。
- 纯本地显示，不修改世界、物品或存档。

## 安装

1. 安装 BepInEx 5.4.x（x64, Mono）。
2. 把 `Highlight.dll` 放到：
   `BepInEx\plugins\Highlight\Highlight.dll`
3. 启动游戏，首次运行生成：
   `BepInEx\config\com.lead.highlight.cfg`

## 配置

主要配置项：

- `Enabled`、`Toggle Key`（默认 `F6`）
- `Radius`、`Refresh Interval`、`Max Highlights`
- `Trap Ids`、`Enemy Ids`、`Highlight Enemies`
- `Color`、`Enemy Color`、`Outline Alpha`、`Overlay Alpha`
- `Through Walls`、`Pulse`、`Pulse Speed`
- `Show Lockpick Helper` 及辅助颜色/宽度/半径
