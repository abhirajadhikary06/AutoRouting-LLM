# Benchmark Values
Here are the benchmark values from [Hugging Face Open LLM Leaderboard](https://tinyurl.com/2cumu2v8) of the models listed in [README.md](https://github.com/abhirajadhikary06/AutoRouting-LLM/blob/main/README.md) file.

## Large Language Communication Models
| Model Name   | Model Link                                                               | MMLU-Pro | GPQA  | BBH   | MuSR  | IFEval | Precision | Parameters <br>Low | Parameters <br>Mid | Parameters <br>Max | MoE |
|--------------|-------------------------------------------------------------------------|----------|-------|-------|-------|--------|-----------|--------------------|--------------------|--------------------|-----|
| llama3.1 (70b)    | [Llama-3.1-70B-Instruct](https://huggingface.co/meta-llama/Llama-3.1-70B-Instruct) | 47.88    | 14.21 | 55.93 | 17.69 | 86.69  | bfloat16  | 8B                 | 70B                | 405B               | No  |
| deepseek-r1 (70b) | [DeepSeek-R1-Distill-Llama-70B](https://huggingface.co/deepseek-ai/DeepSeek-R1-Distill-Llama-70B) | 41.65    | 2.01  | 35.82 | 13.28 | 43.36  | bfloat16  | 8B                 | 70B                | 671B               | No  |
| hermes-3 (70b) | [Hermes-3-Llama-3.1-70B](https://huggingface.co/NousResearch/Hermes-3-Llama-3.1-70B) | 41.41    | 14.88  | 53.77 | 23.43 | 76.61  | bfloat16  | 8B                 | 70B                | 405B               | No  |

*The data for Large Language Communication model are incurred form [Hugging Face Open LLM Leaderboard](https://tinyurl.com/2cumu2v8)*

## Coding Models
| Model Name                   | Model Link                                                                 | MBPP   | HumanEval | Precision | Parameters <br>Low | Parameters <br>Mid | Parameters <br>Max | MoE |
|------------------------------|---------------------------------------------------------------------------|--------|-----------|-----------|--------------------|--------------------|--------------------|-----|
| qwen2.5-coder-instruct (32b)          | [Qwen2.5-Coder-32B-Instruct](https://huggingface.co/Qwen/Qwen2.5-Coder-32B)        | 47.81  | 12.86     | float16   | 7B                 | 14B                | 32B                | No  |
| deepseek-coder-v2-instruct (16b) | [DeepSeek-Coder-V2-Instruct](https://huggingface.co/deepseek-ai/DeepSeek-Coder-V2-Instruct) | N/A  | N/A     | bfloat16  | 16B                | N/A                | 236B               | Yes |
| codellama-instruct (70b)              | [CodeLlama-70b-Instruct-hf](https://huggingface.co/codellama/CodeLlama-70b-Instruct-hf)     | 62.20   | 67.80       | float16       | 7B                | 34B                | 70B                | No  |