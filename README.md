<div align="center">

<img src="https://raw.githubusercontent.com/Mithijain22/Mithijain22/main/banner-header-final-v4.gif" width="100%" alt="banner"/>

</div>

<br/>

<div align="center">

🌳 = Complete&nbsp;&nbsp;&nbsp;&nbsp;🌱 = Still Growing

</div>

<br/>

## <img src="https://raw.githubusercontent.com/Mithijain22/Mithijain22/main/icon-leaf.png" width="32" valign="middle"/> about me

I'm a CSE undergrad at **VIT Bhopal** who likes building systems that actually get stress-tested before I call them done — distributed systems, backend architecture, and the occasional detour into ML.

I care more about a project surviving a chaos test than looking clean in a demo — you'll notice a lot of what I build gets deliberately broken before I trust it.

- 🔭 Currently building: a from-scratch **DDPM diffusion model** in PyTorch
- 🌾 Background: healthcare backend systems (real-time video consults, prescription APIs) during my internship at Apiero Medica
- ⚙️ Comfort zone: Java/Spring Boot backends, distributed systems, Kafka pipelines, and the AWS/Terraform/Docker stack around them
- ☁️ Fun fact: I've caught more bugs from chaos-testing my own systems than from anyone else's code review

<br/>

<div align="center">
<img src="https://raw.githubusercontent.com/Mithijain22/Mithijain22/main/divider-treeline.jpg" width="100%" alt="divider"/>
</div>

<br/>

## <img src="https://raw.githubusercontent.com/Mithijain22/Mithijain22/main/icon-tree.png" width="32" valign="middle"/> featured projects

