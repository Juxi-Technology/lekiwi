English | [简体中文](README_zh.md)

<p align="center">
  <img alt="LeRobot, Hugging Face Robotics Library" src="./media/readme/lerobot-logo-thumbnail.png" width="100%">
</p>

**LeRobot** aims to provide models, datasets, and tools for real-world robotics in PyTorch. The goal is to lower the barrier to entry so that everyone can contribute to and benefit from shared datasets and pretrained models.

🤗 A hardware-agnostic, Python-native interface that standardizes control across diverse platforms, from low-cost arms (SO-100) to humanoids.

🤗 A standardized, scalable LeRobotDataset format (Parquet + MP4 or images) hosted on the Hugging Face Hub, enabling efficient storage, streaming and visualization of massive robotic datasets.

🤗 State-of-the-art policies that have been shown to transfer to the real-world ready for training and deployment.

🤗 Comprehensive support for the open-source ecosystem to democratize physical AI.

## 📖 Docs

### 🤖 Robot Arms

| Product | GitHub | 📖 Wiki Tutorial |
|---------|--------|-----------------|
| **SO-ARM101** 6-Axis Desktop Arm | [Original Project](https://huggingface.co/docs/lerobot/so101) | [📖 Tutorial](https://wiki.juxitech.com/tutorials/robot-arms/so-arm101/SO-ARM101-Tutorial) |
| **AmazingHand** Bionic Dexterous Hand | [GitHub](https://github.com/Juxi-Technology/AmazingHand) | [📖 Tutorial](https://wiki.juxitech.com/tutorials/robot-arms/amazing-hand/AmazingHand-Interface-Control) |
| **Lekiwi** Omnidirectional Robot | [Original Project](https://huggingface.co/docs/lerobot/lekiwi) | [📖 Tutorial](https://wiki.juxitech.com/tutorials/robot-arms/lekiwi/Lekiwi-Tutorial) |

### 📚 LeKiwi Tutorials (in this repository)

Step-by-step **assembly** and **usage** guides, plus product information, live in [`Tutorial/`](Tutorial/) — available in **11 languages**:

`en` · `zh-hans` · `zh-hant` · `de` · `es` · `fr` · `it` · `ja` · `ko` · `pt-br` · `pt-pt`

Each guide carries a language switcher on its first line. English: [Tutorial/en/](Tutorial/en/)

## 🛠️ Resources

- **[Documentation](https://huggingface.co/docs/lerobot/index):** The complete guide to tutorials & API.
- **[Chinese Tutorials: LeRobot+SO-ARM101中文教程-同济子豪兄](https://zihao-ai.feishu.cn/wiki/space/7589642043471924447)** Detailed doc for assembling, teleoperate, dataset, train, deploy. Verified by Seed Studio and 5 global hackathon players.
- **[Discord](https://discord.gg/q8Dzzpym3f):** Join the `LeRobot` server to discuss with the community.
- **[X](https://x.com/LeRobotHF):** Follow us on X to stay up-to-date with the latest developments.
- **[Robot Learning Tutorial](https://huggingface.co/spaces/lerobot/robot-learning-tutorial):** A free, hands-on course to learn robot learning using LeRobot.
- **[T-Shirt Folding Experiment](https://huggingface.co/spaces/lerobot/robot-folding):** An end-to-end demonstration of folding t-shirts with LeRobot.
- **[LeLab](https://github.com/huggingface/leLab):** A web interface for LeRobot — teleoperate, calibrate, record datasets, replay, and train your SO arm from the browser, no CLI required.
