# 不完美，才真实 · AI 视频镜头与灯光 skill

AI 视频一眼假，毛病多半不在画质，在镜头和光：太标准了，标准到不像有人在拍。

镜头 skill 的思路是用"不完美"指导运镜。真人拍的镜头会慢半拍、会被门框挡住、会忍不住往前凑，这些"毛病"背后都有原因，也正是真实感的来源。你选一位导演，它把这位导演的拍法翻成一条条具体的拍摄动作，写成能直接用的提示词。

这个仓库有两个 skill，拆剧本时一起用：先定这场戏的情绪，再分别决定镜头怎么动、光怎么打。

| skill | 管什么 | 文件夹 |
|---|---|---|
| **imperfect-camera** | 镜头怎么动：选一位导演，生成像真人拍的运镜提示词 | `imperfect-camera/` |
| **scene-lighting** | 光怎么打：按剧情拆出每场戏的灯光卡，写成模型照着执行的提示词 | `scene-lighting/` |

## imperfect-camera · 内置 10 位导演

王家卫 · 姜文 · 宁浩 · 侯孝贤 · 达内兄弟 · 格林格拉斯 · 安德里亚·阿诺德 / 罗比·瑞恩 · 卢贝兹基 · 是枝裕和 · 小津安二郎

说不出名字也行，告诉它你想要的感觉（"像纪录片""暧昧港风""燃""好笑但不傻"），它会推荐。

## scene-lighting · 剧本灯光设计

AI 默认的光是"哪儿都照好"的平均光，写"电影感布光""伦勃朗光、体积光、8K"都改变不了。这个 skill 让你**先定情绪，再写光从哪来**：

- 8 种剧情功能（温暖、孤独、紧张、危险、浪漫、回忆、压抑、希望）各有一套实测过的灯光写法
- 摄影术语换成画面里看得见的东西：光源入画定方向、写曝光关系出逆光、写身后的台灯出轮廓光
- 一场戏一段灯光文字，所有镜头复用；近景加一句方向，光就不会穿帮
- 附一段完整的短剧拆解示例（6 场 7 个镜头，实测 6/7 合格）

用法：把剧本给它，说"给这段剧本设计灯光"。

## 安装

**Claude Code**：把 `imperfect-camera` 和 `scene-lighting` 文件夹放进项目的 `.claude/skills/`（只对这个项目生效），或放进 `~/.claude/skills/`（所有项目生效）。

**Claude 网页版 / App**：下载 [imperfect-camera.zip](https://github.com/misterwin0553-droid/imperfect-camera/releases/latest/download/imperfect-camera.zip) 和 [scene-lighting.zip](https://github.com/misterwin0553-droid/imperfect-camera/releases/latest/download/scene-lighting.zip)，在 设置 → 功能（Capabilities）→ Skills 里分别上传。

## imperfect-camera 怎么用

直接说：

> 用侯孝贤的风格拍：她站在窗前，门外传来钥匙声，她转身。10 秒，竖屏。

它会给你两段提示词：**普通版**（常规 AI 拍法）和**导演版**。两段都拿去生成，对比着看。

- 用 **PX Show**：它会把内容写进对应字段。
- 用**其他模型**（Seedance、可灵、即梦、Veo、Sora……）：直接粘贴那段提示词。

## imperfect-camera 遵循的几条写法

- **写拍的人，不写运镜。** 不写"镜头平稳推近"，写"镜头晚了半拍才反应过来，往右挪，绕到能看清她脸的位置"。
- **顺着模型的脾气。** 模型的镜头只回应画面里已经发生的事，所以"慢半拍""追过去"好拍，"镜头比人先动"难拍，后者交给时间点或剪辑。
- **写镜头情绪时锁住演员。** 否则紧张会跑到演员身上。
- **动作幅度给上限。** 冲得太猛会被拍成跳切。
- **把时间写满。** 空着的时间，模型会补上最标准的平稳运镜。
- **导演名字不进提示词。** 写"王家卫风格"，模型多半只学到色调；要写的是他怎么拍。

背后的完整思路见 [`imperfect-camera/references/theory.md`](imperfect-camera/references/theory.md)。

## 反馈

用出了好片子或者踩了坑，欢迎[开一个 Issue](https://github.com/misterwin0553-droid/imperfect-camera/issues/new?template=feedback.yml)，表单都备好了。最有用的是**同一个场景的普通版和导演版**一起发；也可以照 [`FEEDBACK.md`](FEEDBACK.md) 的格式，在 X 上评论或私信我。

## 说明

- 导演卡是对公开作品拍摄风格的分析和概括，不代表导演本人或其团队。
- 许可：[CC BY 4.0](LICENSE)。可以自由使用、修改、再分享（包括商用），请注明出处并附上本仓库链接。
