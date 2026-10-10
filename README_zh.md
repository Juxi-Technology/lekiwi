[English](README.md) | 简体中文

<p align="center">
  <img alt="LeRobot, Hugging Face Robotics Library" src="./media/readme/lerobot-logo-thumbnail.png" width="100%">
</p>

**LeRobot** 致力于为真实机器人提供 PyTorch 模型、数据集与工具，目标是降低入门门槛，让每个人都能贡献并受益于共享数据集与预训练模型。

🤗 与硬件无关的 Python 原生接口，统一了从低成本机械臂（SO-100）到人形机器人的各类平台控制方式。

🤗 标准化的、可扩展的 LeRobotDataset 数据格式（Parquet + MP4 或图像），托管于 Hugging Face Hub，支持大规模机器人数据集的高效存储、流式读取与可视化。

🤗 业界领先的策略模型，已验证可迁移到真实世界，可直接用于训练与部署。

🤗 全面支持开源生态，推动物理 AI 的大众化。

## 📖 文档

### 🤖 机械臂

| 产品 | GitHub | 📖 Wiki 教程 |
|------|--------|-------------|
| **SO-ARM101** 6 轴桌面机械臂 | [原项目](https://huggingface.co/docs/lerobot/so101) | [📖 教程](https://wiki.juxitech.com/tutorials/robot-arms/so-arm101/SO-ARM101-Tutorial) |
| **AmazingHand** 仿生灵巧手 | [GitHub](https://github.com/Juxi-Technology/AmazingHand) | [📖 教程](https://wiki.juxitech.com/tutorials/robot-arms/amazing-hand/AmazingHand-Interface-Control) |
| **Lekiwi** 全向移动机器人 | [原项目](https://huggingface.co/docs/lerobot/lekiwi) | [📖 教程](https://wiki.juxitech.com/tutorials/robot-arms/lekiwi/Lekiwi-Tutorial) |

### 📚 Lekiwi 教程（本仓库内）

组装教程、使用教程与产品资料位于 [`Tutorial/`](Tutorial/)，提供 **11 种语言**：

`en` · `zh-hans` · `zh-hant` · `de` · `es` · `fr` · `it` · `ja` · `ko` · `pt-br` · `pt-pt`

每篇首行都带语言切换条。中文教程见 [Tutorial/zh-hans/](Tutorial/zh-hans/)

## 🛠️ 资源

- **[官方文档](https://huggingface.co/docs/lerobot/index)：** 完整的教程与 API 指南。
- **[中文教程：LeRobot+SO-ARM101中文教程-同济子豪兄](https://zihao-ai.feishu.cn/wiki/space/7589642043471924447)** 涵盖组装、遥操作、数据集、训练与部署的详细文档。已由 Seeed Studio 及 5 位全球黑客松选手验证。
- **[Discord](https://discord.gg/q8Dzzpym3f)：** 加入 `LeRobot` 服务器，与社区交流讨论。
- **[X](https://x.com/LeRobotHF)：** 关注我们的 X 账号，了解最新进展。
- **[机器人学习教程](https://huggingface.co/spaces/lerobot/robot-learning-tutorial)：** 免费的实操课程，学习如何使用 LeRobot 做机器人学习。
- **[折叠 T 恤实验](https://huggingface.co/spaces/lerobot/robot-folding)：** 用 LeRobot 折叠 T 恤的端到端演示。
- **[LeLab](https://github.com/huggingface/leLab)：** LeRobot 的 Web 界面——无需命令行，在浏览器中即可完成遥操作、标定、数据集录制、回放与 SO 机械臂训练。
