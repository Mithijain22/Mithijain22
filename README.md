<div align="center">

<!-- Banner: use your Ghibli-style scenery image here (the grassy hill / cloud one works great).
     Upload it to an `assets/` folder in this repo, then swap the URL below with its raw GitHub link.
     Keep any character in the scene small/silhouette-scale — it's a mood detail, not the focus. -->
<img src="https://your-image-link-here.com/banner.png" width="100%" alt="banner"/>

<br/>

<img src="https://readme-typing-svg.demolab.com?font=Fira+Code&size=22&duration=3500&pause=1000&color=6FA96F&center=true&vCenter=true&width=650&lines=Hi%2C+I'm+Mithi+%F0%9F%8D%83;CSE+%40+VIT+Bhopal+%7C+Backend+%26+Systems;Building+quietly%2C+like+a+forest+spirit+%F0%9F%8C%B1" alt="typing animation" />

</div>

<br/>

## 🌿 about me

I'm a CSE undergrad at **VIT Bhopal** who likes building systems that actually get stress-tested before I call them done — distributed systems, backend architecture, and the occasional detour into ML.

I care more about a project surviving a chaos test than looking clean in a demo — you'll notice a lot of what I build gets deliberately broken before I trust it.

- 🔭 Currently building: a from-scratch **DDPM diffusion model** in PyTorch
- 🌱 Background: healthcare backend systems (real-time video consults, prescription APIs) during my internship at Apiero Medica
- ⚙️ Comfort zone: Java/Spring Boot backends, distributed systems, Kafka pipelines, and the AWS/Terraform/Docker stack around them
- ☁️ Fun fact: I've caught more bugs from chaos-testing my own systems than from anyone else's code review

<br/>

## 🍃 featured projects

<div align="center">

🚀 = Complete &nbsp;&nbsp;|&nbsp;&nbsp; 🏗️ = In Progress

</div>

<br/>

