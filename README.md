# VistaQA Zero-Shot Grounding Challenge: Team NeuroVision

Predictions and official evaluation results for Team NeuroVision's entry to the VistaQA Zero-Shot Grounding Challenge (VLM4RWD workshop, NeurIPS 2026).

| | GROVE (eps 0.1) | GROVE (eps 0.01) |
|---|---|---|
| Best published system (GPT-5.4-Thinking + SAM 3) | 45.53 | |
| **Ours** | **67.36** | **63.00** |

One zero-shot run over all 1,157 samples, scored with the official VistaQA-Evaluation code at commit `6ad724f` with the Qwen2.5-14B-Instruct judge.

## Files

- `results/predictions.jsonl`: the submitted predictions in the official format (one answer and a list of COCO-RLE instance masks per sample). sha256 `907a8712927aa090a2cec69d7531bc7da92c8487b25a7ab5d5d01e75c6cbbb5c`.
- `results/evaluation_results_eps0.1.json`: official evaluator output at epsilon 0.1.
- `results/evaluation_results_eps0.01.json`: official evaluator output at epsilon 0.01.

## Verify

From the `src` folder of the official evaluator, with Qwen2.5-14B-Instruct served through an OpenAI-compatible endpoint:

```bash
export OPENAI_API_KEY=EMPTY OPENAI_BASE_URL=http://127.0.0.1:8001/v1
python main.py --gt /path/to/gt --pred results/predictions.jsonl --llm_model Qwen2.5-14B-Instruct --epsilon 0.1 --output_dir out
```

The system is described in the challenge report.
