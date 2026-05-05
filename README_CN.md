# AI Research Skills Library

> **全面的开源 AI 研究技能库，赋能 AI Agent 自主完成 AI 研究——从想法到论文。99 个技能，22 个类别。**

<p align="center">
  <a href="https://opensource.org/licenses/MIT"><img src="https://img.shields.io/badge/License-MIT-yellow.svg" alt="License: MIT"></a>
  <a href="https://github.com/qcmuu/AI-Research-Skills"><img src="https://img.shields.io/badge/GitHub-Repo-blue.svg?logo=github" alt="GitHub"></a>
</p>

[English](README.md) | 中文

---

## 目录

- [什么是 AI Research Skills](#什么是-ai-research-skills)
- [技能总览（99 个）](#技能总览99-个)
- [技能结构](#技能结构)
- [快速开始](#快速开始)
- [使用场景](#使用场景)
- [仓库结构](#仓库结构)
- [贡献指南](#贡献指南)
- [许可证](#许可证)
- [致谢](#致谢)

## 什么是 AI Research Skills

每个技能是一个独立的专家级指导包（200-500 行），包含真实代码示例、故障排除指南和生产就绪的工作流。技能专为 AI 编程助手（Claude Code、Cursor、OpenCode 等）设计，赋予它们在特定 AI 研究工具和框架上的深度专业能力。

覆盖 AI 研究全生命周期：

- **选题** → 用结构化框架头脑风暴研究方向
- **架构** → 设计和理解模型架构
- **数据** → 策划、分词、处理训练数据集
- **训练** → 微调、分布式训练、后训练（RLHF/DPO/GRPO）
- **优化** → 量化、剪枝、蒸馏、优化模型
- **评估** → 使用标准和自定义基准进行评测
- **推理部署** → vLLM、TensorRT-LLM、llama.cpp、SGLang、Ollama
- **Agent 与 RAG** → 构建自主代理和检索增强系统
- **多模态** → 视觉、语音、机器人模型
- **论文写作** → 撰写论文、绘图、做报告

**Autoresearch** 技能可自主编排整个生命周期，按需调用各领域技能。

## 技能总览（99 个）

| 类别 | 数量 | 技能 |
|----------|---|--------|
| **自主研究** | 1 | 自主研究编排 |
| **模型架构** | 5 | LitGPT、Mamba、NanoGPT、RWKV、TorchTitan |
| **分词** | 2 | HuggingFace Tokenizers、SentencePiece |
| **微调** | 4 | Axolotl、LLaMA-Factory、PEFT、Unsloth |
| **可解释性** | 4 | TransformerLens、SAELens、pyvene、nnsight |
| **数据处理** | 2 | Ray Data、NeMo Curator |
| **后训练** | 8 | TRL、GRPO、OpenRLHF、SimPO、verl、slime、miles、torchforge |
| **安全对齐** | 4 | Constitutional AI、LlamaGuard、NeMo Guardrails、Prompt Guard |
| **分布式训练** | 6 | Megatron-Core、DeepSpeed、FSDP、Accelerate、Lightning、Ray Train |
| **基础设施** | 3 | Modal、SkyPilot、Lambda Labs |
| **优化** | 7 | Flash Attention、bitsandbytes、GPTQ、AWQ、HQQ、GGUF、ML Training Recipes |
| **评估** | 3 | lm-eval-harness、BigCode、NeMo Evaluator |
| **推理部署** | 5 | vLLM、TensorRT-LLM、llama.cpp、SGLang、Ollama |
| **MLOps** | 4 | W&B、MLflow、TensorBoard、SwanLab |
| **Agent** | 6 | LangChain、LlamaIndex、CrewAI、AutoGPT、A-Evolve、OpenHands |
| **RAG** | 6 | Chroma、FAISS、Sentence Transformers、Pinecone、Qdrant、Haystack |
| **提示工程** | 4 | DSPy、Instructor、Guidance、Outlines |
| **可观测性** | 2 | LangSmith、Phoenix |
| **多模态** | 10 | CLIP、Whisper、LLaVA、Stable Diffusion、SAM、BLIP-2、AudioCraft、Cosmos Policy、OpenPI、OpenVLA-OFT |
| **前沿技术** | 7 | MoE、模型合并、长上下文、推测解码、知识蒸馏、模型剪枝、Mergekit |
| **论文写作** | 4 | ML 论文写作、学术绘图、会议报告、系统论文写作 |
| **研究选题** | 2 | 研究头脑风暴、创新思维 |

<details>
<summary><b>查看全部 99 个技能详情</b></summary>

### 自主研究（1 个技能）
- **[Autoresearch](0-autoresearch-skill/)** - 使用双循环架构（内部优化 + 外部综合）的自主研究编排。管理从文献调研到论文写作的完整生命周期，自动路由到所有领域技能。

### 模型架构（5 个技能）
- **[LitGPT](01-model-architecture/litgpt/)** - Lightning AI 的 20+ 种 LLM 实现，含生产训练方案
- **[Mamba](01-model-architecture/mamba/)** - O(n) 复杂度的状态空间模型，比 Transformer 快 5 倍
- **[RWKV](01-model-architecture/rwkv/)** - RNN+Transformer 混合架构，无限上下文，Linux 基金会项目
- **[NanoGPT](01-model-architecture/nanogpt/)** - Karpathy 用约 300 行代码实现的教学版 GPT
- **[TorchTitan](01-model-architecture/torchtitan/)** - PyTorch 原生分布式训练，支持 Llama 3.1 的 4D 并行

### 分词（2 个技能）
- **[HuggingFace Tokenizers](02-tokenization/huggingface-tokenizers/)** - Rust 实现，<20s/GB，支持 BPE/WordPiece/Unigram
- **[SentencePiece](02-tokenization/sentencepiece/)** - 语言无关，50k 句/秒，T5/ALBERT 使用

### 微调（4 个技能）
- **[Axolotl](03-fine-tuning/axolotl/)** - 基于 YAML 的微调，支持 100+ 模型
- **[LLaMA-Factory](03-fine-tuning/llama-factory/)** - WebUI 无代码微调
- **[Unsloth](03-fine-tuning/unsloth/)** - 2 倍速 QLoRA 微调
- **[PEFT](03-fine-tuning/peft/)** - 参数高效微调，支持 LoRA、QLoRA、DoRA 等 25+ 方法

### 可解释性分析（4 个技能）
- **[TransformerLens](04-mechanistic-interpretability/transformer-lens/)** - HookPoints、激活缓存、回路分析
- **[SAELens](04-mechanistic-interpretability/saelens/)** - 稀疏自编码器训练与分析，用于特征发现
- **[pyvene](04-mechanistic-interpretability/pyvene/)** - 斯坦福因果干预库，声明式配置
- **[nnsight](04-mechanistic-interpretability/nnsight/)** - 通过 NDIF 远程可解释性分析，可在 70B+ 模型上运行实验

### 数据处理（2 个技能）
- **[Ray Data](05-data-processing/ray-data/)** - 分布式 ML 数据处理，流式执行，GPU 支持
- **[NeMo Curator](05-data-processing/nemo-curator/)** - GPU 加速数据策划，去重速度快 16 倍

### 后训练（8 个技能）
- **[TRL Fine-Tuning](06-post-training/trl-fine-tuning/)** - Transformer 强化学习
- **[GRPO-RL-Training](06-post-training/grpo-rl-training/)** - 使用 TRL 的组相对策略优化
- **[OpenRLHF](06-post-training/openrlhf/)** - 基于 Ray + vLLM 的完整 RLHF 流水线
- **[SimPO](06-post-training/simpo/)** - 简单偏好优化，无需参考模型
- **[verl](06-post-training/verl/)** - 字节跳动 HybridFlow RL 框架，FSDP/Megatron + vLLM/SGLang 后端
- **[slime](06-post-training/slime/)** - 清华 THUDM 的 Megatron+SGLang 框架，支撑 GLM-4.x 模型
- **[miles](06-post-training/miles/)** - slime 企业分支，支持 FP8、INT4、MoE 推测 RL
- **[torchforge](06-post-training/torchforge/)** - Meta 的 PyTorch 原生 RL，集成 Monarch+TorchTitan+vLLM

### 安全与对齐（4 个技能）
- **[Constitutional AI](07-safety-alignment/constitutional-ai/)** - 基于原则的 AI 自我改进
- **[LlamaGuard](07-safety-alignment/llamaguard/)** - LLM 输入/输出安全分类器
- **[NeMo Guardrails](07-safety-alignment/nemo-guardrails/)** - 使用 Colang 的可编程护栏
- **[Prompt Guard](07-safety-alignment/prompt-guard/)** - Meta 的 86M 提示注入和越狱检测器，99%+ TPR，<2ms GPU 延迟

### 分布式训练（6 个技能）
- **[Megatron-Core](08-distributed-training/megatron-core/)** - NVIDIA 框架，在 H100 上以 47% MFU 训练 2B-462B 参数模型
- **[DeepSpeed](08-distributed-training/deepspeed/)** - 微软 ZeRO 优化
- **[PyTorch FSDP2](08-distributed-training/pytorch-fsdp2/)** - 全分片数据并行 v2，支持 `fully_shard` 和 DTensor
- **[Accelerate](08-distributed-training/accelerate/)** - HuggingFace 4 行代码分布式训练 API
- **[PyTorch Lightning](08-distributed-training/pytorch-lightning/)** - 高级训练框架，含 Trainer 类
- **[Ray Train](08-distributed-training/ray-train/)** - 多节点编排和超参调优

### 基础设施（3 个技能）
- **[Modal](09-infrastructure/modal/)** - 无服务器 GPU 云，Python 原生 API，T4-H200 按需使用
- **[SkyPilot](09-infrastructure/skypilot/)** - 跨 20+ 云服务商的多云编排，支持 Spot 实例恢复
- **[Lambda Labs](09-infrastructure/lambda-labs/)** - 预留/按需 GPU 云，H100/A100

### 优化（7 个技能）
- **[Flash Attention](10-optimization/flash-attention/)** - 2-4 倍速注意力机制，内存高效
- **[bitsandbytes](10-optimization/bitsandbytes/)** - 8-bit/4-bit 量化，内存减少 50-75%
- **[GPTQ](10-optimization/gptq/)** - 4-bit 训练后量化，精度损失 <2%
- **[AWQ](10-optimization/awq/)** - 激活感知权重量化，4-bit 精度损失极小
- **[HQQ](10-optimization/hqq/)** - 半二次量化，无需校准数据
- **[GGUF](10-optimization/gguf/)** - llama.cpp 量化格式，K-quant 方法，CPU/Metal 推理
- **[ML Training Recipes](10-optimization/ml-training-recipes/)** - 生产级训练方案和最佳实践

### 评估（3 个技能）
- **[lm-evaluation-harness](11-evaluation/lm-evaluation-harness/)** - EleutherAI 的 LLM 基准评测标准，60+ 任务
- **[BigCode Evaluation Harness](11-evaluation/bigcode-evaluation-harness/)** - 代码模型评测，HumanEval、MBPP、MultiPL-E
- **[NeMo Evaluator](11-evaluation/nemo-evaluator/)** - NVIDIA 企业级评测平台，18+ 评测框架的 100+ 基准

### 推理部署（5 个技能）
- **[vLLM](12-inference-serving/vllm/)** - 基于 PagedAttention 的高吞吐 LLM 推理
- **[TensorRT-LLM](12-inference-serving/tensorrt-llm/)** - NVIDIA 最快推理，24k tok/s，FP8/INT4 量化
- **[llama.cpp](12-inference-serving/llama-cpp/)** - CPU/Apple Silicon 推理，GGUF 量化
- **[SGLang](12-inference-serving/sglang/)** - 结构化生成，RadixAttention，Agent 场景快 5-10 倍
- **[Ollama](12-inference-serving/ollama/)** - 一条命令本地运行 LLM，多模态支持

### MLOps（4 个技能）
- **[Weights & Biases](13-mlops/weights-and-biases/)** - 实验追踪、超参扫描、模型注册
- **[MLflow](13-mlops/mlflow/)** - 模型注册、追踪、部署、自动日志
- **[TensorBoard](13-mlops/tensorboard/)** - 可视化、性能分析、嵌入、标量/图像
- **[SwanLab](13-mlops/swanlab/)** - 实验追踪和可视化

### Agent（6 个技能）
- **[LangChain](14-agents/langchain/)** - 最流行的 Agent 框架，500+ 集成，ReAct 模式
- **[LlamaIndex](14-agents/llamaindex/)** - LLM 应用数据框架，300+ 连接器，聚焦 RAG
- **[CrewAI](14-agents/crewai/)** - 多 Agent 编排，基于角色的协作
- **[AutoGPT](14-agents/autogpt/)** - 自主 AI Agent 平台，可视化工作流构建器
- **[A-Evolve](14-agents/a-evolve/)** - Agent 演化和技能获取
- **[OpenHands](14-agents/openhands/)** - 自主软件工程 Agent

### RAG（6 个技能）
- **[Chroma](15-rag/chroma/)** - 开源向量数据库，本地/云端
- **[FAISS](15-rag/faiss/)** - Facebook 相似度搜索，十亿级，GPU 加速
- **[Sentence Transformers](15-rag/sentence-transformers/)** - 5000+ 嵌入模型，多语言
- **[Pinecone](15-rag/pinecone/)** - 托管向量数据库，自动扩缩，<100ms 延迟
- **[Qdrant](15-rag/qdrant/)** - 高性能向量搜索，Rust 驱动，混合搜索
- **[Haystack](15-rag/haystack/)** - deepset 生产级 NLP 和 RAG 框架，模块化流水线架构，100+ 集成

### 提示工程（4 个技能）
- **[DSPy](16-prompt-engineering/dspy/)** - 声明式提示编程，含优化器
- **[Instructor](16-prompt-engineering/instructor/)** - 使用 Pydantic 验证的结构化 LLM 输出
- **[Guidance](16-prompt-engineering/guidance/)** - 使用正则/语法的约束生成
- **[Outlines](16-prompt-engineering/outlines/)** - 基于 FSM 的结构化文本，零开销

### 可观测性（2 个技能）
- **[LangSmith](17-observability/langsmith/)** - LLM 可观测性、追踪、评估、监控
- **[Phoenix](17-observability/phoenix/)** - 开源 AI 可观测性，OpenTelemetry 追踪

### 多模态（10 个技能）
- **[CLIP](18-multimodal/clip/)** - OpenAI 视觉-语言模型，零样本分类
- **[Whisper](18-multimodal/whisper/)** - 鲁棒语音识别，99 种语言
- **[LLaVA](18-multimodal/llava/)** - 视觉-语言助手，GPT-4V 水平
- **[Stable Diffusion](18-multimodal/stable-diffusion/)** - 通过 Diffusers 的文生图，SDXL、ControlNet
- **[Segment Anything](18-multimodal/segment-anything/)** - Meta SAM，零样本图像分割
- **[BLIP-2](18-multimodal/blip-2/)** - Q-Former 视觉-语言预训练，图像描述、VQA
- **[AudioCraft](18-multimodal/audiocraft/)** - Meta MusicGen/AudioGen，文生音乐和音效
- **[Cosmos Policy](18-multimodal/cosmos-policy/)** - NVIDIA Cosmos 世界基础模型，面向物理 AI
- **[OpenPI](18-multimodal/openpi/)** - 开源视觉-语言-动作模型，面向机器人
- **[OpenVLA-OFT](18-multimodal/openvla-oft/)** - 开源视觉-语言-动作模型，最优微调

### 前沿技术（7 个技能）
- **[MoE 训练](19-emerging-techniques/moe-training/)** - 使用 DeepSpeed 的混合专家训练，Mixtral 8x7B
- **[模型合并](19-emerging-techniques/model-merging/)** - TIES、DARE、SLERP 模型合并
- **[长上下文](19-emerging-techniques/long-context/)** - RoPE、YaRN、ALiBi 扩展上下文窗口
- **[推测解码](19-emerging-techniques/speculative-decoding/)** - Medusa、Lookahead 1.5-3.6 倍加速推理
- **[知识蒸馏](19-emerging-techniques/knowledge-distillation/)** - 70B→7B 模型压缩
- **[模型剪枝](19-emerging-techniques/model-pruning/)** - Wanda、SparseGPT 50% 稀疏化
- **[Mergekit](19-emerging-techniques/mergekit/)** - 无需 GPU 合并微调后的 LLM；SLERP、TIES、DARE、Frankenmerging

### 论文写作（4 个技能）
- **[ML 论文写作](20-ml-paper-writing/ml-paper-writing/)** - 为 NeurIPS、ICML、ICLR、ACL、AAAI、COLM 撰写可发表论文
- **[学术绘图](20-ml-paper-writing/academic-plotting/)** - matplotlib/seaborn 出版级图表和 Gemini AI 架构图
- **[会议报告](20-ml-paper-writing/presenting-conference-talks/)** - 在 ML 会议上展示研究成果
- **[系统论文写作](20-ml-paper-writing/systems-paper-writing/)** - 撰写系统导向的 ML 研究论文

### 研究选题（2 个技能）
- **[研究头脑风暴](21-research-ideation/brainstorming-research-ideas/)** - 高影响力研究方向的结构化创意框架
- **[创新思维](21-research-ideation/creative-thinking-for-research/)** - 认知科学框架，产生真正新颖的研究想法

</details>

## 技能结构

每个技能遵循标准化格式：

```
skill-name/
├── SKILL.md                    # 主要指导（200-500 行，含 YAML 前置元数据）
├── references/                 # 深度文档（目标 300KB+）
│   ├── README.md               # 来自官方文档
│   ├── api.md                  # API 参考
│   ├── tutorials.md            # 分步指南
│   ├── issues.md               # 真实 GitHub 问题与解决方案
│   └── releases.md             # 版本历史
├── scripts/                    # 辅助脚本（可选）
└── templates/                  # 代码模板（可选）
```

## 快速开始

### 配合 Claude Code 使用

1. 克隆仓库：
```bash
git clone https://github.com/qcmuu/AI-Research-Skills.git
```

2. 指向相关技能目录，例如：
```
Read the skill at 03-fine-tuning/unsloth/SKILL.md and help me fine-tune Llama 3 on my dataset.
```

### 配合任意 AI 编程助手使用

将相关的 `SKILL.md` 和 `references/` 复制到项目中，或直接让助手读取：

```
Read ./06-post-training/grpo-rl-training/SKILL.md and set up a GRPO training pipeline.
```

### 浏览技能

探索目录树——每个编号类别包含技能文件夹和完整文档：

```bash
ls 12-inference-serving/    # vLLM、TensorRT-LLM、llama.cpp、SGLang、Ollama
ls 08-distributed-training/  # DeepSpeed、FSDP、Accelerate、Megatron-Core 等
```

## 使用场景

| 角色 | 示例任务 | 技能 |
|------|---------|------|
| **研究员** | 用自定义数据微调 Llama 3 | `03-fine-tuning/axolotl/` |
| **ML 工程师** | 优化推理延迟 | `12-inference-serving/vllm/` |
| **学生** | 学习 Transformer 原理 | `01-model-architecture/litgpt/` |
| **团队** | 将训练扩展到 100 个 GPU | `08-distributed-training/deepspeed/` |
| **Agent 构建者** | 构建 RAG 流水线 | `15-rag/haystack/` |
| **机器人研究员** | 训练视觉-语言-动作模型 | `18-multimodal/openpi/` |

## 仓库结构

```
AI-Research-Skills/
├── README.md
├── README_CN.md
├── CONTRIBUTING.md
├── 0-autoresearch-skill/        (1 个技能)
├── 01-model-architecture/       (5 个技能)
├── 02-tokenization/             (2 个技能)
├── 03-fine-tuning/              (4 个技能)
├── 04-mechanistic-interpretability/ (4 个技能)
├── 05-data-processing/          (2 个技能)
├── 06-post-training/            (8 个技能)
├── 07-safety-alignment/         (4 个技能)
├── 08-distributed-training/     (6 个技能)
├── 09-infrastructure/           (3 个技能)
├── 10-optimization/             (7 个技能)
├── 11-evaluation/               (3 个技能)
├── 12-inference-serving/        (5 个技能)
├── 13-mlops/                    (4 个技能)
├── 14-agents/                   (6 个技能)
├── 15-rag/                      (6 个技能)
├── 16-prompt-engineering/       (4 个技能)
├── 17-observability/            (2 个技能)
├── 18-multimodal/               (10 个技能)
├── 19-emerging-techniques/      (7 个技能)
├── 20-ml-paper-writing/         (4 个技能)
└── 21-research-ideation/        (2 个技能)
```

## 贡献指南

欢迎贡献！详见 [CONTRIBUTING.md](CONTRIBUTING.md)，包含：

- 添加新技能
- 改进现有技能
- 质量标准和最佳实践
- 提交流程

每个技能必须遵循[质量标准](CONTRIBUTING.md)，包括 YAML 前置元数据、200-500 行的 SKILL.md 和参考文档。

## 许可证

MIT 许可证 - 详见 [LICENSE](LICENSE)。

个别技能可能引用不同许可证的库，使用前请检查各项目的许可证。

## 致谢

本库基于众多开源项目和 AI 研究社区的工作：

- **[Orchestra Research](https://github.com/Orchestra-Research/AI-Research-SKILLs)** - 本项目 fork 自的原始库（87 个技能）
- **[Claude Code](https://www.claude.com/product/claude-code)** - AI 配对编程
- EleutherAI、HuggingFace、NVIDIA、Lightning AI、Meta AI、Anthropic
- 所有维护优秀文档的研究者
