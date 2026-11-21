# Auto Unlock

《Casualties: Unknown / 未知伤亡》自动开锁与自动密码插件。

## 功能

- 进入开锁小游戏后自动完成。
- 进入空投仓/密码盘后自动输入正确密码。
- 可配置完成延迟，默认 0.6 秒，让界面先显示。
- 无需按键，不修改游戏文件。
- 延迟内提前退出界面会立即取消，不会延迟完成或卡死。

## 安装

1. 安装 BepInEx 5.4.x（x64, Mono）。
2. 把 `AutoUnlock.dll` 放到：
   `BepInEx\plugins\AutoUnlock\AutoUnlock.dll`
3. 启动游戏，生成配置：
   `BepInEx\config\com.lead.autounlock.cfg`

## 配置

- `Enabled`
- `Solve Delay`：界面出现后等待秒数（默认 0.6）
- `Verbose Log`

> 与开锁音效类 Mod 一起用时，建议先禁用本插件。
