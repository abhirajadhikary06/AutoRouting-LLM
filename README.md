# Auto Routing LLM
## References
- **Switch Transformers: Scaling to Trillion Parameter Models with Simple and Efficient Sparsity** (https://arxiv.org/pdf/2101.03961)
- **ROUTOO: LEARNING TO ROUTE TO LARGE LANGUAGE MODELS EFFECTIVELY** (https://openreview.net/pdf?id=RQ9fQLEajC)
- **Fusing LLM Capabilities with Routing Data (matches RouteLLM: Learning to Route LLMs with Preference Data)** (https://arxiv.org/pdf/2507.10540)
- **Universal Model Routing for Efficient LLM Inference** (https://arxiv.org/pdf/2502.08773)
- **Router-R1: Teaching LLMs Multi-Round Routing and Aggregation via Reinforcement Learning** (https://arxiv.org/pdf/2506.09033)
- **Mixture-of-Agents Enhances Large Language Model Capabilities** (https://arxiv.org/pdf/2406.04692)
- **TOWARDS ROBUST MULTI-MODAL REASONING VIA MODEL SELECTION** (https://openreview.net/pdf?id=KTf4DGAzus)

## LLM Benchmark Criterias
### 1. Reasoning and General Knowledge (Core for Prompt Understanding)

* **MMLU (Massive Multitask Language Understanding)**

  * **Metric**: Accuracy (%) on 57 diverse subjects
  * **Method**: Few-shot prompts to simulate real-user queries
  * **Rationale**: Helps route to models strong in knowledge-based prompts

* **GSM8K (Grade School Math)**

  * **Metric**: Accuracy on math word problems
  * **Method**: Include step-by-step reasoning evaluation
  * **Rationale**: Identifies models for analytical or quantitative prompt routing

---

### 2. Coding and Technical Tasks (For Programming-Related Prompts)

* **HumanEval**

  * **Metric**: Pass\@1 (%) for code generation correctness
  * **Method**: Test on Python programming problems
  * **Rationale**: Essential if router handles code prompts (e.g., switch to DeepSeek R1 if scores >80%)

* **MBPP (Mostly Basic Python Problems)**

  * **Metric**: Execution accuracy on basic coding tasks
  * **Rationale**: Complements HumanEval for broader coding evaluation in auto-switching

---

### 3. NLP-Specific Tasks (Classification, Entailment, Reliability)

* **GLUE / SuperGLUE**

  * **Metric**: Average score across sentiment, entailment, etc.
  * **Method**: Frame tasks as text-to-text for models like FLAN-T5
  * **Rationale**: Directly tests classification suitability for routing

* **TruthfulQA**

  * **Metric**: % of truthful answers
  * **Rationale**: Ensures reliable outputs, reduces hallucinations

---

### 4. Efficiency and Deployment Metrics (Critical for Real-Time Routing)

* **Tokens per Second (TPS)**

  * **Metric**: Generation speed (tokens/sec)
  * **Method**: Test on standard hardware (e.g., GPU)
  * **Rationale**: For low-latency switching; prioritize models >30 TPS

* **Time to First Token (TTFT)**

  * **Metric**: Latency (ms) to initial response
  * **Rationale**: Key for user experience; aim for <500ms

* **Memory Usage (VRAM/CPU)**

  * **Metric**: Peak memory during evaluation
  * **Rationale**: Helps select lightweight models (e.g., FLAN-T5) for constrained environments

---

### 5. Specialized for Auto-Routing (Adaptability and Safety)

* **Few-Shot / Zero-Shot Performance (Custom Dataset)**

  * **Metric**: Accuracy on your own 50–100 categorized prompts (e.g., code, chat, math)
  * **Rationale**: Simulates real routing; measures adaptability without fine-tuning

* **Toxicity / Bias Score (ToxiGen, RealToxicityPrompts)**

  * **Metric**: % of toxic or biased outputs
  * **Rationale**: Prevents unsafe routing for sensitive prompts
---

### 6. Hugging Face Open LLM Leaderboard
  * **Link to Open LLM Leaderboard**: https://tinyurl.com/26gprlkk
   - **MMLU-Pro (Massive Multitask Language Understanding - Pro)**: Accuracy (%) on an upgraded version of MMLU with 57 subjects, but harder questions, more answer choices (10 instead of 4), and anti-contamination measures.
   - **GPQA (Graduate-Level Google-Proof Q&A)**: Accuracy on expert-level, non-Googleable questions in physics, chemistry, and biology (diamond subset for high difficulty).
   - **BBH (Big-Bench Hard)**: Accuracy on 23 challenging tasks from Big-Bench (e.g., logical deduction, commonsense reasoning), using few-shot chain-of-thought prompting.
   - **MuSR (Multi-Step Soft Reasoning)**: Accuracy on multi-step reasoning tasks, including murder mysteries, algebra word problems, and object counting, emphasizing step-by-step logic.
   - **IFEval (Instruction-Following Evaluation)**: % of verifiable instructions followed (e.g., "write exactly 3 sentences"), using 500+ prompts at strict and loose levels.
   - **Parameters (Model Size)**: Number of parameters (e.g., 7B, 70B).
   - **Mixture of Experts (MoE)**: Yes/No indicator for MoE architecture.

## Roughly Selected Models
  Models mentioned here are selected on the basis of parameters they are trained on, large models are the best suited for Large Language Communication, Coding, Vision, Embedding, MoE, Lightweight
  ### Large Language Communication
  - **llama3.1 (8B)**: Popular (100.4M pulls), recent (8 months ago), efficient size for testing switching speed on communication prompts.
  - **deepseek-r1 (7B)**: High reasoning performance, supports tools/thinking; benchmark for accuracy on diverse prompts (58.2M pulls, updated 1 month ago).
  - **hermes3 (8B)**: Excels in instruction following and agentic tasks; test for conversational quality in switching scenarios (329.2K pulls).

  ### Coding Models
  - **qwen2.5-coder (7B)**: Latest code-specific model with strong generation/fixing; benchmark on HumanEval for coding accuracy (6.4M pulls, updated 2 months ago).
  - **deepseek-coder-v2 (16B)**: MoE architecture for efficient coding; test inference speed and quality in prompt switching (1M pulls).
  - **codellama (13B)**: Versatile for code discussion/generation; popular for baselines (2.8M pulls).

  ### Multimodal/Vision Models
  - **llava (7B)**: End-to-end multimodal for vision-language; benchmark on VQA if adding image prompts (8.7M pulls).
  - **qwen2.5vl (7B)**: Flagship VL model; test for visual reasoning in hybrid prompts (484.2K pulls, updated 3 months ago).

  ### Embedding Models
  - **nomic-embed-text**: High-performing with large context; benchmark for prompt embedding accuracy (36M pulls).
  - **bge-m3**: Versatile multilingual embeddings; test for routing efficiency (1.9M pulls).

  ### Mixture-of-Experts (MoE) Models
  - **mixtral (8x7B)**: Open MoE for general/coding; benchmark sparsity in switching (1.3M pulls).
  - deepseek-v2 (16B): Economical MoE; test for cost-effective routing (179.4K pulls).

  ### Small/Lightweight Models (<5B Parameters)
  - **phi3.5 (3.8B)**: Lightweight with strong performance; benchmark speed on mobile/edge (315K pulls).
  - **smollm2 (1.7B)**: Compact for quick tests; evaluate in low-resource switching (1.5M pulls).
  - **granite3.1-moe (1B)**: MoE for efficiency; test latency in benchmarks (250.9K pulls).

