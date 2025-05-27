# 🔍 PyTorch Model Profiling and Efficiency Tools

This document lists the best GitHub repositories for computing model complexity (FLOPs, MACs, parameters), GPU usage, and efficiency metrics for PyTorch models. These tools support static analysis (design time) and dynamic profiling (runtime), with examples for CNNs, Transformers, and more.

---

## 🧮 Static Complexity Analyzers (FLOPs, MACs, Params)

### [Ultralytics THOP (PyTorch-OpCounter)](https://github.com/Lyken17/pytorch-OpCounter)
- Estimates **MACs**, **FLOPs**, and **parameters**.
- Easy integration with PyTorch.
- Supports CNNs and Transformers.
- Example:
  ```python
  from thop import profile, clever_format
  macs, params = profile(model, inputs=(dummy_input,))
  print(*clever_format([macs, params], '%.3f'))
  ```

### [Sovrasov PTFlops (flops-counter.pytorch)](https://github.com/sovrasov/flops-counter.pytorch)
- Provides two backends: `pytorch` (module-based) and `aten` (low-level).
- Estimates theoretical MACs and params.
- Handles Transformers and convolution layers.
- Prints per-layer stats.

---

### [Facebook fvcore](https://github.com/facebookresearch/fvcore)
- Contains `FlopCountAnalysis` for MACs (FLOPs = MACs by their definition).
- Reports total and per-op operation counts.
- Used in [Detectron2](https://github.com/facebookresearch/detectron2).

---

### [MrYxJ Calculate-FLOPs](https://github.com/MrYxJ/Calculate-FLOPs)
- Supports **Linear, CNN, RNN, GCN, BERT, LLAMA**, etc.
- Integrates with HuggingFace models.
- Useful for LLM FLOP analysis:
  ```python
  from calculate_flops import calculate_flops_hf
  calculate_flops_hf("bert-base-uncased")
  ```

  
