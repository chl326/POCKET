# POCKET  
**Portable Offline Computing Kit for Edge Tasks**

## Overview
POCKET is a portable, self-sustaining edge AI system designed to enable offline, privacy-preserving local inference without reliance on cloud services or continuous internet access. Built around the NVIDIA Jetson platform, POCKET integrates local large language models (LLMs), offline knowledge sources, and a portable power system into a compact, rugged form factor.

The system demonstrates that modern AI workloads can be executed efficiently at the edge while maintaining user control, data privacy, and system independence.

---

## Key Features
- Fully offline AI inference (no cloud dependency)  
- Battery-powered operation using a 299Wh power system  
- Solar-assisted charging via a 30W panel  
- Local LLM deployment using llama.cpp and Ollama  
- LAN-based access to hosted models  
- Offline knowledge access using Kiwix (ZIM files)  
- Modular and open-source architecture  

---

## System Architecture

### Hardware
- NVIDIA Jetson Orin Nano Super (8GB)  
- 14-inch display  
- 299Wh portable power station  
- 30W solar panel  
- 2TB NVMe SSD (Samsung 990 EVO Plus)  
- 128GB NVMe boot drive (SK hynix BC711)  
- Bluetooth keyboard  
- Weatherproof enclosure  

### Power Subsystem
- Internal battery system with AC output  
- Measured baseline system draw includes conversion losses and peripherals  
- Display estimated at approximately 7W  
- Idle system draw observed between approximately 13W–16W at the battery level  

---

## Software Stack
- Ubuntu 22.04 (JetPack 6.2.1)  
- Ollama (local model serving)  
- Open WebUI (browser-based interface)  
- llama.cpp (CUDA-enabled where supported)  
- LM Studio (CPU-based inference due to CUDA limitations)  
- Kiwix Desktop (offline Wikipedia and knowledge bases)  

---

## Performance Summary

### Model Configuration
- Model: DeepSeek 1.5B  
- Quantization: Q4_KM  

### LM Studio (CPU-Based)
- Throughput: approximately 7.5 tokens/second  
- Average Power: approximately 8.9W  
- Total Runtime: approximately 302 seconds  
- Energy per Token: approximately 1.19 J/token  
- Behavior: CPU-bound with high EMC utilization  

### Open WebUI + Ollama (CUDA via llama.cpp)
- Throughput: approximately 33–35 tokens/second  
- Average Power: approximately 17–20W  
- Energy per Token: approximately 0.4–0.5 J/token  
- Behavior: significantly improved efficiency and throughput  
- Reduced memory bandwidth pressure compared to CPU-only inference  

---

## Power and Energy Analysis

Energy per token is computed using:

E_total = P_avg × T  
E_per_token = E_total / N_tokens  

Where:
- P_avg is the average power during inference  
- T is total runtime  
- N_tokens is total generated tokens  

Battery runtime can be approximated as:

t = C / (P_system + P_losses + P_display)

Where:
- C = 299 Wh  
- P_display ≈ 7W  
- P_losses ≈ 5–6W (conversion and overhead)  

---

## Testing Methodology

### Metrics Collected
- Runtime  
- Tokens per second  
- CPU, GPU, and EMC load  
- Power rails (VDD_IN, VDD_CPU_GPU_CV, VDD_SOC)  

### Tools Used
- tegrastats for logging system metrics  
- CSV parsing for post-processing  
- LaTeX (pgfplots) for graph generation  

### Test Structure
- One-hour idle tests across multiple power modes  
- Inference benchmarking using standardized prompts  
- Comparison between CPU-only and GPU-accelerated pipelines  

---

## Power Modes Tested
- 7W mode  
- 15W mode  
- 25W mode  
- MAXN SUPER mode  

---

## Repository Structure
```text
POCKET/
├── docs/
├── hardware/
├── software/
├── tests/
├── results/
└── resources/