**🚀 [Sentinel](https://github.com/Mithijain22/Sentinel) — Real-Time Fraud Detection & Response Platform**
Event-driven Kafka pipeline sustaining ~1,200 events/sec with 0% feature-mismatch rate (down from 6.4%), 94% fraud-burst detection at 1.8% false-positive rate, ~180ms p50 decision latency.
`Java` `Spring Boot` `Kafka` `PostgreSQL` `AWS` `Terraform` `Docker` `GitHub Actions` `OpenTelemetry` `Prometheus` `Grafana`

<details>
<summary>see details</summary>
<br/>

- Engineered an event-driven microservices pipeline using Apache Kafka to compute real-time features with point-in-time correctness, sustaining ~1,200 events/sec (tested to 50,000-event replay runs) at a 0% feature-mismatch rate, down from 6.4% in the naive/leakage version.
- Achieved 94% fraud-burst detection accuracy with a 1.8% false-positive rate at 180ms (p50) / 640ms (p99) ingest-to-decision latency; orchestrated a saga pattern across services achieving a 99.2% success rate with ~8.4s automatic recovery after a mid-saga service failure.
- Deployed on AWS via Terraform (IaC) with CI/CD (GitHub Actions) and 100% OpenTelemetry tracing coverage; validated via shadow evaluation at 91.3% live/shadow rule agreement and zero duplicate effects across repeated-event chaos tests.

</details>

<br/>

**🚀 [Chronos](https://github.com/Mithijain22/Chronos) — Distributed Job Scheduler (Raft, from scratch)**
Raft consensus implemented from scratch in pure Java 17, zero external dependencies. 13/13 chaos-harness checks passed across a real 5-node, multi-process cluster with zero committed-job loss.
`Java 17` `Multithreading` `Raft Consensus` `Distributed Systems` `Fault Tolerance`

<details>
<summary>see details</summary>
<br/>

- Implemented Raft consensus (leader election, log replication, commit safety, write-ahead persistent log) from scratch in pure Java 17+ with zero external dependencies, using records and sealed interfaces for RPC message types and node states, a hand-rolled JSON parser, and JDK HttpServer/HttpClient transport across a 6-module architecture.
- Verified correctness with a custom test-runner suite and a real 5-node, multi-process chaos harness that kills real OS processes and simulates network partitions, passing 13/13 checks across multiple runs with zero committed-job loss and zero duplicate execution; manually re-verified via a live dashboard with real process kill/restart and partition/heal controls.
- Designed fencing-token idempotency (per-job version numbers) so stale worker reports after reassignment are silently ignored; caught and fixed 4 real concurrency/timing bugs during development, including a stale-leader-reconnect bug and cross-OS fsync timeout tuning.

</details>

<br/>

**🚀 [RL-Based Kubernetes Autoscaler](https://github.com/Mithijain22/rl-kubernetes-autoscaler) — PPO vs. Baseline HPA**
A research-style RL autoscaler benchmarked against real HPA behavior, with a full 8-seed statistical audit — including two self-caught methodology bugs and an honestly-reported negative result.
`Python` `PyTorch` `Stable-Baselines3` `Gymnasium` `NumPy` `Pandas`

<details>
<summary>see details</summary>
<br/>

Built to test whether a PPO agent that learns traffic patterns can out-scale Kubernetes' reactive HPA — tested across two synthetic traffic distributions plus real Alibaba Cluster Trace 2018 data.

- Built a from-scratch tabular Q-learning agent first to establish reward-shaping fundamentals, then upgraded to PPO via Stable-Baselines3 on a Gymnasium-wrapped simulated cluster environment.
- Caught and fixed two real methodology bugs before trusting any result: a train/eval seed-leakage bug (90% byte-identical "held-out" data) and a real-data sampling bias bug that silently captured only 294 of 4,023 machines from the Alibaba trace.
- Ran a full 8-seed statistical audit with bootstrap confidence intervals — this overturned an earlier "clean win" claim on Distribution A once seed count increased from 3 to 8, and confirmed PPO reliably underperforms baseline on Distribution B (dual daily peaks, frequent small bursts) at 95% confidence.
- Tested an AWARE-inspired behavior-cloning warm start; it consistently made results worse across 3 seeds, and reported that as a legitimate negative result with a root-cause hypothesis (uncalibrated critic) rather than discarding it.
- Ran failure-mode analysis on the worst-performing seeds and found the failure is economic (miscalibrated cost-reliability tradeoff), not behavioral — a more precise diagnosis than "PPO can't generalize."

</details>

<br/>

**🚀 [Intelligent Java Cache](https://github.com/Mithijain22/Intelligent-Java-Cache) — Multithreaded Adaptive Caching Library**
From-scratch concurrent cache (LRU, LFU, ARC, TinyLFU) sustaining 4M+ ops/sec under 16-thread load with zero data corruption; adaptive layer auto-switches to the best-performing policy live.
`Java 17` `ReentrantLock` `Count-Min Sketch` `Spring Boot` `WebSocket` `JUnit`

<details>
<summary>see details</summary>
<br/>

- Designed a multithreaded, concurrent in-memory caching library from scratch (LRU, LFU, ARC, TinyLFU) using HashMap + doubly linked list core data structures, ReentrantLock-based thread safety, and the Decorator design pattern; sustained 4M+ ops/sec under 16-thread load with zero data corruption across 640K+ operations.
- Built TinyLFU's Count-Min Sketch admission filter, achieving a 100% vs. 0% hot-key survival rate against LRU under scan floods, and a 78.2% vs. 71.8% hit rate (LFU vs. LRU) on Zipfian access patterns.
- Created an adaptive layer that shadow-evaluates all four eviction policies live and auto-switches to the best performer within 1,000 operations; validated with 60+ automated JUnit tests across a 3-module REST/WebSocket architecture.

</details>

<br/>

**🚀 [NovelTea](https://github.com/Mithijain22/NovelTea) — Book Discovery & Recommendation Platform**
Full-stack app with JWT auth and AI-grounded recommendations; cut cached API latency from ~300–800ms to ~1ms with Caffeine caching.
`Java` `Spring Boot` `Spring Security` `React` `PostgreSQL` `Docker`

<details>
<summary>see details</summary>
<br/>

- Built a full-stack app (Java, Spring Boot, React) with JWT auth (Spring Security, BCrypt), a PostgreSQL/JPA relational data model (DTO pattern), and Google Books + Gemini LLM API integration for AI-grounded recommendations.
- Cut cached API latency from ~300–800ms to ~1ms using Caffeine caching; containerized with Docker, deployed via Render/Vercel with GitHub Actions CI.

</details>

<br/>

**🏗️ [From-Scratch Diffusion Model (DDPM)](https://github.com/Mithijain22/diffusion-project) — In Progress**
A denoising diffusion probabilistic model built from scratch in PyTorch — no `diffusers` library, no pretrained pipeline — including the forward noising process, a custom U-Net with timestep embeddings, and the reverse sampling loop.
`Python` `PyTorch` `U-Net` `Diffusion Models`

<details>
<summary>see details</summary>
<br/>

- Implements the full DDPM pipeline from scratch: closed-form forward noising, a U-Net trained to predict added noise (MSE loss), and step-by-step reverse sampling from pure noise to a coherent image.
- Currently trained at 32×32 resolution on MNIST/Fashion-MNIST, generating recognizable samples, with 64×64 and a sampling-step-count vs. quality/speed comparison planned as next milestones.
- Deliberately scoped for a demoable, understandable implementation over state-of-the-art image quality.

</details>

<br/>

## 🌤️ tech stack

<div align="center">

![Java](https://img.shields.io/badge/Java-6FA96F?style=for-the-badge&logo=openjdk&logoColor=white)
![Python](https://img.shields.io/badge/Python-87CEEB?style=for-the-badge&logo=python&logoColor=white)
![SpringBoot](https://img.shields.io/badge/Spring_Boot-A9C9A4?style=for-the-badge&logo=springboot&logoColor=white)
![React](https://img.shields.io/badge/React-87CEEB?style=for-the-badge&logo=react&logoColor=white)
![PyTorch](https://img.shields.io/badge/PyTorch-6FA9C9?style=for-the-badge&logo=pytorch&logoColor=white)
<br/>
![AWS](https://img.shields.io/badge/AWS-A9C9A4?style=for-the-badge&logo=amazonaws&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-87CEEB?style=for-the-badge&logo=docker&logoColor=white)
![Terraform](https://img.shields.io/badge/Terraform-6FA96F?style=for-the-badge&logo=terraform&logoColor=white)
![Kafka](https://img.shields.io/badge/Kafka-444444?style=for-the-badge&logo=apachekafka&logoColor=white)
![Kubernetes](https://img.shields.io/badge/Kubernetes-6FA9C9?style=for-the-badge&logo=kubernetes&logoColor=white)
<br/>
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-6FA96F?style=for-the-badge&logo=postgresql&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-87CEEB?style=for-the-badge&logo=mysql&logoColor=white)
![Grafana](https://img.shields.io/badge/Grafana-A9C9A4?style=for-the-badge&logo=grafana&logoColor=white)
![GitHubActions](https://img.shields.io/badge/GitHub_Actions-6FA9C9?style=for-the-badge&logo=githubactions&logoColor=white)

</div>

<br/>

## 🌾 github stats

<div align="center">

<img src="https://github-readme-stats.vercel.app/api?username=Mithijain22&show_icons=true&theme=default&hide_border=true&title_color=6FA96F&icon_color=87CEEB&text_color=444444&bg_color=00000000" width="48%" alt="stats"/>
<img src="https://github-readme-streak-stats.herokuapp.com/?user=Mithijain22&theme=default&hide_border=true&background=00000000&ring=6FA96F&fire=87CEEB&currStreakLabel=6FA96F" width="48%" alt="streak"/>

<br/>

<img src="https://github-readme-stats.vercel.app/api/top-langs/?username=Mithijain22&layout=compact&theme=default&hide_border=true&title_color=6FA96F&text_color=444444&bg_color=00000000" width="45%" alt="top languages"/>

</div>

<br/>

## 🌱 let's connect

<div align="center">

[![LinkedIn](https://img.shields.io/badge/LinkedIn-87CEEB?style=for-the-badge&logo=linkedin&logoColor=white)](https://linkedin.com/in/mithi-jain-856825330)
[![Email](https://img.shields.io/badge/Email-6FA96F?style=for-the-badge&logo=gmail&logoColor=white)](mailto:mithijain220405@gmail.com)
[![Resume](https://img.shields.io/badge/Resume-A9C9A4?style=for-the-badge&logo=googledocs&logoColor=white)](https://github.com/Mithijain22/Mithijain22/blob/main/Mithi_Jain_Resume.pdf)

**🌤️ Open to SDE / backend / systems opportunities**

</div>

<br/>

<div align="center">

*"Whenever someone creates something with all of their heart, then that creation is given a soul."* — Hayao Miyazaki

</div>
