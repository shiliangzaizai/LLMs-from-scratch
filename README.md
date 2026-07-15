# 从零构建大模型（LLMs from Scratch）· 中文导读

> 本仓库是 Sebastian Raschka 著作 **《Build a Large Language Model (From Scratch)》** 的**官方配套代码库**：从零开始、逐步手写一个类 GPT 的大语言模型（LLM），覆盖数据处理、注意力机制、GPT 架构、预训练、微调全流程。
>
> 配套书：<https://amzn.to/4fqvn0D> ｜ 作者博客导读：<https://sebastianraschka.com/blog/2025/reading-books.html>
>
> 本文件为**中文导读版**，便于快速了解项目结构与章节地图；**完整英文说明、环境配置与逐章链接以 [README.en.md](README.en.md) 为准**。

---

## 1. 这个项目能学到什么

不调用任何现成 LLM 框架的"黑盒"，而是**从底层张量运算写起**，亲手实现一个 GPT 类模型：

- 理解 LLM 的内部工作原理（从内到外）；
- 掌握分词（BPE）、注意力机制、Transformer 解码器架构；
- 跑通"预训练 → 分类微调 → 指令微调"的完整训练链路；
- 配套练习 + 视频课，适合系统学习。

---

## 2. 章节地图（核心代码索引）

| 章节 | 主题 | 核心代码（快速入口） | 全部代码 |
|---|---|---|---|
| Setup | 环境搭建建议 | — | [setup](setup) |
| **Ch 1** | 理解大语言模型 | 无代码（概念章） | — |
| **Ch 2** | 文本数据处理 | [ch02.ipynb](ch02/01_main-chapter-code/ch02.ipynb)、[dataloader.ipynb](ch02/01_main-chapter-code/dataloader.ipynb)、[exercise-solutions.ipynb](ch02/01_main-chapter-code/exercise-solutions.ipynb) | [./ch02](./ch02) |
| **Ch 3** | 编写注意力机制 | [ch03.ipynb](ch03/01_main-chapter-code/ch03.ipynb)、[multihead-attention.ipynb](ch03/01_main-chapter-code/multihead-attention.ipynb)、[exercise-solutions.ipynb](ch03/01_main-chapter-code/exercise-solutions.ipynb) | [./ch03](./ch03) |
| **Ch 4** | 从零实现 GPT 模型 | [ch04.ipynb](ch04/01_main-chapter-code/ch04.ipynb)、[gpt.py](ch04/01_main-chapter-code/gpt.py)、[exercise-solutions.ipynb](ch04/01_main-chapter-code/exercise-solutions.ipynb) | [./ch04](./ch04) |
| **Ch 5** | 在无标注数据上预训练 | [ch05.ipynb](ch05/01_main-chapter-code/ch05.ipynb)、[gpt_train.py](ch05/01_main-chapter-code/gpt_train.py)、[gpt_generate.py](ch05/01_main-chapter-code/gpt_generate.py)、[exercise-solutions.ipynb](ch05/01_main-chapter-code/exercise-solutions.ipynb) | [./ch05](./ch05) |
| **Ch 6** | 微调做文本分类 | [ch06.ipynb](ch06/01_main-chapter-code/ch06.ipynb)、[gpt_class_finetune.py](ch06/01_main-chapter-code/gpt_class_finetune.py)、[exercise-solutions.ipynb](ch06/01_main-chapter-code/exercise-solutions.ipynb) | [./ch06](./ch06) |
| **Ch 7** | 微调让模型遵循指令 | [ch07.ipynb](ch07/01_main-chapter-code/ch07.ipynb)、[gpt_instruction_finetuning.py](ch07/01_main-chapter-code/gpt_instruction_finetuning.py)、[ollama_evaluate.py](ch07/01_main-chapter-code/ollama_evaluate.py)、[exercise-solutions.ipynb](ch07/01_main-chapter-code/exercise-solutions.ipynb) | [./ch07](./ch07) |
| **附录 A** | PyTorch 入门 | [code-part1.ipynb](appendix-A/01_main-chapter-code/code-part1.ipynb)、[code-part2.ipynb](appendix-A/01_main-chapter-code/code-part2.ipynb)、[DDP-script.py](appendix-A/01_main-chapter-code/DDP-script.py) | [./appendix-A](./appendix-A) |
| **附录 B** | 参考文献与延伸阅读 | 无代码 | [./appendix-B](./appendix-B) |
| **附录 C** | 练习解答 | [解答列表](appendix-C) | [./appendix-C](./appendix-C) |
| **附录 D** | 给训练循环加"花活" | [appendix-D.ipynb](appendix-D/01_main-chapter-code/appendix-D.ipynb) | [./appendix-D](./appendix-D) |
| **附录 E** | 用 LoRA 做参数高效微调 | [appendix-E.ipynb](appendix-E/01_main-chapter-code/appendix-E.ipynb) | [./appendix-E](./appendix-E) |

> 每章目录（如 `ch02/`）下通常包含：`01_main-chapter-code/`（主代码 notebook）、`0x_bonus_*/`（拓展材料）、练习解答等。

---

## 3. 环境搭建

`setup/` 目录提供多种环境方案：

- [01_optional-python-setup-preferences](setup/01_optional-python-setup-preferences) — Python 环境偏好（可选）
- [02_installing-python-libraries](setup/02_installing-python-libraries) — 安装 Python 依赖库
- [03_optional-docker-environment](setup/03_optional-docker-environment) — Docker 环境（可选）
- [04_optional-aws-sagemaker-notebook](setup/04_optional-aws-sagemaker-notebook) — AWS SageMaker（可选）

依赖声明见根目录 `requirements.txt`、`pyproject.toml`、`pixi.toml`。

---

## 4. 硬件要求

- 主章节代码设计在**普通笔记本**上即可在合理时间内运行，**无需专用硬件**；
- 代码会自动检测并使用可用的 GPU；
- 详细建议见 [setup README](setup/README.md)。

---

## 5. 附加学习资源（详见 README.en.md）

- **视频课**：约 17 小时 15 分钟的配套视频课，按书本章节逐章编码（Manning LiveVideo）。
- **练习**：每章含若干练习，解答汇总于附录 C，对应 notebook 在各章目录。
- **自测 PDF**：可下载约 170 页《Test Yourself On Build a Large Language Model (From Scratch)》，每章约 30 道测验题。
- **Bonus 材料**：各章附赠 notebook（如从零写 BPE 分词器、高效多头注意力对比、FLOPs 分析、KV Cache、GQA/MLA/SWA 等注意力变体）。
- **推理专题**：`reasoning-from-scratch/` 目录含推理相关代码。

---

## 6. 如何使用本仓库

1. 先读 [setup](setup) 配好环境；
2. 按 Ch 1 → Ch 7 顺序打开对应 `ch0X/01_main-chapter-code/*.ipynb` 边读边跑；
3. 卡住时查附录 C（练习解答）与 Bonus 材料；
4. 想深入 PyTorch 或 LoRA 看附录 A / E。

---

> 本中文 README 为导读；**逐章完整说明、链接与最新更新以 [README.en.md](README.en.md) 为准**。许可证见 `LICENSE.txt`。
