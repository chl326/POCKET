POCKET

Portable Offline Computing Kit for Edge Tasks

Overview

POCKET is a portable, self-powered edge AI system built around the NVIDIA Jetson Orin Nano Super. It is designed for offline, privacy-preserving local inference, battery-powered operation, and access to offline knowledge sources such as Kiwix.

Features
Local LLM inference
Offline knowledge access
Battery-powered operation
Solar-assisted charging
LAN access to hosted AI services
Open-source software stack
Hardware
Jetson Orin Nano Super 8GB
14-inch display
299Wh battery
30W solar panel
2TB NVMe SSD
Bluetooth keyboard
Weatherproof enclosure
Software Stack
Ubuntu 22.04
Ollama
Open WebUI
llama.cpp
Kiwix Desktop
tegrastats monitoring
Repository Structure

Explain each main folder here.

Current Status
Hardware integrated
Local inference working
Battery testing completed
Solar testing in progress
Further optimization ongoing
Results

Briefly summarize:

battery life
tokens/sec
energy per token
LM Studio vs Ollama/Open WebUI findings
Future Work
JetPack 7.x / CUDA 13 support
improved thermal design
tighter RAG integration
solar charging validation
offline document inference from ZIM sources
Authors
Chris Langfitt
Dilen ...
Advisor: Dr. Naher

A few repo tips that will make it look polished:

- Put **photos, diagrams, and graphs** in `docs/images/` or `results/graphs/`
- Keep **raw logs** separate from cleaned CSVs
- Put every bash script in `software/scripts/` with clear names like:
  - `pocket-webmode.sh`
  - `tegrastats-log.sh`
  - `parse_tegrastats.py`
- Add a **BOM file** in `hardware/bill-of-materials/`
- Add a **setup guide** like `docs/setup.md`
- Add a **performance summary** like `results/benchmark-summary.md`

For your first useful commits, I’d do them in this order:

1. Initial repo structure  
2. README draft  
3. Hardware photos and block diagrams  
4. Scripts for web mode and monitoring  
5. Test logs and cleaned CSVs  
6. Graphs and results  
7. Paper / presentation material

For the GitHub landing page, you want people to instantly understand:
- what POCKET is
- why it matters
- what hardware/software it uses
- what results you got

A strong top section could be:

> POCKET is a portable offline AI platform built for privacy-preserving local inference, offline knowledge access, and self-powered edge computing using the Jetson Orin Nano Super.

If you want, I can build you a full **professional README.md** for the POCKET repo that you can paste directly into GitHub.
okay so from all the passed conversations compile a readme

Here’s a clean, professional README.md compiled from everything you’ve worked on with POCKET. You can copy/paste this directly into GitHub.

POCKET

Portable Offline Computing Kit for Edge Tasks

Overview

POCKET is a portable, self-sustaining edge AI system designed to enable offline, privacy-preserving local inference without reliance on cloud services or constant internet access. Built around the NVIDIA Jetson platform, POCKET integrates local large language models (LLMs), offline knowledge sources, and a fully portable power system into a compact, rugged form factor.

The system demonstrates that modern AI workloads can be executed efficiently at the edge while maintaining user control, data privacy, and system independence.

Key Features
🔒 Fully Offline AI Inference (no cloud dependency)
⚡ Battery-Powered Operation (299Wh system)
☀️ Solar-Assisted Charging (30W panel)
🧠 Local LLM Support (DeepSeek, llama.cpp, Ollama)
🌐 LAN-Based Model Access
📚 Offline Knowledge Integration (Kiwix ZIM files)
🗺️ Offline Mapping Support (Organic Maps - in progress)
🧩 Modular & Open-Source Design
System Architecture
Hardware Overview
NVIDIA Jetson Orin Nano Super (8GB)
14" Display
299Wh Portable Power Station
30W Solar Panel
no emojis

Here is your compiled professional README.md without emojis and written in a clean, technical tone suitable for GitHub and your paper.

POCKET

Portable Offline Computing Kit for Edge Tasks

Overview

POCKET is a portable, self-sustaining edge AI system designed to enable offline, privacy-preserving local inference without reliance on cloud services or continuous internet access. Built around the NVIDIA Jetson platform, POCKET integrates local large language models (LLMs), offline knowledge sources, and a portable power system into a compact, rugged form factor.

The system demonstrates that modern AI workloads can be executed efficiently at the edge while maintaining user control, data privacy, and system independence.

Key Features
Fully offline AI inference (no cloud dependency)
Battery-powered operation using a 299Wh power system
Solar-assisted charging via a 30W panel
Local LLM deployment using llama.cpp and Ollama
LAN-based access to hosted models
Offline knowledge access using Kiwix (ZIM files)
Modular and open-source architecture
System Architecture
Hardware
NVIDIA Jetson Orin Nano Super (8GB)
14-inch display
299Wh portable power station
30W solar panel
2TB NVMe SSD (Samsung 990 EVO Plus)
128GB NVMe boot drive (SK hynix BC711)
Bluetooth keyboard
Weatherproof enclosure
Power Subsystem
Internal battery system with AC output
Measured baseline system draw includes conversion losses and peripherals
Display estimated at approximately 7W
Idle system draw observed between approximately 13W–16W at the battery level
Software Stack
Ubuntu 22.04 (JetPack 6.2.1)
Ollama (local model serving)
Open WebUI (browser-based interface)
llama.cpp (CUDA-enabled where supported)
LM Studio (CPU-based inference due to CUDA limitations)
Kiwix Desktop (offline Wikipedia and knowledge bases)
Performance Summary
Model Configuration
Model: DeepSeek 1.5B
Quantization: Q4_KM
LM Studio (CPU-Based)
Throughput: approximately 7.5 tokens/second
Average Power: approximately 8.9W
Total Runtime: approximately 302 seconds
Energy per Token: approximately 1.19 J/token
Behavior: CPU-bound with high EMC utilization
Open WebUI + Ollama (CUDA via llama.cpp)
Throughput: approximately 33–35 tokens/second
Average Power: approximately 17–20W
Energy per Token: approximately 0.4–0.5 J/token
Behavior: significantly improved efficiency and throughput
Reduced memory bandwidth pressure compared to CPU-only inference
Power and Energy Analysis

Energy per token is computed using:

E_total = P_avg × T
E_per_token = E_total / N_tokens

Where:

P_avg is the average power during inference
T is total runtime
N_tokens is total generated tokens

Battery runtime can be approximated as:

t = C / (P_system + P_losses + P_display)

Where:

C = 299 Wh
P_display ≈ 7W
P_losses ≈ 5–6W (conversion and overhead)
Testing Methodology
Metrics Collected
Runtime
Tokens per second
CPU, GPU, and EMC load
Power rails (VDD_IN, VDD_CPU_GPU_CV, VDD_SOC)
Tools Used
tegrastats for logging system metrics
CSV parsing for post-processing
LaTeX (pgfplots) for graph generation
Test Structure
One-hour idle tests across multiple power modes
Inference benchmarking using standardized prompts
Comparison between CPU-only and GPU-accelerated pipelines
Power Modes Tested
7W mode
15W mode
25W mode
