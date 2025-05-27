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

  ### [Swall0w/Torchstat](https://github.com/Swall0w/torchstat)
- Outputs FLOPs, MACs, parameters, and memory.
- Provides a CLI-style per-layer breakdown.
- Useful for analyzing memory bottlenecks and expensive layers.

---

## ⚡ Dynamic Profilers (Runtime and GPU Metrics)

### [cli99/Flops-Profiler](https://github.com/cli99/Flops-Profiler)
- Logs runtime **FLOPs, MACs, latency, and throughput**.
- Supports both CPU and GPU profiling.
- Prints per-layer stats during forward/backward passes.

---

### [PyTorch Profiler (`torch.profiler`)](https://pytorch.org/docs/stable/profiler.html)
- Official PyTorch profiler for **time, memory, and FLOPs**.
- Visualizes results in **TensorBoard** or Chrome Trace.
- Example usage:
  ```python
  with torch.profiler.profile(
      activities=[ProfilerActivity.CPU, ProfilerActivity.CUDA],
      with_flops=True,
      record_shapes=True
  ) as prof:
      model(inputs)

### [DeepSpeed Flops Profiler](https://github.com/microsoft/DeepSpeed)
- Tracks FLOPs, MACs, parameters, and latency per module and device.
- Designed for large-scale models (e.g., BERT, GPT).
- Supports model parallelism and data parallelism in distributed training setups.
- Outputs detailed layer-by-layer statistics during forward and backward passes.

---

### [NVIDIA PyProf](https://github.com/NVIDIA/PyProf)
- A low-level GPU profiler that maps **CUDA kernel traces** to **PyTorch layers**.
- Extracts and analyzes:
  - Tensor Core usage
  - Execution time per kernel
  - Kernel occupancy and efficiency
- Interfaces with NVIDIA tools like **Nsight Systems** and **nvprof**.

---

## 🎯 GPU & Memory Utilities

### [Stonesjtu/pytorch_memlab](https://github.com/Stonesjtu/pytorch_memlab)
- PyTorch-specific CUDA memory analysis toolkit.
- Features:
  - **Line-by-line memory profiling**
  - **Live tensor tracking** (shows shapes, dtypes, sizes)
  - **Peak memory reports** per Python line/function
- Ideal for identifying **OOM errors**, **memory leaks**, and large tensors that dominate memory.

---

## ✅ Summary Table

| Tool                                                                  | FLOPs / MACs | Params | GPU Usage | Memory | Runtime Metrics | Static / Dynamic |
|-----------------------------------------------------------------------|--------------|--------|-----------|--------|------------------|------------------|
| [THOP](https://github.com/Lyken17/pytorch-OpCounter)                  | ✅           | ✅     | ❌        | ❌     | ❌               | Static           |
| [PTFlops](https://github.com/sovrasov/flops-counter.pytorch)         | ✅           | ✅     | ❌        | ❌     | ❌               | Static           |
| [fvcore](https://github.com/facebookresearch/fvcore)                 | ✅           | ✅     | ❌        | ❌     | ❌               | Static           |
| [Calculate-FLOPs](https://github.com/MrYxJ/Calculate-FLOPs)          | ✅           | ✅     | ❌        | ❌     | ❌               | Static           |
| [Torchprofile](https://github.com/zhijian-liu/torchprofile)          | ✅           | ❌     | ❌        | ❌     | ❌               | Static           |
| [Torchstat](https://github.com/Swall0w/torchstat)                    | ✅           | ✅     | ❌        | ✅     | ❌               | Static           |
| [Flops-Profiler](https://github.com/cli99/Flops-Profiler)            | ✅           | ✅     | ✅        | ✅     | ✅               | Dynamic          |
| [torch.profiler](https://pytorch.org/docs/stable/profiler.html)      | ✅           | ✅     | ✅        | ✅     | ✅               | Dynamic          |
| [DeepSpeed](https://github.com/microsoft/DeepSpeed)                  | ✅           | ✅     | ✅        | ✅     | ✅               | Dynamic          |
| [PyProf](https://github.com/NVIDIA/PyProf)                           | ✅           | ✅     | ✅        | ✅     | ✅               | Dynamic          |
| [GPUtil](https://github.com/anderskm/gputil)                         | ❌           | ❌     | ✅        | ✅     | ❌               | Runtime Only     |
| [pytorch_memlab](https://github.com/Stonesjtu/pytorch_memlab)        | ❌           | ❌     | ✅        | ✅     | ❌               | Runtime Only     |




  
