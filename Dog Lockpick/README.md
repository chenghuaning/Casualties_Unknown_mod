# Dog Lockpick

《Casualties: Unknown / 未知伤亡》开锁时播放「大狗」音效的插件。

## 功能

- 只有按住开锁键时才循环播放「大狗」，打开界面不播放。
- 随开锁进度/时间推移，音调与音量逐渐升高、速度变快。
- 松开开锁键立即停止。
- 开锁成功时停止循环，播放一次 3 倍时长拉伸的「叫！」。
- 成功音继承循环最后的音调，不会突然降调。
- 音频已内嵌进 DLL，单文件安装。

## 安装

1. 安装 BepInEx 5.4.x（x64, Mono）。
2. 把 `DogLockpick.dll` 放到：
   `BepInEx\plugins\DogLockpick\DogLockpick.dll`
3. 使用时请禁用 Auto Unlock，否则开锁会瞬间完成。
4. 启动游戏，按住开锁键。

## 配置

`BepInEx\config\com.lead.doglocpick.cfg`

- `Enabled`
- `Loop Volume`（默认 0.8）
- `Max Pitch`（默认 2.2）
- `Success Volume`（默认 1.0）
- `Verbose Log`
