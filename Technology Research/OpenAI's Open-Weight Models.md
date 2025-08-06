## Overview

* gpt-oss series comprises of [OpenAI’s open-weight models](https://openai.com/open-models) designed for powerful reasoning, agentic tasks, and versatile developer use cases; can be fine-tuned for a variety of specialized use cases
* a "weighted model" is a machine learning model that has been trained and saved with its weights, which are the core numerical values that define the model’s knowledge, behaviors, and responses

## Available Models

* **gpt-oss-120b** — for production, general purpose, high reasoning use cases that fit into a single H100 GPU (117B parameters with 5.1B active parameters); a large open model designed to run in data centers and on high-end desktops and laptops.
* **gpt-oss-20b** — for lower latency, and local or specialized use cases (21B parameters with 3.6B active parameters); a medium-sized open model that can run on most desktops and laptops.

## Highlights

- **Permissive Apache 2.0 license:** Build freely without copyleft restrictions or patent risk—ideal for experimentation, customization, and commercial deployment.
- **Configurable reasoning effort:** Easily adjust the reasoning effort (low, medium, high) based on your specific use case and latency needs.
	- **Low**: Fast responses for general dialogue.
	- **Medium**: Balanced speed and detail.
	- **High**: Deep and detailed analysis.
- **Full chain-of-thought:** Gain complete access to the model’s reasoning process, facilitating easier debugging and increased trust in outputs. It’s not intended to be shown to end users.
- **Agentic capabilities:** Use the models’ native capabilities for function calling, [web browsing](https://github.com/openai/gpt-oss/tree/main?tab=readme-ov-file#browser), [Python code execution](https://github.com/openai/gpt-oss/tree/main?tab=readme-ov-file#python), and Structured Outputs.
- **Native MXFP4 quantization:** The models are trained with native MXFP4 precision for the MoE layer, making `gpt-oss-120b` run on a single H100 GPU and the `gpt-oss-20b` model run within 16GB of memory.

## Advantages

* Ideal for smaller organizations that may lack the budget or flexibility to adopt proprietary models.
* Both models are freely available for download (however, you still pay for the underlying Bedrock usage metered by tokens)
* Both models support external tools to enhance their capabilities and can be used in an agentic workflow.
* Excel at coding, scientific analysis, and mathematical reasoning, with performance comparable to leading alternatives.

## Potential Trade-Offs

* Fine-tuning is complex and may require building a RAG (Retrieval-Augmented Generation) pipeline for context-based reasoning
* Larger models (20B/120B) require GPUs raising hosting cost to minimize latency
* Limited support for function calling and tools in current OSS APIs
* May require initial testing for non-public frameworks (e.g. WPS)

## How to Run

* directly via [Amazon Bedrock](https://aws.amazon.com/blogs/aws/openai-open-weight-models-now-available-on-aws/)
* private LLM instance
	* with [Transformers](https://cookbook.openai.com/articles/gpt-oss/run-transformers) by Hugging Face
	* locally with [Ollama](https://cookbook.openai.com/articles/gpt-oss/run-locally-ollama)
	* with [vLLM](https://cookbook.openai.com/articles/gpt-oss/run-vllm)

## Comparison: Bedrock vs Self-Hosted

| Feature                    | Amazon Bedrock GPT‑OSS    | Self-Hosted on EC2 (vLLM)            |
| -------------------------- | ------------------------- | ------------------------------------ |
| **Upfront setup**          | None                      | Medium/High (model download + infra) |
| **Pricing model**          | Per token (pay-as-you-go) | Per hour (fixed cost)                |
| **Input token cost (20b)** | $0.002 / 1K tokens        | ~$0.0003–0.001 / 1K (est.)*          |
| **Output token cost**      | $0.004 / 1K tokens        | ~$0.0006–0.002 / 1K (est.)*          |
| **Privacy**                | Shared infra, encrypted   | Full control, isolated               |
| **Latency**                | Medium (~300–700ms)       | Lower (esp. if tuned with vLLM)      |
| **Scalability**            | Instantly scalable        | Needs infra planning                 |
| **Maintenance**            | AWS handles everything    | You manage versions, updates         |

## Sample System Architecture using GPT-OSS

1. **Bioptrics Survey App**: collects user repsponses
2. **Preprocessing Layer**: clean input and extract key fields
3. **RAG Retrieval Layer:** pull relevant frameworks and search docs using embeddings
4. **GPT‑OSS Model Server**: self-hosted on a cloud GPU instance; uses vLLM, TGI, or Transformers
5. **Postprocessing Layer**: format as PDF / report and create graphs / apply formatting
6. **Delivery Layer**: store in the org dashboard / Amazon S3 (Simple Storage Service)