**🌳 [Sentinel](https://github.com/Mithijain22/Sentinel) — Real-Time Fraud Detection & Response Platform**
Event-driven Kafka pipeline sustaining ~1,200 events/sec with 0% feature-mismatch rate (down from 6.4%), 94% fraud-burst detection at 1.8% false-positive rate, ~180ms p50 decision latency.

<img src="https://skillicons.dev/icons?i=java,spring,kafka,postgres,aws,docker&theme=light" height="32"/>

<details>
<summary>see details</summary>
<br/>

- Engineered an event-driven microservices pipeline using Apache Kafka to compute real-time features with point-in-time correctness, sustaining ~1,200 events/sec (tested to 50,000-event replay runs) at a 0% feature-mismatch rate, down from 6.4% in the naive/leakage version.
- Achieved 94% fraud-burst detection accuracy with a 1.8% false-positive rate at 180ms (p50) / 640ms (p99) ingest-to-decision latency; orchestrated a saga pattern across services achieving a 99.2% success rate with ~8.4s automatic recovery after a mid-saga service failure.
- Deployed on AWS via Terraform (IaC) with CI/CD (GitHub Actions) and 100% OpenTelemetry tracing coverage; validated via shadow evaluation at 91.3% live/shadow rule agreement and zero duplicate effects across repeated-event chaos tests.

</details>

<br/>

**🌳 [Chronos](https://github.com/Mithijain22/Chronos) — Distributed Job Scheduler (Raft, from scratch)**
Raft consensus implemented from scratch in pure Java 17, zero external dependencies. 13/13 chaos-harness checks passed across a real 5-node, multi-process cluster with zero committed-job loss.

<img src="https://skillicons.dev/icons?i=java&theme=light" height="32"/>

<details>
<summary>see details</summary>
<br/>

- Implemented Raft consensus (leader election, log replication, commit safety, write-ahead persistent log) from scratch in pure Java 17+ with zero external dependencies, using records and sealed interfaces for RPC message types and node states, a hand-rolled JSON parser, and JDK HttpServer/HttpClient transport across a 6-module architecture.
- Verified correctness with a custom test-runner suite and a real 5-node, multi-process chaos harness that kills real OS processes and simulates network partitions, passing 13/13 checks across multiple runs with zero committed-job loss and zero duplicate execution; manually re-verified via a live dashboard with real process kill/restart and partition/heal controls.
- Designed fencing-token idempotency (per-job version numbers) so stale worker reports after reassignment are silently ignored; caught and fixed 4 real concurrency/timing bugs during development, including a stale-leader-reconnect bug and cross-OS fsync timeout tuning.

</details>

<br/>

**🌳 [RL-Based Kubernetes Autoscaler](https://github.com/Mithijain22/rl-kubernetes-autoscaler) — PPO vs. Baseline HPA**
A research-style RL autoscaler benchmarked against real HPA behavior, with a full 8-seed statistical audit — including two self-caught methodology bugs and an honestly-reported negative result.

<img src="https://skillicons.dev/icons?i=python,pytorch&theme=light" height="32"/>

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

**🌳 [Intelligent Java Cache](https://github.com/Mithijain22/Intelligent-Java-Cache) — Multithreaded Adaptive Caching Library**
From-scratch concurrent cache (LRU, LFU, ARC, TinyLFU) sustaining 4M+ ops/sec under 16-thread load with zero data corruption; adaptive layer auto-switches to the best-performing policy live.

<img src="https://skillicons.dev/icons?i=java,spring&theme=light" height="32"/>

<details>
<summary>see details</summary>
<br/>

- Designed a multithreaded, concurrent in-memory caching library from scratch (LRU, LFU, ARC, TinyLFU) using HashMap + doubly linked list core data structures, ReentrantLock-based thread safety, and the Decorator design pattern; sustained 4M+ ops/sec under 16-thread load with zero data corruption across 640K+ operations.
- Built TinyLFU's Count-Min Sketch admission filter, achieving a 100% vs. 0% hot-key survival rate against LRU under scan floods, and a 78.2% vs. 71.8% hit rate (LFU vs. LRU) on Zipfian access patterns.
- Created an adaptive layer that shadow-evaluates all four eviction policies live and auto-switches to the best performer within 1,000 operations; validated with 60+ automated JUnit tests across a 3-module REST/WebSocket architecture.

</details>

<br/>

**🌳 [NovelTea](https://github.com/Mithijain22/NovelTea) — Book Discovery & Recommendation Platform**
Full-stack app with JWT auth and AI-grounded recommendations; cut cached API latency from ~300–800ms to ~1ms with Caffeine caching.

<img src="https://skillicons.dev/icons?i=java,spring,react,postgres,docker&theme=light" height="32"/>

<details>
<summary>see details</summary>
<br/>

- Built a full-stack app (Java, Spring Boot, React) with JWT auth (Spring Security, BCrypt), a PostgreSQL/JPA relational data model (DTO pattern), and Google Books + Gemini LLM API integration for AI-grounded recommendations.
- Cut cached API latency from ~300–800ms to ~1ms using Caffeine caching; containerized with Docker, deployed via Render/Vercel with GitHub Actions CI.

</details>

<br/>

**🌱 [From-Scratch Diffusion Model (DDPM)](https://github.com/Mithijain22/diffusion-project) — Still Growing**
A denoising diffusion probabilistic model built from scratch in PyTorch — no `diffusers` library, no pretrained pipeline — including the forward noising process, a custom U-Net with timestep embeddings, and the reverse sampling loop.

<img src="https://skillicons.dev/icons?i=python,pytorch&theme=light" height="32"/>

<details>
<summary>see details</summary>
<br/>

- Implements the full DDPM pipeline from scratch: closed-form forward noising, a U-Net trained to predict added noise (MSE loss), and step-by-step reverse sampling from pure noise to a coherent image.
- Currently trained at 32×32 resolution on MNIST/Fashion-MNIST, generating recognizable samples, with 64×64 and a sampling-step-count vs. quality/speed comparison planned as next milestones.
- Deliberately scoped for a demoable, understandable implementation over state-of-the-art image quality.

</details>

<br/>

<div align="center">
<img src="https://raw.githubusercontent.com/Mithijain22/Mithijain22/main/divider-flowers.jpg" width="100%" alt="divider"/>
</div>

<br/>

## <img src="https://raw.githubusercontent.com/Mithijain22/Mithijain22/main/icon-cloud.png" width="32" valign="middle"/> tech stack

<div align="center">

<img src="https://skillicons.dev/icons?i=java,python,spring,react,pytorch,aws,docker,terraform,kafka,kubernetes,postgres,mysql,grafana,githubactions&theme=light" />

</div>

<br/>

## <img src="https://raw.githubusercontent.com/Mithijain22/Mithijain22/main/icon-wheat.png" width="32" valign="middle"/> github stats

<div align="center">

<img src="https://github-readme-stats.vercel.app/api?username=Mithijain22&show_icons=true&theme=default&hide_border=true&title_color=6FA96F&icon_color=87CEEB&text_color=444444&bg_color=00000000" width="48%" alt="stats"/>
<img src="https://github-readme-streak-stats.herokuapp.com/?user=Mithijain22&theme=default&hide_border=true&background=00000000&ring=6FA96F&fire=87CEEB&currStreakLabel=6FA96F" width="48%" alt="streak"/>

<br/>

<img src="https://github-readme-stats.vercel.app/api/top-langs/?username=Mithijain22&layout=compact&theme=default&hide_border=true&title_color=6FA96F&text_color=444444&bg_color=00000000" width="45%" alt="top languages"/>

</div>

<br/>

## <img src="https://raw.githubusercontent.com/Mithijain22/Mithijain22/main/icon-sprout.png" width="32" valign="middle"/> let's connect

<div align="center">

[<img src="https://raw.githubusercontent.com/Mithijain22/Mithijain22/main/badge-linkedin.png" height="50"/>](https://linkedin.com/in/mithi-jain-856825330)
[<img src="https://raw.githubusercontent.com/Mithijain22/Mithijain22/main/badge-email.png" height="50"/>](mailto:mithijain220405@gmail.com)
[<img src="https://raw.githubusercontent.com/Mithijain22/Mithijain22/main/badge-resume.png" height="50"/>](https://github.com/Mithijain22/Mithijain22/blob/main/Mithi_Jain_Resume.pdf)

**🌤️ Open to SDE / backend / systems opportunities**

</div>

<br/>

<div align="center">

*"Whenever someone creates something with all of their heart, then that creation is given a soul."* — Hayao Miyazaki

</div>

<br/>

<div align="center">
<img src="https://raw.githubusercontent.com/Mithijain22/Mithijain22/main/banner-footer.jpg" width="100%" alt="footer"/>
</div>
