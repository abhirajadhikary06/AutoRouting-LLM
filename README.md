# Auto Routing LLM
## References
- Switch Transformers: Scaling to Trillion Parameter Models with Simple and Efficient Sparsity (https://arxiv.org/pdf/2101.03961)
- ROUTOO: LEARNING TO ROUTE TO LARGE LANGUAGE MODELS EFFECTIVELY (https://openreview.net/pdf?id=RQ9fQLEajC)
- Fusing LLM Capabilities with Routing Data (matches RouteLLM: Learning to Route LLMs with Preference Data) (https://arxiv.org/pdf/2507.10540)
- Universal Model Routing for Efficient LLM Inference (https://arxiv.org/pdf/2502.08773)
- Router-R1: Teaching LLMs Multi-Round Routing and Aggregation via Reinforcement Learning (https://arxiv.org/pdf/2506.09033)
- Mixture-of-Agents Enhances Large Language Model Capabilities (https://arxiv.org/pdf/2406.04692)
- TOWARDS ROBUST MULTI-MODAL REASONING VIA MODEL SELECTION (https://openreview.net/pdf?id=KTf4DGAzus)

## LLM Benchmarking and Criterias
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
