# How to Evaluate LLMs

## Source
YouTube: "AI Engineering Study Notes: Master LLM Evaluations"  
URL: https://youtu.be/Pv4mkG2K_s8?si=fMhjgf9-y296f1zD

## Overview
This note summarizes foundational concepts and practical guidance for evaluating large language model (LLM) applications. It contrasts traditional deterministic software testing with LLM evaluation, explains why informal "vibe testing" is insufficient for production, and outlines evaluation types and operational metrics needed to run reliable LLM systems in production.

## Key Concepts
- AI Engineer: Builds applications and products on top of foundation models / LLMs.
- LLM Evals: Systematic methodology and techniques to evaluate LLM applications for reliability and production readiness.
- Vibe Testing: Informal, subjective testing using a few prompts (e.g., 5–10); non-repeatable and insufficient for production.
- Deterministic vs. Probabilistic Systems:
  - Deterministic: Same input → same output (typical traditional software).
  - Probabilistic: Same input can produce different valid outputs across runs/users (LLMs).
- Golden Dataset & Rubrics: Curated test cases paired with evaluation rules used to build custom eval pipelines.
- Operational Evals: Live monitoring of production metrics (latency, tokens per second, system load, etc.).

## Detailed Explanation
- Why vibe testing fails:
  - Non-repeatable and subjective — results vary by prompt choice and evaluator.
  - Does not capture edge cases, adversarial inputs (prompt injections/jailbreaks), or latent safety/legal risks.
  - Produces false confidence; leads to hallucinations, liability, and public failures when exposed to real users.

- Traditional software testing vs. LLM testing:
  - Determinism: Traditional code is deterministic; testing centers on correctness for given inputs. LLMs are probabilistic, so single-run correctness tests are inadequate.
  - Multidimensional criteria: LLM evaluations must cover factuality, groundedness, completeness, tonality/style, safety, latency, throughput, and cost—not just binary correctness.
  - Continuous monitoring: LLM systems require ongoing operational evaluation post-deployment, not a one-time test-and-release.

- Mindset shift for AI engineers:
  - Move from single-developer projects and "works-for-me" demos to designing robust evaluation pipelines that scale to millions of users.
  - Invest in curated golden datasets, clear rubrics, safety tests, and operational telemetry.

## Examples
- Deterministic vs. Probabilistic behavior:
  - Deterministic: A calculator returning 2 + 2 = 4 every time.
  - Probabilistic: ChatGPT explaining "overfitting" with different valid wording, emphasis, or examples across sessions.

- Real-world production failures (illustrative cases):
  - Air Canada chatbot: Hallucinated that a customer could claim a bereavement refund. Company denied refund; court held the company legally responsible for the chatbot's statement.
  - Chevrolet dealership chatbot: User emotionally manipulated the chatbot to accept a legally binding offer to sell a car for $1 (jailbreak / social engineering).
  - Legal-research hallucination: A lawyer used ChatGPT for precedent research; model fabricated non-existent cases, resulting in a $5,000 fine and loss of the case.

## Code / Commands
- No code snippets, CLI commands, or formulas were provided in this lesson. The video focused on conceptual foundations, case studies, and a 10-topic roadmap for LLM evaluation.

## Practical Applications
- Pre-deployment:
  - Build a golden dataset representing expected inputs, edge cases, adversarial scenarios, and safety tests.
  - Define rubrics for grading outputs across dimensions (factuality, groundedness, completeness, tone, safety).
  - Run domain-specific evaluations: RAG (retrieval-augmented generation) and agentic AI testing.

- Domain-specific evals:
  - RAG Evals: Measure retrieval relevance, groundedness to source documents, and factual consistency between retrieved content and generated responses.
  - Agentic Evals: Test multi-step reasoning, tool invocation correctness, step ordering, and safe failure modes.
  - Safety Evals: Create tests to detect jailbreaks, prompt injections, toxic or disallowed content.

- Post-deployment / Operational:
  - Monitor latency, tokens per second (TPS), time to first token (TTFT), throughput, error rates, and system load.
  - Track drift in model outputs and update golden dataset/rubrics as product behavior and user interactions evolve.

## Common Mistakes / Important Notes
- Relying on vibe testing for production readiness (only 5–10 prompts).
- Treating LLM output like deterministic code—testing only for binary correctness.
- Disowning chatbot output legally/operationally (claiming the chatbot is an independent entity).
- Blindly trusting generated content (e.g., legal precedents, policy statements) without verification.
- Stopping evaluation at launch—neglecting ongoing operational monitoring and reevaluation.

## Key Takeaways
- LLM evaluation is multidimensional and continuous. It must include pre-deployment golden datasets + rubrics, domain-specific tests (RAG, agents), safety checks, and live operational monitoring.
- Vibe testing is useful for early exploration but dangerously insufficient for production.
- Treat chatbots and LLM-powered interfaces as company-controlled outputs—businesses can be held responsible for model-generated statements.
- Build evaluation pipelines that account for probabilistic outputs, adversarial inputs, and operational constraints (latency, cost, throughput).

Sample interview questions to prepare:
- How do you evaluate a RAG application or an agentic AI application before deployment?
- Why is evaluating an LLM application harder than testing traditional software?
- What is "vibe testing" and why is it insufficient for production?
- Which operational metrics should be monitored after deploying an LLM application?

## Quick Revision
- AI Engineer: Builds apps on foundation models.
- Vibe Testing: Informal testing with ~5–10 prompts by feel — non-repeatable and risky.
- Core challenge: Traditional software is deterministic; LLMs are probabilistic and require multidimensional evaluation (factuality, groundedness, completeness, tone, latency, cost).
- Legal point: Courts treat chatbots as company property—companies are responsible for their outputs.
- Evaluation roadmap: Model benchmarks → Custom eval pipelines (golden dataset + rubrics) → RAG evals → Agent evals → Safety evals → Operational evals (latency, TPS, TTFT).