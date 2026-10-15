# РЕАКТОР / Reactor Audio Visualizer

以切尔诺贝利反应堆堆芯的控制棒阵列为视觉原型的实时音频可视化实验（整活儿向）。

网页使用 Web Audio API 在浏览器本机分析音频，将不同频段的能量映射为 709 根控制棒的升降运动。支持三种音源、本地音频文件、麦克风输入、视角拖动与缩放，以及灵敏度、平滑度和音量调节。

## 功能

- **音源**：演示信号（ДРОН，八振荡器纯五度嗡鸣）／ **进行曲**（МАРШ，112 BPM 的 Web Audio 实时合成进行曲：底鼓、军鼓、铜管和弦、旋律）／ 麦克风（监听静音，防啸叫）／ 导入本地音频文件（MP3 / WAV / M4A / FLAC）。
- **皮肤**（04 / ОФОРМЛЕНИЕ）：
  - `ОЛИВА` 橄榄 · 值班 — 默认军绿配色
  - `КРАСНАЯ ЗВЕЗДА` 构成红 — 构成主义红黑白
  - `ФОСФОР` 磷光 — CRT 控制室青绿磷光
  - `РЖАВЧИНА` 锈蚀 — 普里皮亚季锈橙
  - `ГОСТ` 蓝图 — 浅色图纸风（响度越大棒越深）
  - 皮肤选择会写入 `localStorage`。
- **视角**：拖动旋转、滚轮缩放、重置视角、全屏。

## 关于“勋宗进行曲”

“勋宗”是网友给勃列日涅夫起的梗称（勋章太多）。所谓“勋宗进行曲”通常指《苏维埃进行曲》（*Soviet March*，《红色警戒 3》原声）。该曲目受版权保护，无法随项目分发，因此内置的“进行曲”是**用振荡器实时合成的原创段落**，风格取自苏式军乐（小调、进行曲节奏、铜管）；想听原曲，直接用「导入音频文件」即可。

## Run locally

```bash
python3 -m http.server 4173 --directory dist
```

Then open <http://localhost:4173>.

## Notes

This is an audiovisual interaction experiment. It is not a physical simulation of a reactor, and audio is processed locally in the browser.

## License

MIT. See [LICENSE](LICENSE).
