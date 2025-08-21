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
| qwen2.5-coder-instruct (32b)          | [Qwen2.5-Coder-32B-Instruct](https://huggingface.co/Qwen/Qwen2.5-Coder-32B-Instruct)        | 90.20  | 92.70     | float16   | 7B                 | 14B                | 32B                | No  |
| deepseek-coder-v2-instruct (16b) | [DeepSeek-Coder-V2-Instruct](https://huggingface.co/deepseek-ai/DeepSeek-Coder-V2-Instruct) | 76.20  | 90.2     | bfloat16  | 16B                | N/A                | 236B               | Yes |
| codellama-instruct (70b)              | [CodeLlama-70b-Instruct-hf](https://huggingface.co/codellama/CodeLlama-70b-Instruct-hf)     | 62.20   | 67.80       | float16       | 7B                | 34B                | 70B                | No  |

*The data for Coding models are incurred from [Qwenlm](https://qwenlm.github.io/blog/qwen2.5-coder-family), [Deepseek Github](https://github.com/deepseek-ai/DeepSeek-Coder), [Meta](https://ai.meta.com/blog/code-llama-large-language-model-coding)*

## Multimodal/Vision (Image Specific) Models
| Model Name  | Model Link | MMMU  | MMMU-Pro | VQAv2 | MathVista | DocVQA | Precision | Parameters <br>Low | Parameters <br>Mid | Parameters <br>Max | MoE |
|------------------------------|---------------------------------------------------------------------------|--------|-----------|-------|-----------|--------|-----------|--------------------|--------------------|--------------------|-----|
| llava-1.5 (7b) | [llava-1.5-7b-hf](https://huggingface.co/llava-hf/llava-1.5-7b-hf)        | 34.20  | N/A       | 78.50  | 54.80      | 58.20    | float16   | N/A                | N/A                | 7B                | No  |
| llama3.2-vision (90b) | [Llama-3.2-90B-Vision](https://huggingface.co/meta-llama/Llama-3.2-90B-Vision) | 60.30  | 45.20     | 78.10  | 57.30      | 90.10    | bfloat16  | 3B                | 11B                | 90B               | No |
| qwen2.5vl-instruct (72b) | [Qwen2.5-VL-72B-Instruct](https://huggingface.co/Qwen/Qwen2.5-VL-72B-Instruct) | 70.20  | 51.10    | 84.90  | 74.80      | 96.40    | auto      | 7B                | 32B                | 72B | No |

*The data for Multimodal/Vision models are incurred from [Llava1.5-Documentation(1)](https://arxiv.org/pdf/2411.10440), [Llava-Documentation(2)](https://arxiv.org/pdf/2310.03744), [Llava-Documentation(3)](https://arxiv.org/html/2503.15621v1), [Meta](https://ai.meta.com/blog/llama-3-2-connect-2024-vision-edge-mobile-devices), [HuggingFace-Qwen2.5VL](https://huggingface.co/Qwen/Qwen2.5-VL-72B-Instruct#image-benchmark)*

## Embedding Models
| Model Name                   | Model Link                                                                 | Embedding Dimension   | HumanEval | Maximum Sequence Length(tokens) | MoE |
|------------------------------|---------------------------------------------------------------------------|--------|-----------|-----------|--------------------|--------------------|--------------------|-----|
| Nomic-Embed-Text-v2-moe (475m)          | [Nomic-Embed-Text-v2](https://huggingface.co/nomic-ai/nomic-embed-text-v2-moe?utm_source=chatgpt.com)        | 768  |      | 512   |  yes  |
| BGE-M3 (568m) | [BGE-M3](https://huggingface.co/BAAI/bge-m3/discussions/60?utm_source=chatgpt.com) | 76.20  | 90.2     | bfloat16  | Yes |
| All-MiniLM-L6-v2 (23m)              | [ll-MiniLM-L6-v2](https://huggingface.co/sentence-transformers/all-MiniLM-L6-v2)     | 62.20   | 67.80       | float16      | No  |

**

## Mixture-of-Experts (MoE) Models
| Model Name  | Model Link | MMLU | BBH | C-Eval | CMMLU | HumanEval | MBPP | GSM8K | Math | Precision | Parameters <br>Low | Parameters <br>Mid | Parameters <br>Max | MoE |
|-------------|------------|------|-----|--------|-------|-----------|------|-------|------|-----------|---------------------|--------------------|--------------------|-----|
| mixtral (8x22b) | [Mixtral-8x22B-v0.1](https://huggingface.co/mistralai/Mixtral-8x22B-v0.1) | 77.80 | 78.40 | 60.00 | 61.00 | 75.00 | 64.40 | 87.90 | 49.80 | float16  | 8x7B  | N/A  | 8x22B | Yes |
| deepseek-v2 (236b) | [DeepSeek-V2](https://huggingface.co/deepseek-ai/DeepSeek-V2) | 78.40 | 81.30 | 80.90 | 82.40 | 76.80 | 70.40 | 90.80 | 52.70 | bfloat16 | 16B   | N/A  | 236B  | Yes |


*The data for Mixture-of-Experts (MoE) models are incurred from [HuggingFace-Deepseek-V2](https://huggingface.co/deepseek-ai/DeepSeek-V2) and [HuggingFace-Mixtral](https://huggingface.co/mistralai/Mixtral-8x22B-v0.1)*