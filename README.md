# РЕАКТОР / Reactor Audio Visualizer

以切尔诺贝利反应堆堆芯的控制棒阵列为视觉原型的实时音频可视化实验（整活儿向）。

网页使用 Web Audio API 在浏览器本机分析音频，将不同频段的能量映射为 709 根控制棒的升降运动。支持三种内置音源、本地音频文件、麦克风输入、视角拖动与缩放，以及灵敏度、平滑度和音量调节。

> Fork of [wzk112/reactor-audio-visualizer](https://github.com/wzk112/reactor-audio-visualizer)（上游），本仓库为个人分支：<https://github.com/YicongCao/reactor-audio-visualizer>。

## 功能

- **音源**（01 / ИСТОЧНИК СИГНАЛА）：演示信号（ДРОН，八振荡器纯五度嗡鸣）／ **进行曲**（МАРШ，112 BPM 的 Web Audio 实时合成进行曲：底鼓、军鼓、大号低音、铜管和弦、旋律）／ 麦克风（监听静音，防啸叫）／ 导入本地音频文件（MP3 / WAV / M4A / FLAC，可拖动进度条）。
- **响应调节**（02 / РЕАКЦИЯ СТЕРЖНЕЙ）：灵敏度 0.3–3.0×、运动平滑度 0–95%、播放音量。控制棒高度按 `45 Hz → 14400 Hz` 指数映射，低频在堆芯中心、高频在边缘。
- **皮肤**（04 / ОФОРМЛЕНИЕ）：
  - `ОЛИВА` 橄榄 · 值班 — 默认军绿配色
  - `КРАСНАЯ ЗВЕЗДА` 构成红 — 构成主义红黑白
  - `ФОСФОР` 磷光 — CRT 控制室青绿磷光
  - `РЖАВЧИНА` 锈蚀 — 普里皮亚季锈橙
  - `ГОСТ` 蓝图 — 浅色图纸风（响度越大棒越深）
  - 选择会写入 `localStorage`，刷新后保留。
- **视角**：拖动旋转、滚轮缩放、重置视角、全屏。

## 关于“勋宗进行曲”

“勋宗”是网友给勃列日涅夫起的梗称（勋章太多）。所谓“勋宗进行曲”通常指《苏维埃进行曲》（*Soviet March*，《红色警戒 3》原声）。该曲目受版权保护，无法随项目分发，因此内置的“进行曲”是**用振荡器实时合成的原创段落**，风格取自苏式军乐（小调、进行曲节奏、铜管）；想听原曲，直接用「导入音频文件」即可。

## 本分支相对上游的改动

- 新增 5 套皮肤与整套主题系统：`style.css` 的硬编码配色改为 CSS 自定义属性，canvas 侧（棒体、侧面、警戒环、频谱条）从主题对象取色。
- 新增“进行曲 / МАРШ”音源，Web Audio 实时合成的 112 BPM 苏式进行曲。
- 注入苏联控制室元素：出厂铭牌（`СДЕЛАНО В СССР · РБМК-1000 · ЗАВ. № 04 · ИЗГ. 1977 г.`）、西里尔文分区标题与单位标签、堆芯轴线标注、灵敏度限值警告条。
- `dist/assets/` 下新增 AI 生成的氛围素材（共约 190 KB）：
  - `bg-core.jpg` — 切尔诺贝利厂区黄昏全景，作为堆芯舞台背景层，经 `mix-blend-mode: luminosity` 与各皮肤渐变混合，自动跟随主题色调；
  - `knob-plate.jpg` — 苏式胶木旋钮，替换三个滑块与进度条的拖动块，且**随数值真实旋转**（-135°…+135°）；
  - `button-play.jpg` — 红色蘑菇头急停按钮，替换播放键；
  - `meter-gauge.jpg` — 指针式表头，作为安装在控制室里的仪表装饰叠在舞台右上角；
  - `tape-strip.jpg` — 做旧黄黑警示带，用于舞台底边封条与限值警告条。
- 修复待机涟漪动画首次播放后永久失效的问题。

## Run locally

```bash
git clone git@github.com:YicongCao/reactor-audio-visualizer.git
cd reactor-audio-visualizer
python3 -m http.server 4173 --directory dist
```

Then open <http://localhost:4173>.

无需构建、无依赖，直接用任意静态服务器托管 `dist/` 即可。

## Notes

This is an audiovisual interaction experiment. It is not a physical simulation of a reactor, and audio is processed locally in the browser.

## License

MIT. See [LICENSE](LICENSE).
