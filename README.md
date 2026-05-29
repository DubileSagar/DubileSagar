<div align="center">

<img width="100%" src="https://capsule-render.vercel.app/api?type=waving&color=0:0a0a0f,30:0d0d2e,60:0f0f4a,100:00d4ff&height=200&section=header&text=Sagar%20Ramesh%20Dubile&fontSize=52&fontColor=ffffff&fontAlignY=55&animation=fadeIn&desc=AI%20Engineer%20%7C%20Security%20%7C%20Blockchain&descAlignY=78&descSize=16&descColor=8ab4f8"/>

<br/>

[![Typing SVG](https://readme-typing-svg.demolab.com?font=JetBrains+Mono&weight=600&size=15&duration=2500&pause=800&color=00D4FF&center=true&vCenter=true&width=780&lines=Hybrid+ML+WAF+blocking+SQLi+%26+XSS+in+real-time.;RAG+pipelines+over+11k+conversations+%E2%80%94+no+LangChain.;94%25+facial+recognition+accuracy+%E2%80%94+production-ready.;Semantic+search+that+understands+meaning%2C+not+keywords.;Smart+contracts+that+can%27t+be+exploited.;SIH+2025+National+Finalist+%C2%B7+IBM+Blockchain+Certified.;Open+to+full-time+roles+%E2%80%94+let%27s+build+something+real.)](https://github.com/DubileSagar)

<br/>

[![Portfolio](https://img.shields.io/badge/Portfolio-sagardubile.dev-00d4ff?style=for-the-badge&logo=firefox&logoColor=white)](https://sagardubile.dev)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/sagar-dubile-2079b0306/)
[![Email](https://img.shields.io/badge/Email-EA4335?style=for-the-badge&logo=gmail&logoColor=white)](mailto:dubile.sagarr@gmail.com)
[![GitHub](https://img.shields.io/badge/GitHub-161b22?style=for-the-badge&logo=github&logoColor=white)](https://github.com/DubileSagar)
[![Visitors](https://komarev.com/ghpvc/?username=DubileSagar&color=00d4ff&style=for-the-badge&label=Profile+Views)](https://github.com/DubileSagar)

</div>

---

<img align="right" width="320" src="https://media.giphy.com/media/qgQUggAC3Pfv687qPC/giphy.gif"/>

### About Me

Final-year CS student at VIT Andhra Pradesh building at the intersection of **AI/ML**, **security**, and **blockchain**. I don't just study these fields — I ship with them.

In the past year: a hybrid ML firewall that blocks zero-day web attacks, two production RAG and semantic search systems built from scratch (no LangChain, no LlamaIndex), a civic AI platform tracking real grievances, a frame-wise CCTV facial recognition pipeline, and production Ethereum smart contracts with gas optimization and security auditing.

I care about systems that work in the real world — not just demos.

```
Location   →  India 🇮🇳
Education  →  B.Tech CS · VIT-AP · CGPA 8.81 / 10
Focus      →  AI Engineering · Security · Blockchain
Status     →  Open to full-time / internship roles 🟢
```

<br clear="both"/>

---

### Projects

<br/>

**🛡️ Sentrix — Hybrid ML-Powered Web Application Firewall**

An enterprise-grade WAF sitting as a transparent reverse proxy in front of any web app — zero code changes required. Every HTTP request passes through a two-stage detection pipeline: 60+ handcrafted regex signatures catch textbook attacks instantly, then a fine-tuned DistilBERT transformer catches obfuscated and zero-day variants that rules alone miss. A decision engine fuses both outputs with calibrated confidence thresholds — conservative by design, because false positives are expensive.

Ships with a real-time WebSocket dashboard (live traffic feed, threat analytics, payload inspector), full SQLite audit trail, Docker Compose for local orchestration, and Kubernetes/GKE manifests for one-click cloud deployment.

> `DistilBERT (fine-tuned)` &nbsp;·&nbsp; `60+ Regex Signatures` &nbsp;·&nbsp; `Reverse Proxy` &nbsp;·&nbsp; `FastAPI` &nbsp;·&nbsp; `Docker` &nbsp;·&nbsp; `Kubernetes / GKE` &nbsp;·&nbsp; `SQLi · XSS · Path Traversal · CMDi`

---

**🧠 KaStack — RAG + Persona System over 11k Conversations**

A production-aware Retrieval-Augmented Generation system built without LangChain or LlamaIndex — every component written from scratch. Ingests 11,000+ multi-turn conversations, detects topic boundaries via cosine similarity drift against the full topic centroid (not a rolling window), builds a multi-dimensional persona in three focused passes, and answers queries using two-stage FAISS retrieval combining topic summaries with raw chunks.

Key design choices: Haiku for bulk summarisation, Sonnet for user-facing chat; FAISS IndexFlatIP for exact cosine search; persona extraction capped at 5k messages for LLM passes while programmatic communication stats run on the full dataset.

> `Two-stage FAISS retrieval` &nbsp;·&nbsp; `Cosine drift topic detection` &nbsp;·&nbsp; `3-pass persona extraction` &nbsp;·&nbsp; `Sentence Transformers` &nbsp;·&nbsp; `FastAPI` &nbsp;·&nbsp; `Built from scratch`

---

**🔍 Neural Semantic Search Engine**

Full semantic retrieval system over the 20 Newsgroups dataset (~18k documents). The core insight: Fuzzy C-Means topic clusters don't just label documents — they power the cache index, turning O(n) lookups into O(n/k). PCA to 50 dims before clustering avoids the curse of dimensionality; an FPC sweep from k=5 to k=25 picks the optimal cluster count automatically.

Result: 1 cache entry serving 4 hits across completely different GPU-buying rephrasings — 71.4% hit rate in demo runs.

> `Fuzzy C-Means · PCA` &nbsp;·&nbsp; `Cluster-bucketed semantic cache` &nbsp;·&nbsp; `ChromaDB` &nbsp;·&nbsp; `FastAPI` &nbsp;·&nbsp; `71.4% hit rate`

---

**🏙️ JanVaani — AI-Powered Civic Grievance Platform**

Brings accountability to civic issue resolution. Citizens report problems, AI auto-classifies and prioritises them, and district-level RBAC dashboards track every complaint through its lifecycle with SLA adherence monitoring.

> `+45% prioritisation accuracy` &nbsp;·&nbsp; `+60% citizen engagement` &nbsp;·&nbsp; `-35% resolution time`

---

**👁️ TraceID — Frame-wise CCTV Facial Recognition**

Identifies missing individuals across CCTV footage. Frame-by-frame face detection, automated timestamp logging, optimised matching pipeline for real-time throughput.

> `94% identification accuracy` &nbsp;·&nbsp; `-70% manual review effort` &nbsp;·&nbsp; `Real-time frame processing`

---

### Experience

**⛓️ Blockchain Engineer Intern — Shamgar Software Solutions**
`Nov 2025 – Mar 2026 · Remote, India`

Production Ethereum smart contract development — not sandboxes, actual contracts through review and deployment pipelines.

- Designed smart contract modules focused on secure, exploit-resistant logic
- Ran gas optimisation passes and vulnerability assessments on existing codebases
- Built unit testing pipelines that caught logic flaws before deployment
- Contributed to decentralised application architecture and security-first code reviews

> `Solidity` &nbsp;·&nbsp; `Ethereum` &nbsp;·&nbsp; `Hardhat` &nbsp;·&nbsp; `Remix` &nbsp;·&nbsp; `Gas Optimisation` &nbsp;·&nbsp; `Contract Auditing`

---

### Tech Stack

<div align="center">

**AI · ML · Security**

![Python](https://img.shields.io/badge/Python-1a1a2e?style=for-the-badge&logo=python&logoColor=4fc3f7)
![PyTorch](https://img.shields.io/badge/PyTorch-1a1a2e?style=for-the-badge&logo=pytorch&logoColor=EE4C2C)
![TensorFlow](https://img.shields.io/badge/TensorFlow-1a1a2e?style=for-the-badge&logo=tensorflow&logoColor=FF6F00)
![HuggingFace](https://img.shields.io/badge/HuggingFace-1a1a2e?style=for-the-badge&logo=huggingface&logoColor=FFD21F)
![Scikit-learn](https://img.shields.io/badge/Scikit--learn-1a1a2e?style=for-the-badge&logo=scikitlearn&logoColor=F7931E)

**RAG · Search · NLP**

![Sentence Transformers](https://img.shields.io/badge/Sentence_Transformers-1a1a2e?style=for-the-badge&logo=pytorch&logoColor=4fc3f7)
![FAISS](https://img.shields.io/badge/FAISS-1a1a2e?style=for-the-badge&logo=meta&logoColor=0467DF)
![ChromaDB](https://img.shields.io/badge/ChromaDB-1a1a2e?style=for-the-badge&logo=databricks&logoColor=FF3621)

**Blockchain & Web3**

![Solidity](https://img.shields.io/badge/Solidity-1a1a2e?style=for-the-badge&logo=solidity&logoColor=a0a0ff)
![Ethereum](https://img.shields.io/badge/Ethereum-1a1a2e?style=for-the-badge&logo=ethereum&logoColor=627EEA)
![Hardhat](https://img.shields.io/badge/Hardhat-1a1a2e?style=for-the-badge&logo=hardhat&logoColor=F7DF1E)
![Web3.js](https://img.shields.io/badge/Web3.js-1a1a2e?style=for-the-badge&logo=web3dotjs&logoColor=F16822)

**APIs · Cloud · Infra**

![FastAPI](https://img.shields.io/badge/FastAPI-1a1a2e?style=for-the-badge&logo=fastapi&logoColor=009688)
![Docker](https://img.shields.io/badge/Docker-1a1a2e?style=for-the-badge&logo=docker&logoColor=2496ED)
![Kubernetes](https://img.shields.io/badge/Kubernetes-1a1a2e?style=for-the-badge&logo=kubernetes&logoColor=326CE5)
![AWS](https://img.shields.io/badge/AWS-1a1a2e?style=for-the-badge&logo=amazonaws&logoColor=FF9900)
![Git](https://img.shields.io/badge/Git-1a1a2e?style=for-the-badge&logo=git&logoColor=F05032)
![SQL](https://img.shields.io/badge/SQL-1a1a2e?style=for-the-badge&logo=postgresql&logoColor=4fc3f7)

</div>

---

### GitHub Activity

<div align="center">

<img height="175" src="https://github-readme-stats.vercel.app/api?username=DubileSagar&show_icons=true&theme=tokyonight&count_private=true&hide_border=true&bg_color=0d1117&title_color=00d4ff&icon_color=7c3aed&text_color=8b949e&ring_color=00d4ff&include_all_commits=true"/>
<img height="175" src="https://github-readme-stats.vercel.app/api/top-langs/?username=DubileSagar&layout=compact&theme=tokyonight&hide_border=true&bg_color=0d1117&title_color=00d4ff&text_color=8b949e&langs_count=8"/>

</div>

<div align="center">

<img width="68%" src="https://github-readme-streak-stats.herokuapp.com/?user=DubileSagar&theme=tokyonight&hide_border=true&background=0d1117&ring=00d4ff&fire=7c3aed&currStreakLabel=00d4ff&sideLabels=8b949e&dates=8b949e&currStreakNum=e6edf3&sideNums=e6edf3"/>

</div>

<div align="center">

[![Activity Graph](https://github-readme-activity-graph.vercel.app/graph?username=DubileSagar&theme=tokyo-night&bg_color=0d1117&color=00d4ff&line=7c3aed&point=e6edf3&area=true&area_color=00d4ff&hide_border=true)](https://github.com/DubileSagar)

</div>

---

### Certifications & Achievements

| | |
|---|---|
| 🏆 Smart India Hackathon 2025 | **National Finalist** — competed among thousands of teams across India |
| 🔗 IBM Blockchain Developer | **Certified** — enterprise-grade blockchain development |
| ☁️ AWS Cloud Foundations | **Certified** |
| ☁️ AWS Cloud Architecting | **Certified** |
| 🎓 B.Tech Computer Science | **CGPA 8.81 / 10** — VIT Andhra Pradesh |

---

### Currently

- 🔭 Building at the intersection of **LLMs, security, and blockchain**
- 📖 Going deeper into **agentic systems**, **LLM fine-tuning**, and **ZK proofs**
- 🤝 Open to **full-time roles**, **research collaborations**, and **open-source projects**
- 💬 Always happy to talk AI, security, Web3, or anything technically interesting

---

<div align="center">

![Snake](https://raw.githubusercontent.com/DubileSagar/DubileSagar/output/github-contribution-grid-snake-dark.svg)

</div>

<div align="center">

*I build things because problems genuinely bother me until they're solved.*

<br/>

[![Portfolio](https://img.shields.io/badge/sagardubile.dev-00d4ff?style=for-the-badge&logo=firefox&logoColor=white)](https://sagardubile.dev)
[![LinkedIn](https://img.shields.io/badge/Connect_on_LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/sagar-dubile-2079b0306/)
[![Email](https://img.shields.io/badge/Send_a_Mail-EA4335?style=for-the-badge&logo=gmail&logoColor=white)](mailto:dubile.sagarr@gmail.com)

</div>

<img width="100%" src="https://capsule-render.vercel.app/api?type=waving&color=0:00d4ff,50:0f0f4a,100:0a0a0f&height=120&section=footer"/>
