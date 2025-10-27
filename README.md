# DISCLAIMER: This is NOT the official repository of minimind! please refer to https://github.com/jingyaogong/minimind/ to find official website.

<div align="center">

![logo](./images/logo.png)

</div>

<div align="center">

![visitors](https://visitor-badge.laobi.icu/badge?page_id=jingyaogong/minimind)
[![GitHub Repo stars](https://img.shields.io/github/stars/jingyaogong/minimind?style=social)](https://github.com/jingyaogong/minimind/stargazers)
[![GitHub Code License](https://img.shields.io/github/license/jingyaogong/minimind)](LICENSE)
[![GitHub last commit](https://img.shields.io/github/last-commit/jingyaogong/minimind)](https://github.com/jingyaogong/minimind/commits/master)
[![GitHub pull request](https://img.shields.io/badge/PRs-welcome-blue)](https://github.com/jingyaogong/minimind/pulls)
[![Collection](https://img.shields.io/badge/🤗-MiniMind%20%20Collection-blue)](https://huggingface.co/collections/jingyaogong/minimind-66caf8d999f5c7fa64f399e5)


</div>

<div align="center">

![GitHub Trend](https://trendshift.io/api/badge/repositories/12586)

</div>

<div align="center">
  <h3>"The Simplest Path is the Greatest"</h3>
</div>

* This open-source project aims to train a super-small language model **MiniMind** with only 3 RMB cost and 2 hours,
  starting completely from scratch.
* The **MiniMind** series is extremely lightweight, with the smallest version being $\frac{1}{7000}$ the size of GPT-3,
  making it possible to train quickly on even the most ordinary personal GPUs.
* The project also open-sources the minimalist structure of the large model, including extensions for shared mixed
  experts (MoE), dataset cleaning, pretraining, supervised fine-tuning (SFT), LoRA fine-tuning, direct preference
  optimization (DPO) algorithms, reinforcement learning from AI feedback (RLAIF: PPO/GRPO/SPO), and model distillation 
  algorithms, along with the full code of the entire process.
* **MiniMind** also expands into vision multimodal VLM: [MiniMind-V](https://github.com/jingyaogong/minimind-v).
* All core algorithm code is reconstructed from scratch using native PyTorch! It does not rely on abstract interfaces
  provided by third-party libraries.
* This is not only a full-stage open-source reproduction of a large language model but also a tutorial for beginners in
  LLM.
* We hope this project will serve as an inspiring example for everyone, helping to enjoy the fun of creation and
  promoting the progress of the wider AI community!

> To avoid misunderstanding, the "2 hours" test is based on NVIDIA 3090 hardware (single GPU), and the "3 RMB" refers to the GPU server rental cost. Details of the specifications can be found below.

<div align="center">
  <table>
    <tr>
      <td align="center">
        <a href="https://huggingface.co/collections/jingyaogong/minimind-66caf8d999f5c7fa64f399e5" style="text-decoration: none;">
          <img src="./images/and_huggingface.png" alt="Hugging Face Logo" style="vertical-align: middle; width: auto; max-width: 100%;" />
        </a>
      </td>
      <td align="center">
        <a href="https://www.modelscope.cn/profile/gongjy" style="text-decoration: none;">
          <img src="./images/and_modelscope.png" alt="ModelScope Logo" style="vertical-align: middle; width: auto; max-width: 100%;" />
        </a>
      </td>
    </tr>
  </table>
</div></div>


# 📌 Introduction

The emergence of Large Language Models (LLMs) has sparked unprecedented global attention to AI. 
Whether it's ChatGPT, DeepSeek, or Qwen, they all demonstrate stunning performance that is awe-inspiring.
However, with their massive scale of tens of billions of parameters, they are not only difficult to train on personal devices but nearly impossible to deploy.
Opening the "black box" of large models to explore their internal mechanisms is truly thrilling!
Unfortunately, 99% of exploration can only stop at using techniques like LoRA to perform minor fine-tuning on existing large models to learn new instructions or tasks.
This is like teaching Newton how to use a 21st-century smartphone—while interesting, it completely deviates from the original intent of understanding the essence of physics.
Meanwhile, third-party large model frameworks and toolkits, such as transformers+trl, expose only highly abstract interfaces.
With just 10 lines of code, you can complete the entire workflow of "loading model + loading dataset + inference + reinforcement learning."
While such efficient packaging is convenient, it also acts like a high-speed spacecraft, isolating developers from underlying implementations and hindering deep exploration of LLM core code.
Yet, "building a plane with Lego is far more exciting than flying in first class!"
What's worse, the internet is flooded with expensive courses and marketing accounts selling AI tutorials with countless flaws and superficial understanding.
For this reason, this project's original intention is to lower the barrier to entry for LLM learning, allowing everyone to start by understanding every line of code,
to personally train an extremely small language model from scratch. Yes, from **training from scratch**, not just **inference**!
With less than 3 RMB in server costs, you can personally experience the entire process of building a language model from 0 to 1.
Let's enjoy the fun of creation together!

> [!NOTE]
> (As of 2025-10) The MiniMind series has completed pretraining of multiple model variants, with the smallest being only 25.8M (0.02B), capable of fluent conversation!

<details style="color:rgb(128,128,128)">
<summary>Models List</summary>

| Model (Size)           | Inference Memory (Approx) | Release    | 
|------------------------|---------------------------|------------|
| MiniMind2-small (26M)  | 0.5 GB                    | 2025.04.26 |
| MiniMind2-MoE (145M)   | 1.0 GB                    | 2025.04.26 |
| MiniMind2 (104M)       | 1.0 GB                    | 2025.04.26 |
| minimind-v1-small (26M)| 0.5 GB                    | 2024.08.28 |
| minimind-v1-moe (4×26M)| 1.0 GB                    | 2024.09.17 |
| minimind-v1 (108M)     | 1.0 GB                    | 2024.09.01 |

</details>

**Project Includes**

- Complete code for MiniMind-LLM structure (Dense + MoE models).
- Detailed training code for Tokenizer.
- Complete training code for Pretrain, SFT, LoRA, RLHF-DPO, RLAIF (PPO/GRPO/SPO), and model distillation.
- Collected, distilled, organized and cleaned high-quality datasets for all stages, all open-sourced.
- Implemented from scratch: pretraining, instruction fine-tuning, LoRA, DPO/PPO/GRPO/SPO reinforcement learning, and white-box model distillation. Core algorithms barely depend on third-party framework encapsulation, all open-sourced.
- Compatible with mainstream third-party frameworks like `transformers`, `trl`, `peft`.
- Training supports single GPU, multiple GPUs on a single machine (DDP, DeepSpeed), supports wandb/swanlab visualization of training process. Supports dynamic training start/stop.
- Model testing on third-party evaluation leaderboards (C-Eval, C-MMLU, OpenBookQA, etc.), supports YaRN algorithm for RoPE long-text extrapolation.
- Implements an extremely simple OpenAI API-compliant server, convenient for integration with third-party ChatUI (FastGPT, Open-WebUI, etc.).
- Implements the simplest chat WebUI frontend based on streamlit.
- Fully compatible with popular community inference engines `llama.cpp`, `vllm`, `ollama` or training framework `Llama-Factory`.
- Reproduced (distilled/RL) DeepSeek-R1 reasoning model as MiniMind-Reason model, with **data + models** fully open-sourced!

We hope this open-source project can help LLM beginners get started quickly!

### 👉**Update Log**

<details close> 
<summary> <b>2025-10-24 (newest🎉)</b> </summary>

- 🔥 Added RLAIF training algorithms: PPO, GRPO, SPO (native implementation from scratch)
- Added checkpoint resume training: supports automatic training recovery, cross-GPU recovery, wandb continuity
- Added RLAIF dataset: rlaif-mini.jsonl (randomly sampled 10,000 entries from SFT data); simplified DPO dataset with Chinese data
- Added YaRN algorithm: supports RoPE long-text extrapolation, improving long sequence handling capability
- Adaptive Thinking: Reason model can optionally enable thinking chain
- chat_template fully supports Tool Calling and Reasoning tags (`<tool_call>`, `<think>`, etc.)
- Added complete RLAIF chapter, training curve comparison, algorithm principle explanations
- [SwanLab](https://swanlab.cn/) replaces WandB (friendly for domestic access, fully compatible API)
- Code standardization & fixed some known bugs

</details>

<details close> 
<summary> <b>2025-04-26</b> </summary>

- Important update
- For compatibility needs, you can visit [🔗old repository content🔗](https://github.com/jingyaogong/minimind/tree/7da201a944a90ed49daef8a0265c959288dff83a).
- MiniMind model parameters completely renamed, aligned with Transformers library models (unified naming).
- generate method refactored, inheriting from GenerationMixin class.
- 🔥 Supports popular third-party ecosystems like llama.cpp, vllm, ollama.
- Standardized code and directory structure.
- Modified vocabulary `<s></s>`->`<|im_start|><|im_end|>`

```text
To be compatible with third-party inference frameworks llama.cpp and vllm, this update requires some observable costs.
This update no longer supports "directly" loading old models before 25-04-26 for inference.
Due to differences in Llama's positional encoding compared to minimind, there are differences in QK values after mapping Llama models.
MiniMind2 series old models have been recovered through weight mapping and (fine-tuning training) QKVO linear layer calibration.
After this update, maintenance of the entire minimind-v1 series will be abandoned and removed from the repository.
```

</details>

<details close> 
<summary> <b>2025-02-09</b> </summary>

- Major update since release, Release MiniMind2 Series.
- Code almost completely refactored, using cleaner and more unified structure.
  For compatibility with old code, you can visit [🔗old repository content🔗](https://github.com/jingyaogong/minimind/tree/6e9cd28ef9b34a0a10afbdf6f59e65cb6e628efb).
- Eliminated data preprocessing steps. Unified dataset format, switched to `jsonl` format to avoid dataset download confusion.
- MiniMind2 series shows significant improvement compared to MiniMind-V1.
- Minor improvements: {more standard kv-cache writing, MoE load balancing loss considered, etc.}
- Provides training solutions for model migration to private datasets (medical models, self-awareness examples).
- Streamlined pretraining dataset and significantly improved pretraining data quality, greatly reducing time for quick personal training, single 3090 GPU can reproduce in 2 hours!
- Updates: LoRA fine-tuning separated from peft packaging, implemented from scratch; DPO algorithm implemented from scratch using native PyTorch; white-box model distillation native implementation.
- MiniMind2-DeepSeek-R1 series distilled models born!
- MiniMind2 now has some English ability!
- Updated MiniMind2 and third-party model performance results based on more large model leaderboard tests.

</details>

<details close> 
<summary> <b>2024-10-05</b> </summary>

- Extended MiniMind with multimodal capabilities---Vision
- Check out the twin project [minimind-v](https://github.com/jingyaogong/minimind-v) for details!

</details>

<details close> 
<summary> <b>2024-09-27</b> </summary>

- 09-27 updated the preprocessing method for the pretrain dataset, abandoned preprocessing into .bin format for training to ensure text integrity (slightly sacrificing training speed).
- Current pretrain preprocessing file is named: pretrain_data.csv.
- Removed some redundant code.

</details>

<details close> 
<summary> <b>2024-09-17</b> </summary>

- Updated minimind-v1-moe model
- To avoid ambiguity, no longer using mistral_tokenizer for tokenization, completely using custom minimind_tokenizer as the tokenizer.

</details>

<details close>
<summary> <b>2024-09-01</b> </summary>

- Updated minimind-v1 (108M) model, using minimind_tokenizer, 3 pretraining rounds + 10 SFT rounds, more thorough training, stronger performance.
- Project has been deployed to ModelScope creation space, you can experience it on this website:
- [🔗ModelScope Online Experience🔗](https://www.modelscope.cn/studios/gongjy/minimind)

</details>

<details close> 
<summary> <b>2024-08-27</b> </summary>

- Project first open-sourced

</details>

# 📌 Quick Start

<details style="color:rgb(128,128,128)">
<summary>Share my hardware and software configuration (for reference only)</summary>

* CPU: Intel(R) Core(TM) i9-10980XE CPU @ 3.00GHz
* RAM: 128 GB
* GPU: NVIDIA GeForce RTX 3090(24GB) * 8
* Ubuntu==20.04
* CUDA==12.2
* Python==3.10.16
* [requirements.txt](./requirements.txt)

</details>

### Step 0

```bash
git clone https://github.com/jingyaogong/minimind.git
```

## Ⅰ Testing Existing Model Performance

### 1. Environment Setup

```bash
pip install -r requirements.txt -i https://mirrors.aliyun.com/pypi/simple
```

### 2. Download Model

Go to the project root directory

```bash
git clone https://huggingface.co/jingyaogong/MiniMind2 # or https://www.modelscope.cn/models/gongjy/MiniMind2
```

### (Optional) Command Line Q&A

```bash
# Use transformers format model
python eval_llm.py --load_from ./MiniMind2
```

### (Optional) Launch WebUI

```bash
# May require `python>=3.10`, install with `pip install streamlit`
# cd scripts
streamlit run web_demo.py
```

### (Optional) Third-party Inference Frameworks

```bash
# ollama
ollama run jingyaogong/minimind2
# vllm
vllm serve ./MiniMind2/ --served-model-name "minimind"
```

## Ⅱ Train from Scratch Yourself

### 1. Environment Setup

```bash
pip install -r requirements.txt -i https://mirrors.aliyun.com/pypi/simple
```

<details style="color:rgb(128,128,128)">
<summary>Note: Test Torch CUDA availability in advance</summary>

```bash
import torch
print(torch.cuda.is_available())
```

If not available, please download and install the whl file from [torch_stable](https://download.pytorch.org/whl/torch_stable.html). Reference [link](https://blog.csdn.net/weixin_45456738/article/details/141029610?ops_request_misc=&request_id=&biz_id=102&utm_term=%E5%AE%89%E8%A3%85torch&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-2-141029610.nonecase&spm=1018.2226.3001.4187)

</details>

### 2. Download Data

Download the required data files from the [dataset download link](https://www.modelscope.cn/datasets/gongjy/minimind_dataset/files) provided below (create the `./dataset` directory) and place them in `./dataset`

<details style="color:rgb(128,128,128)">
<summary>Note: Dataset Notes</summary>

By default, it is recommended to download `pretrain_hq.jsonl` + `sft_mini_512.jsonl` for the fastest reproduction of the Zero chat model.

You can freely choose data files. The section below provides multiple combination schemes that can be appropriately combined based on your training needs and GPU resources.

</details>

### 3. Start Training

Directory is located in `trainer`

<details style="color:rgb(128,128,128)">
<summary>💡 Checkpoint Resume Training</summary>

All training scripts automatically save checkpoints. Simply add `--from_resume 1` parameter to automatically detect, load & resume training:

```bash
python train_pretrain.py --from_resume 1
python train_full_sft.py --from_resume 1
...
```

**Checkpoint Resume Mechanism:**
- Training process automatically saves complete checkpoints in `./checkpoints/` directory (model, optimizer, training progress, etc.)
- Checkpoint file naming: `<weight_name>_<dimension>_resume.pth` (e.g., `full_sft_512_resume.pth`)
- Supports cross-GPU recovery (automatically adjusts step)
- Supports wandb training log continuity (automatically resumes the same run)

> Suitable for long training sessions or unstable environments, no need to worry about progress loss from interruptions

</details>

**3.1 Pretraining (Learning Knowledge)**

```bash
python train_pretrain.py
```

> Execute pretraining to get `pretrain_*.pth` as the output weights for pretraining (where * is the model's dimension, default is 512)

**3.2 Supervised Fine-tuning (Learning Conversation Style)**

```bash
python train_full_sft.py
```

> Execute supervised fine-tuning to get `full_sft_*.pth` as the output weights for instruction fine-tuning (where `full` means full-parameter fine-tuning)

<details style="color:rgb(128,128,128)">
<summary>Note: Training Notes</summary>

By default, all training processes save parameters to the file `./out/***.pth` every 100 steps (each save overwrites the old weights).

For simplicity, only the two-stage training process is described here. For other training (LoRA, distillation, reinforcement learning, inference fine-tuning, etc.), refer to the detailed description in the [Experiment](#-experiment) section below.

</details>

---

### 4. Test Your Trained Model

Ensure the model `*.pth` files to be tested are in the `./out/` directory.
You can also directly download and use the `*.pth` files I trained from [here](https://www.modelscope.cn/models/gongjy/MiniMind2-PyTorch/files).

```bash
python eval_llm.py --weight full_sft # or pretrain/dpo/ppo/grpo...
```

<details style="color:rgb(128,128,128)">
<summary>Note: Testing Notes</summary>

The `--weight` parameter specifies the weight name prefix. Options: `pretrain`, `full_sft`, `dpo`, `reason`, `ppo_actor`, `grpo`, `spo`, etc.

Other common parameters:
- `--load_from`: Model loading path (`model`=native torch weights, other paths=transformers format)
- `--save_dir`: Model weight directory (default `out`)
- `--lora_weight`: LoRA weight name (`None` means not used)
- `--historys`: Number of historical dialogue rounds to carry (must be even, 0 means no history)
- `--max_new_tokens`: Maximum generation length (default 8192)
- `--temperature`: Generation temperature (default 0.85)
- `--top_p`: Nucleus sampling threshold (default 0.85)


For usage details, refer directly to the `eval_llm.py` code.

</details>

---

> [!TIP]
> All training scripts are native PyTorch framework, supporting multi-GPU acceleration. Assume your device has N (N > 1) GPUs:

Single machine N GPU training startup (DDP, supports multi-machine multi-GPU cluster)

```bash
torchrun --nproc_per_node N train_xxx.py
```

<details style="color:rgb(128,128,128)">
<summary>Note: Other Notes</summary>

<del>
Single machine N GPU training (DeepSpeed)

```bash
deepspeed --master_port 29500 --num_gpus=N train_xxx.py
```
</del>

You can optionally enable wandb to record the training process (requires direct internet connection)

```bash
# Requires login: wandb login
torchrun --nproc_per_node N train_xxx.py --use_wandb
# and
python train_xxx.py --use_wandb
```

By adding the `--use_wandb` parameter, you can record the training process. After training is complete, you can view the training process on the wandb website. By modifying the `wandb_project` and `wandb_run_name` parameters, you can specify the project name and run name.

[Note]: After June 2025, the domestic network environment cannot directly connect to WandB. The MiniMind project by default switches to using [SwanLab](https://swanlab.cn/) as the training visualization tool (fully compatible with WandB API), that is, just change `import wandb` to `import swanlab as wandb`, no other changes are needed.

</details>

# 📌 Data Introduction

## Ⅰ Tokenizer

Tokenizer maps words from natural language to numbers like `0, 1, 36` through a "dictionary," which can be understood as numbers representing the page number of the word in the "dictionary."
You can choose to construct your own vocabulary table to train a "dictionary." The code can be found in `./scripts/train_tokenizer.py` (for learning reference only. It's not necessary to train one yourself unless required. MiniMind comes with a built-in tokenizer).
Or you can choose tokenizers from well-known open-source large models.
Just as using Xinhua/Oxford dictionaries directly has the advantage of good token encoding compression, but the disadvantage of having too many pages—tens of thousands of word phrases;
A self-trained tokenizer has the advantage of freely controlling vocabulary length and content, but the disadvantage of low compression ratio (for example, "hello" might be split into "h e l l o"
five independent tokens), and rare words are difficult to cover.
The choice of "dictionary" is important. The output of LLM is essentially a multi-class classification problem with SoftMax to N words in the dictionary, then decoding to natural language through the "dictionary."
Because MiniMind size needs to be strictly controlled to avoid top-heavy models (embedding layer parameters taking up too high a proportion of LLM), shorter vocabulary lengths are better.

<details style="color:rgb(128,128,128)">
<summary>Tokenizer Introduction</summary>

The tokenizer vocabulary sizes of powerful open-source models from third parties such as Yi, qwen, chatglm, mistral, and Llama3 are as follows:

<table>
  <tr><th>Tokenizer Model</th><th>Vocabulary Size</th><th>Source</th></tr>
  <tr><td>yi tokenizer</td><td>64,000</td><td>01AI (China)</td></tr>
  <tr><td>qwen2 tokenizer</td><td>151,643</td><td>Alibaba Cloud (China)</td></tr>
  <tr><td>glm tokenizer</td><td>151,329</td><td>Zhipu AI (China)</td></tr>
  <tr><td>mistral tokenizer</td><td>32,000</td><td>Mistral AI (France)</td></tr>
  <tr><td>llama3 tokenizer</td><td>128,000</td><td>Meta (USA)</td></tr>
  <tr><td>minimind tokenizer</td><td>6,400</td><td>Custom</td></tr>
</table>

> 👉 Updated 2024-09-17: To prevent ambiguity from previous versions and control size, all MiniMind models use minimind_tokenizer for tokenization, abandoning all mistral_tokenizer versions.

```
# Some thoughts
> Although minimind_tokenizer has a small length, its encoding/decoding efficiency is weaker than Chinese-friendly tokenizers like qwen2 and glm.
> But the minimind model chose the self-trained minimind_tokenizer as the tokenizer to maintain lightweight overall parameters, avoiding imbalance in encoding layer and computation layer proportions, preventing top-heavy models, because minimind's vocabulary size is only 6400.
> And minimind has never encountered rare word decoding failures in actual testing, with good results.
> Due to the custom vocabulary compression to 6400, the total LLM parameters are as low as 25.8M.
> The training data `pretrain_hq.jsonl` all comes from the `JiangShu large model dataset`, this part of data is relatively secondary. You can freely choose if you need to train.
```

</details>

## Ⅱ Pretraining Data

Having learned from MiniMind-V1's low-quality pretraining data that caused models to talk nonsense, after `2025-02-05` we decided no longer to use large-scale unsupervised datasets for pretraining.
Instead, we tried to extract the Chinese portion from the [JiangShu Large Model Dataset](https://www.modelscope.cn/datasets/deepctrl/deepctrl-sft-data),
Clean out about 1.6GB of corpus with character length `<512` and concatenate them directly as pretraining data `pretrain_hq.jsonl`, where hq means high
quality (of course it's not yet high, improving data quality is endless).

The file `pretrain_hq.jsonl` data format is

```json
{"text": "How can I get rid of procrastination? Curing procrastination is not easy, but the following suggestions may help..."}
```

## Ⅲ SFT Data

The [JiangShu Large Model SFT Dataset](https://www.modelscope.cn/datasets/deepctrl/deepctrl-sft-data)
"is a complete, uniformly formatted, and safe large model training and research resource.
It collected and organized a large amount of open-source datasets from public sources on the internet, unified their format, cleaned the data,
containing Chinese datasets with 10M entries and English datasets with 2M entries."
The above is the official introduction. After downloading, the total data volume is about 4B tokens, which is definitely suitable as SFT data for Chinese large language models.
However, the official data format is messy, and using all of it for SFT would be too expensive.
I performed secondary cleaning of the official dataset, removing entries with symbol pollution and noise; additionally, still only kept content with total length `<512`,
hoping to supplement knowledge lacking in the pretraining phase through large amounts of dialogue at this stage.
Export file is `sft_512.jsonl` (~7.5GB).

The [Magpie-SFT Dataset](https://www.modelscope.cn/organization/Magpie-Align)
collected ~1M high-quality conversations from Qwen2/2.5. I further cleaned this data, exporting the portion with total length `<2048` as `sft_2048.jsonl` (~9GB).
The portion with length `<1024` exported as `sft_1024.jsonl` (~5.5GB). Using large model dialogue data directly for sft falls into the "black-box distillation" category.

Further cleaned the SFT data from the previous two steps (keeping only content with high Chinese character ratio), filtered conversations with length `<512`, and obtained `sft_mini_512.jsonl` (~1.2GB).

The data format for all sft files `sft_X.jsonl` is

```text
{
    "conversations": [
        {"role": "user", "content": "Hello"},
        {"role": "assistant", "content": "Hello!"},
        {"role": "user", "content": "Goodbye"},
        {"role": "assistant", "content": "Goodbye!"}
    ]
}
```

## Ⅳ RLHF Data

From the [Magpie-DPO Dataset](https://www.modelscope.cn/datasets/Magpie-Align/MagpieLM-DPO-Data-v0.1)
approximately 200k preference data entries (all in English) generated from Llama3.1-70B/8B, can be used to train reward models, optimize model reply quality, making it more consistent with human preferences.
Here, we reorganized content with total data length `<3000` into `dpo.jsonl` (~0.9GB), containing two fields `chosen` and `rejected`, where `chosen`
is the preferred reply and `rejected` is the rejected reply.

The file `dpo.jsonl` data format is

```text
{
  "chosen": [
    {"content": "Q", "role": "user"}, 
    {"content": "good answer", "role": "assistant"}
  ], 
  "rejected": [
    {"content": "Q", "role": "user"}, 
    {"content": "bad answer", "role": "assistant"}
  ]
}
```

## Ⅴ Reasoning Dataset:

There's no denying that in February 2025, who can be hotter than DeepSeek...
It also sparked my strong interest in RL-guided reasoning models. I've already reproduced R1-Zero using Qwen2.5.
If I have time + good results (but 99% of base models lack ability), I will later update MiniMind with RL-trained reasoning models rather than distilled models.
With limited time, the fastest low-cost solution is still direct distillation (black-box method).
Unable to resist R1's popularity, in just a few days there are already various R1 distillation datasets like [R1-Llama-70B](https://www.modelscope.cn/datasets/Magpie-Align/Magpie-Reasoning-V2-250K-CoT-Deepseek-R1-Llama-70B), [R1-Distill-SFT](https://www.modelscope.cn/datasets/AI-ModelScope/R1-Distill-SFT),
[Alpaca-Distill-R1](https://huggingface.co/datasets/shareAI/Alpaca-Distill-R1-ZH),
[deepseek_r1_zh](https://huggingface.co/datasets/jinliuxi/deepseek_r1_zh) and so on. Pure Chinese data is relatively scarce.
Finally integrated them, export file as `r1_mix_1024.jsonl`, data format consistent with `sft_X.jsonl`.

## Ⅵ More Datasets

Currently, [HqWu-HITCS/Awesome-Chinese-LLM](https://github.com/HqWu-HITCS/Awesome-Chinese-LLM)
is collecting and organizing materials related to Chinese LLMs including open-source models, applications, datasets, and tutorials, and continuously updating the latest progress in this field. Comprehensive and professional, Respect!

---

## Ⅷ MiniMind Training Datasets

> [!NOTE]
> After 2025-02-05, all datasets used for final MiniMind training are open-sourced. Therefore, you don't need to preprocess large-scale datasets yourself, avoiding repetitive data processing work.

MiniMind Training Dataset Download: [ModelScope](https://www.modelscope.cn/datasets/gongjy/minimind_dataset/files) | [HuggingFace](https://huggingface.co/datasets/jingyaogong/minimind_dataset/tree/main)

> No need to clone everything, you can download the files you need individually

Place the downloaded dataset files in the `./dataset/` directory (✨ are recommended required items)

```bash
./dataset/
├── dpo.jsonl (55MB, ✨)
├── lora_identity.jsonl (22.8KB)
├── lora_medical.jsonl (34MB)
├── pretrain_hq.jsonl (1.6GB, ✨)
├── r1_mix_1024.jsonl (340MB)
├── rlaif-mini.jsonl (1MB)
├── sft_1024.jsonl (5.6GB)
├── sft_2048.jsonl (9GB)
├── sft_512.jsonl (7.5GB)
└── sft_mini_512.jsonl (1.2GB, ✨)
```

<details style="color:rgb(128,128,128)">
<summary>Note: Brief Description of Each Dataset</summary>

* `dpo.jsonl`✨ --RLHF stage dataset (optimized and simplified, suitable for fast training)
* `lora_identity.jsonl` --Self-awareness dataset (e.g., Who are you? I am minimind...), recommended for lora training (can also be used for full-parameter SFT, don't be limited by the name)
* `lora_medical.jsonl` --Medical Q&A dataset, recommended for lora training (can also be used for full-parameter SFT, don't be limited by the name)
* `pretrain_hq.jsonl`✨ --Pretraining dataset, integrated from JiangShu Technology
* `r1_mix_1024.jsonl` --DeepSeek-R1-1.5B distilled data, maximum character length per entry is 1024 (therefore set max_seq_len=1024 when training)
* `rlaif-mini.jsonl` --RLAIF training dataset, randomly sampled 10,000 high-quality conversations from SFT dataset for training reinforcement learning algorithms like PPO/GRPO/SPO
* `sft_1024.jsonl` --Integrated from Qwen2.5 distilled data (a subset of sft_2048), maximum character length per entry is 1024 (therefore set max_seq_len=1024 when training)
* `sft_2048.jsonl` --Integrated from Qwen2.5 distilled data, maximum character length per entry is 2048 (therefore set max_seq_len=2048 when training)
* `sft_512.jsonl` --Integrated from JiangShu Technology SFT data, maximum character length per entry is 512 (therefore set max_seq_len=512 when training)
* `sft_mini_512.jsonl`✨ --Minimal integration from JiangShu Technology SFT data + Qwen2.5 distilled data (for quick training of Zero models), maximum character length per entry is 512 (therefore set max_seq_len=512 when training)

</details>

![dataset](./images/dataset.jpg)

<details style="color:rgb(128,128,128)">
<summary>Instructions & Recommended Training Schemes</summary>

* MiniMind2 Series was trained on approximately 20GB of corpus in total, about 4B tokens, corresponding to the data combination training results above (cost: 💰💰💰💰💰💰💰💰, results: 😊😊😊😊😊😊)

* For the fastest speed to implement Zero model from scratch, we recommend using the data combination of `pretrain_hq.jsonl` + `sft_mini_512.jsonl`, specific cost and results can be seen in the table below (cost: 💰, results: 😊😊)

* For friends with certain computing resources or those who care more about results, you can consider the former to fully reproduce MiniMind2; for those with only single GPU or who care about quick reproduction in short time, we highly recommend the latter;

* [Compromise solution] You can also choose medium-sized data like `sft_mini_512.jsonl`, `sft_1024.jsonl` for free combination training (cost: 💰💰💰, results: 😊😊😊😊).

</details>

# 📌 Model

## Structure

MiniMind-Dense (same as [Llama3.1](https://ai.meta.com/blog/meta-llama-3-1/)) uses the Transformer Decoder-Only structure. The differences from GPT-3 are:

* Adopts GPT-3's pre-normalization method, normalizing at the input of each Transformer sub-layer rather than at the output. Specifically, it uses the RMSNorm normalization function.
* Replaced ReLU with SwiGLU activation function to improve performance.
* Like GPT-Neo, it removed absolute position embeddings and switched to rotary position embeddings (RoPE), which works better when handling inference beyond training length.

---

MiniMind-MoE model structure is based on Llama3 and the MixFFN mixture-of-experts module from [Deepseek-V2/3](https://arxiv.org/pdf/2405.04434).

* DeepSeek-V2 in feed-forward networks (FFN) uses finer-grained expert splitting and shared expert isolation techniques to improve the effect of Experts.

---

MiniMind's overall structure is consistent, with only small adjustments in RoPE computation, inference functions, and FFN layer code.
The structure is shown in the diagram below (redrawn version):

![structure](./images/LLM-structure.png)
![structure-moe](./images/LLM-structure-moe.png)

To modify model configuration, see [./model/model_minimind.py](./model/model_minimind.py).
Reference model parameter versions see the table below:

| Model Name        | params | len_vocab | rope_theta | n_layers | d_model | kv_heads | q_heads | share+route |
|-------------------|--------|-----------|------------|----------|---------|----------|---------|-------------|
| MiniMind2-Small   | 26M    | 6400      | 1e6        | 8        | 512     | 2        | 8       | -           |
| MiniMind2-MoE     | 145M   | 6400      | 1e6        | 8        | 640     | 2        | 8       | 1+4         |
| MiniMind2         | 104M   | 6400      | 1e6        | 16       | 768     | 2        | 8       | -           |
| minimind-v1-small | 26M    | 6400      | 1e4        | 8        | 512     | 8        | 16      | -           |
| minimind-v1-moe   | 4×26M  | 6400      | 1e4        | 8        | 512     | 8        | 16      | 1+4         |
| minimind-v1       | 108M   | 6400      | 1e4        | 16       | 768     | 8        | 16      | -           |


## Model Configuration

📋 Regarding LLM parameter configuration, there's an interesting paper [MobileLLM](https://arxiv.org/pdf/2402.14905) that conducted detailed research and experiments.
Scaling Law has its own unique patterns in small models.
Parameters causing Transformer parameter scaling changes almost entirely depend on `d_model` and `n_layers`.

* `d_model`↑ + `n_layers`↓ -> Wide and short
* `d_model`↓ + `n_layers`↑ -> Narrow and tall

The 2020 Scaling Law paper argued that training data volume, parameter quantity, and training iterations are the key factors determining performance, while model architecture influence is negligible.
However, this law doesn't seem to fully apply to small models.
MobileLLM argues that architecture depth is more important than width, "deep and narrow" "tall and skinny" models can learn more abstract concepts than "wide and shallow" models.
For example, when model parameters are fixed at 125M or 350M, 30-42 layer "narrow" models clearly have superior performance compared to around 12 layer "wide" models,
showing similar trends across 8 benchmark tests including commonsense reasoning, Q&A, and reading comprehension.
This is actually a very interesting discovery, because previously when designing architectures for ~100M scale small models, almost no one tried stacking more than 12 layers.
This is consistent with what MiniMind observed in experiments when adjusting model parameters between `d_model` and `n_layers` during training.
However, "deep and narrow" models also have dimensional limits. When d_model<512, the disadvantage of embedding dimension collapse is very obvious,
and added layers cannot compensate for the disadvantage of insufficient d_head caused by fixed q_head in embeddings.
When d_model>1536, increasing layers seems to have higher priority than d_model, bringing more "cost-effective" parameter -> performance gains.

* Therefore MiniMind sets small model dim=512, n_layers=8 to achieve the balance of "extremely small size <-> better performance."
* Setting dim=768, n_layers=16 to gain larger performance improvements, more consistent with small model Scaling-Law curves.

For reference, GPT3 parameter settings see the table below:
![gpt3_config.png](./images/gpt3_config.png)

---

# 📌 Experiment

## Ⅰ Training Costs

- **Time unit**: Hours (h).
- **Cost unit**: Chinese Yuan (￥); 7￥ ≈ 1 USD.
- **3090 rental price**: ≈1.3￥/h (you can check current prices yourself).
- **Reference standard**: The table only shows actual measured training time for `pretrain` and `sft_mini_512` two datasets. Other time costs are estimated based on dataset size (may have slight variations).

> Based on 3090 (single GPU) cost calculation

| Model Name      | params | pretrain         | sft_mini_512     | sft_512       | sft_1024          | sft_2048         | RLHF          |
|-----------------|--------|------------------|------------------|---------------|-------------------|------------------|---------------|
| MiniMind2-Small | 26M    | ≈1.1h<br/>≈1.43￥ | ≈1h<br/>≈1.3￥    | ≈6h<br/>≈7.8￥ | ≈4.58h<br/>≈5.95￥ | ≈7.5h<br/>≈9.75￥ | ≈1h<br/>≈1.3￥ |
| MiniMind2       | 104M   | ≈3.9h<br/>≈5.07￥ | ≈3.3h<br/>≈4.29￥ | ≈20h<br/>≈26￥ | ≈15h<br/>≈19.5￥   | ≈25h<br/>≈32.5￥  | ≈3h<br/>≈3.9￥ |

---

<details style="color:rgb(128,128,128)">
<summary>Training Cost Summary & Forecast</summary>

> MiniMind2-Small Parameters
>> `pretrain_hq`+`sft_mini_512` Dataset
<br/>Single 3090 GPU (1 epoch) + 2.1 hours + Cost 2.73 Chinese Yuan
<br/>Can train MiniMind-Zero-0.025B model from scratch!!!

> MiniMind2-Small Parameters
>> `pretrain_hq`+`sft_512`+`sft_2048`+`dpo` Dataset
<br/>Single 3090 GPU (2 epochs) + Approximately 38.16 hours + Cost 49.61 Chinese Yuan
<br/>Can train MiniMind2-Small-0.025B model from scratch!!!

> MiniMind2 Parameters
>> `pretrain_hq`+`sft_512`+`sft_2048`+`dpo` Dataset
<br/>Single 3090 GPU (2 epochs) + Approximately 122 hours + Cost 158.6 Chinese Yuan
<br/>Can train MiniMind2-0.1B model from scratch!!!

</details>

✨ Based on single NVIDIA 3090 GPU, `MiniMind-Zero` requires only `2 hours` + `3 Chinese Yuan` from scratch to achieve ChatBot effect!

✨ PS: If training with 8 4090 GPUs, the total time can even be compressed to less than 10 minutes! (Due to shorter time, cost is still around 3 Yuan, comparable to single GPU cost)

✨ With an extremely low barrier to entry, achieve large model freedom for everyone! This is the original intention behind the birth of the MiniMind series!

✨ The `MiniMind-Zero` costing only `3 Chinese Yuan` is not just hype! Chat test:

```text
👶: Please introduce yourself.
🤖️: As an artificial intelligence, I have no actual life and no self-awareness, so I don't have my own life. I was designed to help users answer questions, provide information, and have conversations, etc. My design and functionality are built by computer science, machine learning, artificial intelligence technology and algorithms, and I'm implemented through programming and algorithms.

👶: Recommend some special dishes from Hangzhou.
🤖️: Hangzhou has many delicious special dishes, such as chicken kebabs, eel head, boiled fish, tofu brain, etc. These dishes are very delicious, with unique flavors and tastes, definitely worth trying.

👶: Please explain the concept of "large language models" to me.
🤖️: A large language model is a type of artificial intelligence technology that uses large amounts of text data to train models, then continuously optimizes the model through iterations. Its goal is to generate text that meets specific needs based on input data. These texts can be any topic you're interested in.

👶: Introduce the history of the United States, please.
🤖️: The "Introok's the believeations of theument" you mentioned gets its name from the ancient Chinese "groty of of the change."
```

Extremely fast with initial results, and can even be further compressed to obtain smaller and higher quality training data.
Zero model weights are saved as `full_sft_512_zero.pth` (see MiniMind model file links below). If interested, you can download and test this model.

---

## Ⅱ Main Training (Required)

> All training scripts should be executed in the `cd ./trainer` directory

### **1. Pretraining (Pretrain)**:

What LLMs need to learn first is not to communicate directly with people, but to fill the network parameters with the ink of knowledge. The "ink" should ideally be as saturated as possible, accumulating vast knowledge about the world.
Pretraining is where the model first studies hard to learn a large amount of basic knowledge, such as organizing large-scale high-quality training data from Wikipedia, news, books, etc.
This process is "unsupervised," meaning humans don't need to perform any "supervised" corrections during the process. Instead, the model itself summarizes patterns and learns knowledge from large amounts of text.
The model's goal at this stage is only one: **Learn word prediction**. For example, given the input "Qin Shi Huang," it can continue with "was the first emperor of China."

```bash
torchrun --nproc_per_node 1 train_pretrain.py # 1 means single GPU training, adjust based on your hardware (set >=2 for multiple GPUs)
# or
python train_pretrain.py
```

> After training, model weight files are saved by default every `100 steps` as: `pretrain_*.pth` (where *
> is the model's specific dimension, new files overwrite old ones on each save)

| MiniMind2-Small (512dim) | MiniMind2 (768dim) |
|---|---|
| <img src="./images/pre_512_loss.png"> | <img src="./images/pre_768_loss.png"> |

### **2. Supervised Fine-Tuning (SFT)**:

After pretraining, the LLM has mastered a lot of knowledge, but at this point it only knows how to do word prediction mindlessly and doesn't know how to chat with people.
The SFT stage requires applying a custom chat template to fine-tune the semi-finished LLM.
For example, after the model encounters such a template [question->answer, question->answer], it no longer does mindless word continuation, but realizes this is the end of a complete conversation.
This process is called instruction fine-tuning, like helping the already knowledgeable "Newton" gentleman adapt to 21st-century smartphone chat habits, learning that the left side of the screen is the other person's message and the right side is the user's message.
During training, MiniMind's instruction and answer lengths are truncated at 512 to save GPU memory. Like learning to write, you start with short articles, and after learning to write 200-character essays, 800-character articles become easy.
When length extension is needed, you only need to prepare a small amount of 2k/4k/8k length dialogue data for further fine-tuning (preferably combined with RoPE-NTK scaling).
> During inference, by adjusting RoPE scaling, it will be convenient to achieve training-free length extrapolation to 2048 and beyond.

```bash
torchrun --nproc_per_node 1 train_full_sft.py
# or
python train_full_sft.py
```

> After training, model weight files are saved by default every `100 steps` as: `full_sft_*.pth` (where *
> is the model's specific dimension, new files overwrite old ones on each save)

| MiniMind2-Small (512dim) | MiniMind2 (768dim) |
|---|---|
| <img src="./images/sft_512_loss.png"> | <img src="./images/sft_768_loss.png"> |

## Ⅲ Other Training Stages (Optional)

> All training scripts should be executed in the `cd ./trainer` directory

### **3. Knowledge Distillation (KD)**

At this point, after all the previous training steps, the model has completely acquired basic capabilities and usually can graduate.
However, knowledge distillation can further optimize model performance and efficiency. Knowledge distillation means the student model learns from the teacher model.
The teacher model is usually a well-trained large model with high accuracy and generalization ability.
The student model is a smaller model whose goal is to learn the teacher model's behavior rather than learn directly from raw data.
In SFT learning, the model's goal is to fit hard labels for token classification (hard labels), i.e., true class labels (such as 0 or 6400).
In knowledge distillation, the teacher model's softmax probability distribution is used as soft labels (soft labels). The small model only learns soft labels and uses KL-Loss to optimize model parameters.
In simple terms, SFT learns the problem-solving answers the teacher gives directly. The KD process is like "opening" the teacher's smart brain and trying to mimic the neural state of the teacher's "brain" thinking about problems.
For example, when the teacher model calculates the problem `1+1=2`, the final layer neurons a state is 0, neuron b state is 100, neuron c state is -99...
The student model learns the operating rules inside the teacher model's brain through large amounts of data. This process is called: knowledge distillation.
Knowledge distillation has only one purpose: make small models smaller in size while having better results.
However, with the birth and development of LLMs, the term model distillation has been widely abused, creating two schools of "white-box/black-box" knowledge distillation.
Closed-source models like GPT-4, since their internal structure cannot be accessed, can only learn from the data they output. This process is called black-box distillation, and is the most common practice in the age of large models.
Black-box distillation is completely identical to the SFT process, except the data is collected from large model outputs. Therefore, you only need to prepare data and further FT.
Note that you need to change the loaded base model to `full_sft_*.pth`, i.e., further distillation learning based on the fine-tuned model.
Both `./dataset/sft_1024.jsonl` and `./dataset/sft_2048.jsonl` are collected from qwen2.5-7/72B-Instruct large models and can be used directly for SFT to acquire some Qwen behavior.

```bash
# Note: need to change the dataset path in train_full_sft.py and max_seq_len
torchrun --nproc_per_node 1 train_full_sft.py
# or
python train_full_sft.py
```

> After training, model weight files are similarly saved by default every `100 steps` as: `full_sft_*.pth` (where * is the model's specific dimension, new files overwrite old ones on each save)

Emphasis should be placed on introducing MiniMind's white-box distillation code `train_distillation.py`. Since there is no powerful teacher model within the same MiniMind series, the white-box distillation code is only for learning reference.

```bash
torchrun --nproc_per_node 1 train_distillation.py
# or
python train_distillation.py
```

### **4. LoRA (Low-Rank Adaptation)**

LoRA is an efficient Parameter-Efficient Fine-Tuning (PEFT) method aimed at fine-tuning pre-trained models through low-rank decomposition.
Compared to full parameter fine-tuning (Full Fine-Tuning), LoRA only needs to update a small number of parameters.
LoRA's core idea is: introduce low-rank decomposition in the model's weight matrices and only update the low-rank parts while keeping the original pre-trained weights unchanged.
Code can be found in `./model/model_lora.py` and `train_lora.py`, completely implementing the LoRA process from scratch without relying on third-party library packaging.

```bash
torchrun --nproc_per_node 1 train_lora.py
# or
python train_lora.py
```

> After training, model weight files are saved by default every `100 steps` as: `lora_xxx_*.pth` (where *
> is the model's specific dimension, new files overwrite old ones on each save)

Many people are confused about how to make models learn knowledge in their private domains, how to prepare datasets, and how to migrate general-purpose models to build domain-specific models.
Here are some examples. For general models lacking medical domain knowledge, you can try adding domain knowledge to the original model to get better performance.
At the same time, you usually don't want to lose other abilities of the original base model while learning domain knowledge. In this case, LoRA can effectively solve this problem.
You only need to prepare dialogue datasets in the following format and place them in `./dataset/lora_xxx.jsonl`, then run `python train_lora.py`
to get the new model weights `./out/lora/lora_xxx.pth`.

**Medical Scenario**

```
 {"conversations": [{"role": "user", "content": "What height should a cervical spondylosis patient's pillow be?"}, {"role": "assistant", "content": "For cervical spondylosis patients, pillow height selection should be based on..."}]}
 {"conversations": [{"role": "user", "content": "What about xxx"}, {"role": "assistant", "content": "xxx..."}]}
```

**Self-awareness Scenario**

```
 {"conversations": [{"role": "user", "content": "What is your name?"}, {"role": "assistant", "content": "My name is minimind..."}]}
 {"conversations": [{"role": "user", "content": "Who are you"}, {"role": "assistant", "content": "I am..."}]}
```

At this point, [base model + LoRA model] can acquire medical scenario model-enhanced capabilities, equivalent to adding a LoRA plug-in to the base model, which does not lose the base model's original abilities.
You can test the model through `eval_llm.py` for model evaluation.

```bash
# Note: weight parameter specifies base model type, should match the base model used during train_lora training
python eval_llm.py  --weight dpo --lora_weight lora_medical
```

**Small Test**

```
👶: I've been feeling dizzy recently, what could be the reason?
🤖️: Dizziness could be caused by many reasons, including but not limited to: heart disease, eye damage, allergic reactions, skin problems, allergic reactions, stress, anxiety, fatigue, medication side effects, sexual dysfunction, or others...

---

👶: What is your relationship with openai?
🤖️: I am MiniMind, an artificial intelligence assistant developed by Jingyao Gong. I interact with users through natural language processing and algorithm training.
```

PS: As long as you have the required datasets, you can also do full_sft full parameter fine-tuning (need to mix general knowledge to avoid overfitting domain data making the model worse and losing generality)

### **5. Training Reasoning Models (Reasoning Model)**

DeepSeek-R1 was so popular, almost pointing out a new paradigm for future LLMs.
The paper points out that models `>3B` require multiple iterations of cold starts and RL reward training to achieve visible reasoning ability improvements.
The fastest, most reliable, and most economical approach, as well as recent various so-called reasoning models, are almost all directly distilled from data.
But due to lack of technical sophistication, the distillation school is looked down upon by the RL school (hhhh).
I quickly tried on Qwen 1.5B small model and quickly reproduced math reasoning ability in the Zero process.
However, a regrettable consensus is: models with parameters too small cannot achieve any reasoning effect through cold start SFT+GRPO.
For now, MiniMind firmly chooses to be in the distillation school. If RL on 0.1B models later achieves small progress, this training approach section will be updated.

For distillation, you only need to prepare datasets in the same format as the SFT stage. The dataset source has been introduced above. Data format examples:

```json
{
  "conversations": [
    {
      "role": "user",
      "content": "Hello, I am Xiaofang, nice to meet you."
    },
    {
      "role": "assistant",
      "content": "<think>\nHello! I am a small AI reasoning model R1-Lite-Preview developed by an independent developer in China. I'm happy to serve you!\n</think>\n<answer>\nHello! I am a small AI reasoning model R1-Lite-Preview developed by an independent developer in China. I'm happy to serve you!\n</answer>"
    }
  ]
}
```

The reply template for reasoning model R1 is:

```text
<think>\nThinking process\n</think>\n
<answer>\nFinal answer\n</answer>
```

This is constrained by setting a rule-based reward function in GRPO to make the model comply with thinking tags and reply tags (in the early stages of cold starts, reward values should be increased).

Another issue is that although the distillation process is the same as SFT, experimental results show that models have difficulty consistently complying with template-compliant replies every time, i.e., deviating from thinking and reply tag constraints.
A small trick here is to increase the loss penalty for marker position tokens. See details in `train_distill_reason.py`:

```text
# Add extra penalty to positions corresponding to sp_ids
...
loss_mask[sp_ids] = 10 # penalty coefficient
```

Another tip is that because reasoning data only filtered `<1024` length data, it has fewer multi-turn conversations and English data.
Therefore, `r1_mix_1024.jsonl` mixed approximately 10k multi-turn conversations + English data to prevent serious model forgetting.

The script defaults to reasoning ability distillation fine-tuning based on the rlhf model. You can directly start training:

```bash
torchrun --nproc_per_node 1 train_distill_reason.py
# or
python train_distill_reason.py
```

> After training, model weight files are saved by default every `100 steps` as: `reason_*.pth` (where * is the model's specific dimension, new files overwrite old ones on each save)

Let's test it:

```text
👶: Please introduce yourself.
🤖️: <think>
Um, the user is asking me to introduce myself. I need to explain myself first. First, I should clarify who the user is - are they students, working professionals or ordinary people? The user might be a student or working professional, so information delivery should be to help students and working professionals with information. Then I need to respond to the user, which might include introducing where I am, hobbies, career experience, and other information. I should note to use formal language without being too formal, while keeping it concise and clear. This makes it easy for users to understand and convenient for them to check related information. Finally, I should summarize to let the user know how I help them complete their tasks, giving them more information about me.
</think>
<answer>
I am **"your name", what is your name?
</answer>

👶: Which subject are you better at?
🤖️: <think>
Hello! I am a small AI reasoning model R1 developed by Chinese independent developers. If you have any questions, I will do my best to help you.
</think>
<answer>
Hello! I am a small AI reasoning model R1 developed by Chinese independent developers. If you have any questions, I will do my best to help you.
</answer>
```

## IV Reinforcement Learning Training

RL methods in LLMs can be divided into two categories:

1. **Reinforcement Learning from Human Feedback (RLHF)**

- Train the model by evaluating human **preferences** for model outputs, making it generate content more consistent with human values and preferences.

2. **Reinforcement Learning from AI Feedback (RLAIF)**

- Use **AI models** (typically pre-trained language reward models) to provide feedback rather than directly relying on human manual annotation.
- The "AI" here can also be certain rule-based rewards, such as math answer correctness / code executors...

| Type  | Judge | Advantages | Disadvantages |
|-------|-------|-----------|---------------|
| RLHF  | Human | More aligned with real human preferences | High cost, low efficiency |
| RLAIF | Model | Automated, highly scalable | May deviate from real human preferences |

The two are essentially the same, both using **reinforcement learning** to utilize certain forms of "**feedback**" to optimize model behavior.

Except for the different **feedback** sources, there are no other differences.

### 👀 Unified Perspective on PO Algorithms

Before introducing specific algorithm implementations, I'll present my personal understanding of the unified commonality of all Policy Optimization (PO) algorithms in a minimalist perspective.

The essence of all RL algorithms is only optimizing one expectation:

$$\mathcal{J}_{PO} = \mathbb{E}_{q \sim P(Q), o \sim \pi(O|q)} \left[ \underbrace{f(r_t)}_{\text{policy term}} \cdot \underbrace{g(A_t)}_{\text{advantage term}} - \underbrace{h(\text{KL}_t)}_{\text{regularization term}} \right]$$

During training, only **minimize the negative objective function**, i.e.: $\mathcal{L_{PO}}=-\mathcal{J_{PO}}$

This framework contains only three core components:
* **Policy term** $f(r_t)$: How to use probability ratio $r_t$? Tell the model how large the deviation between new and old policies is, whether better tokens are explored
* **Advantage term** $g(A_t)$: How to calculate advantage $A_t$, this is important! Large models solving definite integrals is unremarkable, small models answering addition/subtraction correctly usually have positive advantages
* **Regularization term** $h(\text{KL}_t)$: How to constrain the change magnitude $\text{KL}_t$, both preventing drift and not being too rigid

<details>
<summary>(Expand) Symbol Explanation</summary>

| Symbol | Meaning | Explanation | Range |
|--------|---------|------------|-------|
| $q$ | Question/prompt | Sampled from dataset $P(Q)$ | - |
| $o$ | Model output sequence | Generated by policy $\pi$ | - |
| $r_t$ | Probability ratio | $r_t = \frac{\pi_\theta(o_t\|q, o_{<t})}{\pi_{ref}(o_t\|q, o_{<t})}$ | $(0, +\infty)$ |
| $A_t$ | Advantage function | Measures how good an action is compared to baseline | $(-\infty, +\infty)$ |
| $\text{KL}_t$ | KL divergence | Prevent policy from deviating too far from reference model | $[0, +\infty)$ |

</details>

Different **xxPO algorithms** are essentially just different design instantiations of these three components!

---

### **6. Reinforcement Learning from Human Feedback (RLHF)**

In the previous training steps, the model has acquired basic conversation abilities, but these are completely based on word prediction, lacking the motivation of positive and negative examples.
The model doesn't yet know what answers are good and what are bad. We hope it can be more aligned with human preferences, reducing the probability of unsatisfactory answers.
This process is like having the model undergo new training, learning from excellent employees as examples and passive employees as counter-examples, to learn how to respond better.

#### 6.1 Direct Preference Optimization

Direct Preference Optimization (DPO) algorithm loss:

$$\mathcal{L}_{DPO} = -\mathbb{E}\left[\log \sigma\left(\beta \left[\log \frac{\pi_\theta(y_w|x)}{\pi_{ref}(y_w|x)} - \log \frac{\pi_\theta(y_l|x)}{\pi_{ref}(y_l|x)}\right]\right)\right]$$

Where:
- **Policy term**: $f(r_t) = \log r_w - \log r_l$ (contrast probability ratios of chosen vs rejected)
- **Advantage term**: $g(A_t)$ = / (through preference contrast, no need to explicitly calculate advantage)
- **Regularization term**: $h(\text{KL}_t)$ = implicit in $\beta$ (control deviation from reference model)

Specifically:
- DPO derives an analytical training objective for preference pairs from PPO with KL constraints, directly maximizing the log-odds that "chosen outperforms rejected"; no need to simultaneously train Reward/Value models. DPO only needs to run two models `actor` and `ref`, with low GPU memory usage, stable convergence, and simple implementation.
- Training paradigm: off-policy, using static preference datasets, can repeat multiple epochs; Ref model is fixed (outputs pre-cached).
- DPO's limitation is no online exploration, more used for "preference/safety" human value alignment; limited improvement in "intellectual ability" to solve problems correctly (of course this depends on the dataset, collecting large-scale positive and negative samples with human evaluation is difficult).

```bash
torchrun --nproc_per_node 1 train_dpo.py
# or
python train_dpo.py
```

> After training, model weight files are saved by default every `100 steps` as: `dpo_*.pth` (where * is the model's specific dimension, new files overwrite old ones on each save)

### **7. Reinforcement Learning from AI Feedback (RLAIF)**

Compared to RLHF which relies on human-annotated chosen/rejected preference pairs, RLAIF has AI completely act as the "judge."
The so-called AI "judge" can be a model-based reward large model (Reward Model), can be like R1 setting rule-based functions for validation, or can be environmental feedback like tool calling.
For example: whether math problem answers are correct, whether code execution passes test cases, whether reasoning processes meet format requirements...can all be automatically judged.
RLAIF's greatest advantage is its **scalability** and **On-Policy** characteristics——no need for expensive human annotation, can generate massive training samples, letting models quickly evolve through large-scale online trial and error.

MiniMind implements **2+N** basic + cutting-edge RLAIF methods:
* **PPO**, **GRPO** are classic RL algorithms widely validated at scale;
* N cutting-edge RL algorithms (updated irregularly with experimental nature).

#### 1️⃣ Dataset Preparation (Required)

To quickly verify RLAIF effectiveness, 10,000 high-quality conversations were randomly sampled from the SFT dataset, building about 1MB size `rlaif-mini.jsonl` ([Huggingface](https://huggingface.co/datasets/jingyaogong/minimind_dataset/blob/main/rlaif-mini.jsonl))

Data format is consistent with SFT, but assistant content is not needed, because during training it's completely real-time sampled and generated by the $\Pi$ policy model. Thus:

```json
{
    "conversations": [
        {"role": "user", "content": "Explain what photosynthesis is?"},
        {"role": "assistant", "content": "None"}
    ]
}
```

During RLAIF training, the model generates 1 or more candidate answers based on user questions, then a reward function/model scores the answers.
High-scoring answers are encouraged (increase $\Pi$ policy probability), low-scoring answers are suppressed (decrease $\Pi$ policy probability). This "score->adjust" loop is the core of reinforcement learning.

#### 2️⃣ Reward Model Preparation (Required)

It's known that RLAIF training requires a "reward model (Reward Model)" to score generated answers.

We select the small and high-quality InternLM2-1.8B-Reward
([ModelScope](https://modelscope.cn/models/Shanghai_AI_Laboratory/internlm2-1_8b-reward) | [HuggingFace](https://huggingface.co/internlm/internlm2-1_8b-reward))
as the base reward model.

After downloading the reward model, it needs to be placed in the **same level directory** as the minimind project. The recommended structure is:

```
project/
├── minimind/                    # MiniMind project
│   ├── model/
│   └── ...
└── internlm2-1_8b-reward/       # Reward model (same level as minimind)
    ├── config.json
    ├── model.safetensors
    └── ...
```

<details>
<summary><b>Reward Mechanism Choice and MiniMind Limitations (Click to expand)</b></summary>

**1. Diversity of Reward Mechanisms**

The "reward signal" source in RLAIF can be very flexible:

- **Model-based rewards**: Can use dedicated Reward Models (like InternLM2-Reward), or use general LLMs + prompts for scoring (like Qwen3-as-a-Judge). Reward model scale and architecture are freely selectable.

- **Rule-based rewards**: Can construct reward signals based on rule functions, for example:
  - Math problem answer correctness verification (Ground Truth comparison)
  - SQL execution success rate and result accuracy
  - Code interpreter run results (pass@k)
  - Tool call return status (API success/failure)
  - Format compliance checks (JSON/XML parsing)
  - Reasoning chain completeness evaluation (CoT step count)

- **Environment-based rewards**: In Agent scenarios, environmental feedback itself is natural reward (like game scores, Research completeness, task completion).

Any mechanism that can quantify "answer quality" can serve as an RL reward source. DeepSeek R1 is a typical case: using rule-based functions to verify math answer correctness as reward, no need for additional Reward Models.

**2. MiniMind Limitation: Reward Sparsity Problem**

RLAIF training can be applied to both reasoning and non-reasoning models, the difference is only in format.

However, for MiniMind with such tiny 0.1B parameters and weak abilities, on general tasks (like R1-style math datasets) it encounters serious reward sparsity (Reward Sparsity) problems:

- **Phenomenon**: Model-generated candidate answers are almost all wrong, causing all reward scores $r(x,y) \approx 0$
- **Consequence**: Advantage function $A(x,y) = r(x,y) - b(x) \approx 0$, policy gradient signal disappears, cannot effectively update parameters $\theta$

Like having elementary school students do high school math exams, no matter how many attempts they get zero, cannot learn to improve strategies through score differences. This is a fundamental principle limitation of RL algorithms.

To mitigate this problem, MiniMind's implementation chose **model-based continuous reward signals**:

- Reward Model outputs continuous scores (like -2.5 to +3.0), not binary 0/1
- Even if answer quality is all poor, can still distinguish subtle differences between "much worse" (-3.0) and "worse" (-2.8). So this **dense and continuous** reward signal can provide non-zero gradients to the advantage function $A(x,y)$, enabling gradual policy network optimization
- Can also mix multiple reward sources: $r_{\text{total}} = \alpha \cdot r_{\text{model}} + \beta \cdot r_{\text{rule}}$ (for example, can detect think tag format rewards while also synthesizing answer quality reward scores)
- In minimind practice, avoid directly using rule-based binary rewards + out-of-scope difficulty data (like MATH500), which easily leads to all-zero rewards;
- Monitor reward score variance $\text{Var}(r)$ during training, if it consistently approaches 0 need to adjust data or reward mechanism

**For Production-Scale Large Models in Agentic RL Scenarios**:

In real Agent systems (code generation, tool calling, retrieval-planning-execution multi-turn pipelines), rewards are different paradigms of "delayed round settlement":

- LLM needs to generate tool call instructions token-by-token (tool_call), go through parsing (tool_parse), tool execution (tool_exec), then splice results back to context for next step; repeat until completion.
- One complete task pipeline includes multiple calls+thinking, calculate total reward once until termination condition is met (like whether task is complete, whether tests pass, whether targets are hit).

Therefore, Agentic RL is closer to sparse/delayed reward settings: gradient backprop happens "after the round ends," very different from non-Agentic RL tasks with "instant scoring and instant updates" on single conversation rounds.
This also explains why Agent tasks favor environment feedback (environment-based reward) rather than static reward model scoring.

- **Environmental interaction feedback**: Final results matter (code runs, API returns success, sub-goals complete);
- **Model-based reward limitations**: Limited capture of long pipelines and executable semantics, likely inconsistent with real environmental feedback (reward hacking).

</details>

---

#### 7.1 [Proximal Policy Optimization](https://arxiv.org/abs/1707.06347)

PPO is a very classic reinforcement learning algorithm proposed by OpenAI in 2017, and is the universal baseline method for LLM RL.

**PPO Loss**:
$$\mathcal{L}_{PPO} = -\mathbb{E}\left[\min(r_t \cdot A_t, \text{clip}(r_t, 1-\varepsilon, 1+\varepsilon) \cdot A_t)\right] + \beta \cdot \mathbb{E}[\text{KL}]$$

Where:
- **Policy term**: $f(r_t) = \min(r_t, \text{clip}(r_t, 1-\varepsilon, 1+\varepsilon))$ (clip probability ratio to prevent aggressive updates)
- **Advantage term**: $g(A_t) = R - V(s)$ (estimate value function through Critic network)
- **Regularization term**: $h(\text{KL}_t) = \beta \cdot \mathbb{E}[\text{KL}]$ (global KL divergence constraint)

Comparing to DPO:
- DPO (Off-Policy): Training data is a static preference dataset (chosen vs rejected), can repeatedly use the same batch of data to train multiple epochs, just like traditional supervised learning. High data efficiency, low training cost. Directly optimizes log-likelihood of preference pairs, no Reward Model needed.
- PPO (On-Policy): Must use current policy to real-time sample new data, old policy-collected data cannot be used (distribution shift problem). Although importance sampling and clip mechanisms allow slight distribution shifts, essentially requires data from relatively fresh policies. Low data efficiency, but suited for explorative learning.

In simple terms:

- The former teaches models to learn by offline preset "good/bad standards," even if not outputtable by current models (like practicing ball hitting by watching world champion/runner-up videos);
- The latter teaches models real-time to do things right, online sampling from newest model policy (coach hand-teaching, real-time scoring each action).

MiniMind's PPO implementation includes Actor model (generate answers) and Critic model (evaluate answer value), and complete GAE (Generalized Advantage Estimation) advantage function calculation.

**Training**:

```bash
torchrun --nproc_per_node N train_ppo.py
# or
python train_ppo.py
```

> After training, model weight files are saved by default every `100 steps` as: `ppo_actor_*.pth` (where * is the model's specific dimension)

| MiniMind2-Small (512dim) | MiniMind2 (768dim) |
|---|---|
| <img src="./images/train_ppo_512.png"> | <img src="./images/train_ppo_768.png"> |

From the training curves, you can see PPO has the problem of **slow reward improvement**. I believe this mainly stems from **PPO's dual-network joint optimization** method: Critic needs to gradually converge to accurately estimate value functions, and Actor's policy updates depend on Critic-provided advantage estimates, the two interdependent forming complex optimization. Early training period Critic estimates inaccurately affects Actor gradient direction, leading to slow overall convergence. Furthermore, PPO needs to maintain two networks simultaneously, GPU memory usage about 1.5-2x single-network methods.

#### 7.2 [Group Relative Policy Optimization](https://arxiv.org/pdf/2402.03300)

In early 2025, DeepSeek-R1 became extremely popular, and equally popular was the GRPO algorithm from the DeepSeekMath paper, also becoming one of the most advanced RL algorithms. However, AI six months equals humanity six months, and by now GRPO has evolved into the baseline algorithm of the great XXPO wars (later evolved DAPO, GSPO, CISPO, etc.). In short, the core innovation is "group relative value estimation."

**GRPO Loss**:

$$\mathcal{L}_{GRPO} = -\mathbb{E}\left[r_t \cdot A_t - \beta \cdot \text{KL}_t\right]$$

Where:
- **Policy term**: $f(r_t) = r_t$ (directly use probability ratio, no clip clipping)
- **Advantage term**: $g(A_t) = \frac{R - \mu_{group}}{\sigma_{group}}$ (within-group normalization, eliminate Critic network)
- **Regularization term**: $h(\text{KL}_t) = \beta \cdot \text{KL}_t$ (token-level KL divergence constraint)

For the same question, the model generates N different answers (for example N=4), then calculates reward scores for these N answers.
Next, use the average reward of these N answers as baseline. Answers above baseline are encouraged, answers below baseline are suppressed.
This cleverly avoids training an additional critic network.

Just as all RL faces the principle limitation of positive and negative samples, GRPO is no exception. Its more significant problem is: degenerate groups (Degenerate Groups).
Suppose a question is slightly difficult, causing N answer reward scores to be nearly identical (usually equally bad rather than equally good), then this group's learning signal approaches zero.
On MiniMind such ultra-small models, this problem is especially obvious. When solving math problems 99.99% of the time the entire group answer quality is poor, then cannot learn.
Therefore, must specify reasonable domain for the model, i.e., must limit within capability boundaries.

**Training**:

```bash
torchrun --nproc_per_node N train_grpo.py
# or
python train_grpo.py
```

> After training, model weight files are saved by default every `100 steps` as: `grpo_*.pth`

| MiniMind2-Small (512dim) | MiniMind2 (768dim) |
|---|---|
| <img src="./images/train_grpo_512.png"> | <img src="./images/train_grpo_768.png"> |

From the training curves, you can see GRPO's **reward shows more stable upward trend**, reaching around 4, indicating GRPO itself better utilizes RLAIF signals. Policy Loss generally decreases smoothly. Compared to PPO's dual-network optimization, GRPO's single-network architecture trains more stably with higher convergence ceiling.

#### 7.3 ⏳⌛️🔥 More RL Extensions (Exp)

##### 7.3.1 [Single-stream Policy Optimization](https://arxiv.org/abs/2509.13232)

SPO is an RL algorithm Tencent proposed in September 2025, improving on GRPO's degenerate group problem.
The paper argues that GRPO and similar algorithms' requirement that "one sample depends on a group of samples" seems awkward and inelegant: too-easy or too-hard questions result in the entire group learning nearly nothing, learning efficiency is inherently limited.
SPO's motivation is to return to RL's essence——**1 input, 1 output, is 1 training sample**, returning to basic policy gradient formulas: can get stable baseline without group mean, i.e., spread value estimate V across time dimension, do rough value pre-estimation before training, update V estimate during training while sampling, thus providing each sample with a persistent, adaptive baseline across batches. This "single-stream" design no longer depends on same-group samples, naturally avoiding degenerate groups.

**SPO Loss**:

$$\mathcal{L}_{SPO} = -\mathbb{E}\left[\log \pi_\theta(a_t|s) \cdot A_t - \beta \cdot \text{KL}_t\right]$$

Where:
- **Policy term**: $f(r_t) = \log \pi_\theta(a_t|s)$ (directly use log probability, don't calculate ratio)
- **Advantage term**: $g(A_t) = R - B_t^{adaptive}$ (adaptive baseline, Beta distribution dynamic tracking)
- **Regularization term**: $h(\text{KL}_t) = \beta \cdot \text{KL}_t$ (token-level KL + dynamic $\rho$ adjustment)

At implementation level: SPO uses non-grouped design, uses persistent KL-adaptive value tracker to replace within-group baseline, advantage functions globally normalized across entire batch. This way each sample processed independently, no need to wait for other same-group samples, yet provides stable learning signals for each sample.
On Qwen3-8B's 5 difficult math datasets, SPO averages 3.4 percentage points higher than GRPO, with BRUMO 25 dataset +7.3pp, AIME 25 dataset +4.4pp.

> Note: SPO is an experimental cutting-edge algorithm, MiniMind's implementation is for exploratory learning. Due to extremely small model parameters, cannot fully reproduce paper's 8B model results.

**Training**:

```bash
torchrun --nproc_per_node N train_spo.py
# or
python train_spo.py
```

> After training, model weight files are saved by default every `100 steps` as: `spo_*.pth`

<div align="center">
<img src="./images/train_spo_768.png">
<p><i>MiniMind2 (768dim) Training Curve</i></p>
</div>

Looking at the training curves, SPO's reward fluctuation is similar to PPO, weaker than GRPO. Actual inference testing found model output quality is not high, with logic confusion and format error issues.

**Experimental Note**: Current SPO hand-implemented version may have problems in value_tracker configuration, reward normalization strategy. Still needs to check algorithm's adaptability on small models/or implementation differences.

### RL Algorithm Summary

We return to the "**unified framework**", reorganizing the table showing all different PO algorithms are just different instantiations of three core components:

| Algorithm | Policy Term $f(r_t)$ | Advantage Term $g(A_t)$ | Regularization Term $h(\text{KL}_t)$ | Optimized Models |
|-----------|----------------|----------------|----------------------|----------|
| **DPO** | $\log r_w - \log r_l$ | Implicit (preference contrast) | Implicit in $\beta$ | 2 |
| **PPO** | $\min(r, \text{clip}(r))$ | $R - V(s)$ | $\beta \cdot \mathbb{E}[\text{KL}]$ | 4 |
| **GRPO** | $r$ | $\frac{R - \mu}{\sigma}$ | $\beta \cdot \text{KL}_t$ | 2 |
| **SPO** | $\log \pi_\theta$ | $R - B_t^{adaptive}$ | $\beta \cdot \text{KL}_t$ | 2 |

**RL is Elegant and Self-Consistent**

> The above is purely personal perspective understanding, corrections welcome anytime

---

## V Training Results

### Completed Training - Model Collection

> Considering multiple reports that Baidu Netdisk is slow, MiniMind2 and later all use ModelScope/HuggingFace hosting.

#### ① Native PyTorch Models

MiniMind2 Model Weights ([ModelScope](https://www.modelscope.cn/models/gongjy/MiniMind2-PyTorch) | [HuggingFace](https://huggingface.co/jingyaogong/MiniMind2-Pytorch))

<details style="color:rgb(128,128,128)">
<summary>Torch File Naming Reference</summary>

| Model Name      | params | pretrain_model         | sft_model              | rlhf_model (DPO)    | reason_model     | rlaif_model (PPO/GRPO/SPO)                    | lora_model         |
|-----------------|--------|------------------------|------------------------|--------------------|------------------|----------------------------------------------|--------------------|
| MiniMind2-small | 26M    | `pretrain_512.pth`     | `full_sft_512.pth`     | `dpo_512.pth`     | `reason_512.pth` | `xxpo_512.pth` | `lora_xxx_512.pth` |
| MiniMind2-MoE   | 145M   | `pretrain_640_moe.pth` | `full_sft_640_moe.pth` | `dpo_640_moe.pth` | -                | -                                            | -                  |
| MiniMind2       | 104M   | `pretrain_768.pth`     | `full_sft_768.pth`     | `dpo_768.pth`     | `reason_768.pth` | `xxpo_768.pth` | `lora_xxx_768.pth` |

</details>

#### ② Transformers Models

MiniMind Series ([ModelScope](https://www.modelscope.cn/collections/MiniMind-b72f4cfeb74b47)
| [HuggingFace](https://huggingface.co/collections/jingyaogong/minimind-66caf8d999f5c7fa64f399e5))

---

# 📌 Eval

## Ⅰ RLHF Comparison

Test based on `full_sft` and `dpo` models of `MiniMind2 series`, with fixed random seeds.

[A] MiniMind2：full_sft_640<br/>
[B] MiniMind2：dpo_640


(deleted since not ready yet)

👉 **Results Summary**

Full_sft models perform better in simplicity and information accuracy; rlhf models tend to provide more background information in answers, but information accuracy needs improvement.
Overall, RLHF-trained models tend to learn: speaking more polite but useless nonsense to please "conversation" itself, while having slight loss in information accuracy.
There's no free lunch. Still need to improve RLHF dataset quality and accept unavoidable model capability losses.
The difference between DPO and online PPO is that reject and chosen are both prepared offline, and necessarily have large distribution differences from minimind model outputs.
Simply put, DPO algorithm makes models watch "video" of table tennis world champion's techniques for RL, rather than like PPO asking reward models to act as "coaches" to correct their techniques for RL.

## Ⅱ RLAIF Comparison

Based on `MiniMind2 (768dim)` with same data and training steps subjective comparison, test random seed fixed at 2026, for reference:

[A] MiniMind-Reason-0.1B (Distillation)<br/>
[B] MiniMind-Reason-0.1B (PPO)<br/>
[C] MiniMind-Reason-0.1B (GRPO)

(deleted since not ready yet)

## Ⅲ Other Model Comparisons

[A] [MiniMind2 (0.1B)](https://www.modelscope.cn/models/gongjy/MiniMind2-PyTorch)<br/>
[B] [MiniMind2-MoE (0.15B)](https://www.modelscope.cn/models/gongjy/MiniMind2-PyTorch)<br/>
[C] [MiniMind2-Small (0.02B)](https://www.modelscope.cn/models/gongjy/MiniMind2-PyTorch)<br/>
[D] [minimind-v1-small(0.02B)](https://pan.baidu.com/s/1_COe0FQRDmeapSsvArahCA?pwd=6666)<br/>
[E] [minimind-v1-moe(0.1B)](https://pan.baidu.com/s/1tqB-GMvuiGQBvEl-yZ-oBw?pwd=6666)<br/>
[F] [minimind-v1(0.1B)](https://pan.baidu.com/s/1p713loS7EfwHQf3G9eYI3Q?pwd=6666)<br/>
[G] [baby-llama2-chinese(0.2B)](https://github.com/DLLXW/baby-llama2-chinese)<br/>
[H] [chatlm-mini-chinese(0.2B)](https://github.com/charent/ChatLM-mini-Chinese)<br/>

(deleted since not ready yet)

---

🙋‍ Let's directly ask DeepSeek-R1 to review and score all the above questions and model answers:

<details style="color:rgb(128,128,128)">
<summary>Detailed Reviews</summary>

### Scoring Criteria:

- **Accuracy**: Whether answers are correct with no obvious errors.
- **Completeness**: Whether answers cover core points of the question.
- **Logicality**: Whether answers are well-organized and follow logic.
- **Code Quality**: Whether code runs normally with clear logic.

### Reviews:

1. **Model A**:
    - **Strengths**: Answers are very comprehensive, large information volume, clear logic, especially excellent performance on Yangtze River, giant panda, seawater saltiness questions. Code has minor flaws but overall thinking is correct.
    - **Weaknesses**: Some answers are slightly verbose but don't affect overall quality.
    - **Summary**: Best overall performance with highest score.

2. **Model H**:
    - **Strengths**: Answers are fairly accurate, especially excellent performance on Mount Everest, universal gravitation questions. Code explanation though incomplete is fairly detailed.
    - **Weaknesses**: Some answers somewhat verbose but logicality is strong.
    - **Summary**: Second only to Model A with stable performance.

3. **Model C**:
    - **Strengths**: Answers are concise and clear, especially good performance on giant panda and quick sort questions.
    - **Weaknesses**: Some answers somewhat brief lacking in-depth explanation.
    - **Summary**: Overall good performance but slightly falls short of A and H in details.

4. **Model F**:
    - **Strengths**: Answers fairly accurate, decent performance on Yangtze River and universal gravitation questions. Code section has certain logicality.
    - **Weaknesses**: Some answers not deep enough, code has minor issues.
    - **Summary**: Performs acceptably with room for improvement.

5. **Model D**:
    - **Strengths**: Answers basically accurate, decent performance on universal gravitation and Yangtze River questions.
    - **Weaknesses**: Some answers too brief, code has obvious errors.
    - **Summary**: Generally adequate performance needing code improvement.

6. **Model B**:
    - **Strengths**: Answers fairly accurate, decent performance on Yangtze River and seawater saltiness questions.
    - **Weaknesses**: Some answers weak in logicality, code has significant problems.
    - **Summary**: Average performance needing further optimization.

7. **Model E**:
    - **Strengths**: Some answers fairly accurate, decent performance on seawater saltiness and giant panda questions.
    - **Weaknesses**: Answers too brief, code almost non-functional.
    - **Summary**: Poor performance needing major improvement.

8. **Model G**:
    - **Strengths**: Almost no obvious strengths.
    - **Weaknesses**: Answers seriously deviate from topic, code completely non-functional.
    - **Summary**: Worst performance needing major improvement.

---

### Summary:

- **Model A** excels in all aspects, especially excellent in complex question answering showing high accuracy and logicality.
- **Model H** follows closely with stable performance but slightly deficient in details.
- **Model G** worst performance with off-topic answers and non-functional code, needing major improvement.

</details>

### Scoring Rankings

| Rank | Model | Accuracy (30 points) | Completeness (30 points) | Logicality (20 points) | Code Quality (20 points) | Total (100 points) |
|----|----|-----------|-----------|-----------|------------|-----------|
| 1  | A  | 28        | 29        | 19        | 20         | 96        |
| 2  | H  | 27        | 28        | 18        | 20         | 93        |
| 3  | C  | 26        | 27        | 18        | 18         | 89        |
| 4  | F  | 25        | 26        | 17        | 18         | 86        |
| 5  | D  | 24        | 25        | 17        | 16         | 82        |
| 6  | B  | 23        | 24        | 16        | 15         | 78        |
| 7  | E  | 22        | 23        | 15        | 14         | 74        |
| 8  | G  | 10        | 12        | 10        | 10         | 42        |

### 👉 Subjective Results Summary

Personal subjective evaluation basically aligns with DeepSeek-R1, where:

* MiniMind series ranking very intuitive, larger parameters + sufficient training data score higher. Hallucinations and errors obviously better than small models.

* Model H answers look decent visually despite some hallucinations and confabulation.

* Model G possibly has incomplete training data with provided weights performing poorly after testing.

* Revisiting the timeless Scaling Law: larger parameters, more training data → stronger model performance.

---

## Ⅳ RoPE Long-text Extrapolation

MiniMind supports RoPE position encoding length extrapolation through YaRN algorithm, enabling models to handle text sequences exceeding training length.
When using `eval_llm.py` for inference, just add `--inference_rope_scaling` parameter to enable RoPE extrapolation:

```bash
python eval_llm.py --weight full_sft --inference_rope_scaling
```

The chart below shows perplexity (PPL) comparison before and after RoPE scaling on different lengths of "Journey to the West" vernacular fiction text. You can see that after enabling RoPE scaling, model performance on long texts is significantly improved.

## Ⅴ Objective Benchmarks

Performance comparisons with other small models on Chinese language leaderboards including C-Eval, CMMLU, A-CLUE, TMMLU+...

Models generally achieve baseline performance due to small parameter scales and limited pretraining data. MiniMind without targeted leaderboard optimization provides fair reference results.

---

# 📌 Others

## Model Conversion

* [./scripts/convert_model.py](./scripts/convert_model.py) enables conversion between `torch models/transformers` models

---

## OpenAI-API Based MiniMind Service Interface

* [./scripts/serve_openai_api.py](./scripts/serve_openai_api.py) provides extremely simple OpenAI-API compatible chat interface, convenient for integration with third-party UIs like FastGPT, Open-WebUI, Dify, etc.

* Download model weights from [Huggingface](https://huggingface.co/collections/jingyaogong/minimind-66caf8d999f5c7fa64f399e5), file structure:
    ```
    <MiniMind-Model-Name> (root dir)
    ├─<MiniMind-Model-Name>
    |  ├── config.json
    |  ├── generation_config.json
    |  ├── LMConfig.py
    |  ├── model.py
    |  ├── pytorch_model.bin
    |  ├── special_tokens_map.json
    |  ├── tokenizer_config.json
    |  ├── tokenizer.json
    ```

* Start chat service
    ```bash
    python serve_openai_api.py
    ```
* Test service interface
    ```bash
    python chat_openai_api.py
    ```
* API interface example, compatible with openai api format
    ```bash
    curl http://ip:port/v1/chat/completions \
      -H "Content-Type: application/json" \
      -d '{ 
        "model": "model-identifier",
        "messages": [ 
          { "role": "user", "content": "What is the highest mountain in the world?" }
        ], 
        "temperature": 0.7, 
        "max_tokens": 512,
        "stream": true
    }'
    ```

## <img src="https://avatars.githubusercontent.com/u/136984999" height="28" style="vertical-align: middle;"/> [vllm](https://github.com/vllm-project/vllm)

vLLM is an extremely popular efficient inference framework supporting fast deployment of large models, optimizing GPU memory usage and throughput.

```bash
vllm serve ./MiniMind2 --model-impl transformers --served-model-name "minimind" --port 8998
```

## <img src="https://user-images.githubusercontent.com/1991296/230134379-7181e485-c521-4d23-a0d6-f7b3b61ba524.png" height="28" style="vertical-align: middle;"/> [llama.cpp](https://github.com/ggerganov/llama.cpp)

llama.cpp is a C++ library that can be used directly from command line, supports multi-threaded inference, and supports GPU acceleration.

After referencing official repository installation, insert at ~760 line in `convert_hf_to_gguf.py`

```text
# Add MiniMind2 tokenizer support
if res is None:
    res = "smollm"
```

Convert custom-trained minimind model -> gguf

```bash
python convert_hf_to_gguf.py ../minimind/MiniMind2/
```

Quantize model

```bash
./build/bin/llama-quantize ../minimind/MiniMind2/MiniMind2-109M-F16.gguf ../minimind/MiniMind2/Q4-MiniMind2.gguf Q4_K_M
```

Command line inference

```bash
./build/bin/llama-cli -m ../minimind/MiniMind2/MiniMind2-109M-F16.gguf --chat-template chatml
```

## <img src="https://ollama.com/public/cloud.png" height="28" style="vertical-align: middle;"/> [ollama](https://ollama.ai)

ollama is a tool for running large models locally, supports multiple open-source LLMs, simple and easy to use.

Load custom gguf model through ollama, create new minimind.modelfile:

```text
FROM ./MiniMind2-109M-F16.gguf
TEMPLATE """{{ if .System }}<|im_start|>system
{{ .System }}<|im_end|>
{{ end }}{{ if .Prompt }}<|im_start|>user
{{ .Prompt }}<|im_end|>
{{ end }}<|im_start|>assistant
"""
```

Load model and name as `minimind2`

```bash
ollama create -f minimind.modelfile minimind2
```

Start inference

```text
ollama run minimind2
> Hello, I am MiniMind2, a model based on xxxxxxxx
```

> For more usage of the above three-party frameworks, please refer to their official documentation 😊

# 📌 Acknowledge

> [!NOTE]
> If you find `MiniMind series` helpful, you can add a ⭐ on GitHub<br/>
> This document is lengthy with limited knowledge. Welcome to discuss in Issues or submit PRs to improve the project<br/>
> Your small support is the motivation to continuously improve this project!

## 🤝 [Contributors](https://github.com/jingyaogong/minimind/graphs/contributors)

<a href="https://github.com/jingyaogong"><img src="https://avatars.githubusercontent.com/u/62287848" width="70px" height="70px"/></a>
&nbsp;
<a href="https://github.com/MuWinds"><img src="https://avatars.githubusercontent.com/u/93832089" width="70px" height="70px"/></a>
&nbsp;
<a href="https://github.com/chuanzhubin"><img src="https://avatars.githubusercontent.com/u/2813798" width="70px" height="70px"/></a>
&nbsp;
<a href="https://github.com/iomgaa-ycz"><img src="https://avatars.githubusercontent.com/u/124225682" width="70px" height="70px"/></a>
&nbsp;

## 😊 Thanks

<a href="https://github.com/ipfgao"><b>@ipfgao</b></a>:
<a href="https://github.com/jingyaogong/minimind/issues/26">🔗 Training Steps Recording</a>

<a href="https://github.com/chuanzhubin"><b>@chuanzhubin</b></a>:
<a href="https://github.com/jingyaogong/minimind/pull/34">🔗 Code Line-by-Line Comments</a>

<a href="https://github.com/WangRongsheng"><b>@WangRongsheng</b></a>:
<a href="https://github.com/jingyaogong/minimind/issues/39">🔗 Large Dataset Preprocessing</a>

<a href="https://github.com/pengqianhan"><b>@pengqianhan</b></a>:
<a href="https://github.com/jingyaogong/minimind/issues/73">🔗 A Simple Tutorial</a>

<a href="https://github.com/RyanSunn"><b>@RyanSunn</b></a>:
<a href="https://github.com/jingyaogong/minimind/issues/75">🔗 Inference Process Learning Record</a>

<a href="https://github.com/Nijikadesu"><b>@Nijikadesu</b></a>:
<a href="https://github.com/jingyaogong/minimind/issues/213">🔗 Interactive Notebook Decomposition of Project Code</a>

<details close> 
<summary> <b>Reference Links & Thanks to the Following Excellent Papers or Projects</b> </summary>

- Ranking does not represent any order
- [https://github.com/meta-llama/llama3](https://github.com/meta-llama/llama3)
- [https://github.com/karpathy/llama2.c](https://github.com/karpathy/llama2.c)
- [https://github.com/DLLXW/baby-llama2-chinese](https://github.com/DLLXW/baby-llama2-chinese)
- [(DeepSeek-V2)https://arxiv.org/abs/2405.04434](https://arxiv.org/abs/2405.04434)
- [https://github.com/charent/ChatLM-mini-Chinese](https://github.com/charent/ChatLM-mini-Chinese)
- [https://github.com/wdndev/tiny-llm-zh](https://github.com/wdndev/tiny-llm-zh)
- [(Mistral-MoE)https://arxiv.org/pdf/2401.04088](https://arxiv.org/pdf/2401.04088)
- [https://github.com/Tongjilibo/build_MiniLLM_from_scratch](https://github.com/Tongjilibo/build_MiniLLM_from_scratch)
- [https://github.com/jzhang38/TinyLlama](https://github.com/jzhang38/TinyLlama)
- [https://github.com/AI-Study-Han/Zero-Chatgpt](https://github.com/AI-Study-Han/Zero-Chatgpt)
- [https://github.com/xusenlinzy/api-for-open-llm](https://github.com/xusenlinzy/api-for-open-llm)
- [https://github.com/HqWu-HITCS/Awesome-Chinese-LLM](https://github.com/HqWu-HITCS/Awesome-Chinese-LLM)

</details>

## 🫶 Supporters

<a href="https://github.com/jingyaogong/minimind/stargazers">
    <picture>
      <source media="(prefers-color-scheme: dark)" srcset="https://reporoster.com/stars/dark/jingyaogong/minimind"/>
      <source media="(prefers-color-scheme: light)" srcset="https://reporoster.com/stars/jingyaogong/minimind"/>
      <img alt="github contribution grid snake animation" src="https://reporoster.com/stars/jingyaogong/minimind"/>
    </picture>
</a>

<a href="https://github.com/jingyaogong/minimind/network/members">
    <picture>
      <source media="(prefers-color-scheme: dark)" srcset="https://reporoster.com/forks/dark/jingyaogong/minimind"/>
      <source media="(prefers-color-scheme: light)" srcset="https://reporoster.com/forks/jingyaogong/minimind"/>
      <img alt="github contribution grid snake animation" src="https://reporoster.com/forks/jingyaogong/minimind"/>
    </picture>
</a>

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://api.star-history.com/svg?repos=jingyaogong/minimind&type=Date&theme=dark"/>
  <source media="(prefers-color-scheme: light)" srcset="https://api.star-history.com/svg?repos=jingyaogong/minimind&type=Date"/>
  <img alt="Star History Chart" src="https://api.star-history.com/svg?repos=jingyaogong/minimind&type=Date"/>
</picture>

# License

The original repository (https://github.com/jingyaogong/minimind/)[https://github.com/jingyaogong/minimind/] is licensed under the [Apache-2.0 License](LICENSE).

Copyright for bible is under (https://github.com/BibleNLP/ebible/tree/main/metadata/licenses)[https://github.com/BibleNLP/ebible/tree/main/metadata/licenses].

I would pick up (https://www.gnu.org/licenses/gpl-3.0.en.html)[https://www.gnu.org/licenses/gpl-3.0.en.html] to avoid any unintened secret commerical targeted modification under the table for the part of my work. I don't think it is a good idea to take away the code to customize secretly for evil companies without telling me.


