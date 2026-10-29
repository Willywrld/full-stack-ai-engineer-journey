# Curriculum — Data-Capable AI/ML Engineer

**Version:** 2.0
**Last updated:** [update this date when you edit]
**Purpose:** Master curriculum and progress tracker for a structured journey from absolute beginner to a data-capable AI/ML engineer.

**Legend**
- 🆕 — atom added in v2.0 (data-capable additions)
- ♻️ — atom refocused in v2.0 (title unchanged, scope adjusted)
- ➡️ — cross-reference to a related atom
- 🔀 — teaching-order note

**How to use this file:** see `USAGE` at the bottom of this document.

---

## Table of Contents

- [Progress Tracker Template](#progress-tracker-template)
- [Status Definitions](#status-definitions)
- [Phase 0 — Setup & Professional Baseline](#phase-0--setup--professional-baseline)
- [Phase 1 — Python Language Core](#phase-1--python-language-core)
- [Phase 2 — DSA & Problem Solving in Python](#phase-2--dsa--problem-solving-in-python)
- [Phase 3 — Testing, Debugging, Quality](#phase-3--testing-debugging-quality)
- [Phase 4 — Backend Engineering](#phase-4--backend-engineering)
- [Phase 5 — Frontend for Full Stack](#phase-5--frontend-for-full-stack)
- [Phase 6 — Databases & Data Modeling](#phase-6--databases--data-modeling)
- [Phase 7 — DevOps, Cloud, CI/CD](#phase-7--devops-cloud-cicd)
- [Phase 8 — Data Engineering & Statistical Analysis (split 8A / 8B)](#phase-8--data-engineering--statistical-analysis)
- [Phase 9 — Math for AI](#phase-9--math-for-ai)
- [Phase 10 — Machine Learning](#phase-10--machine-learning)
- [Phase 11 — Deep Learning](#phase-11--deep-learning)
- [Phase 12 — NLP, LLMs, Transformers](#phase-12--nlp-llms-transformers)
- [Phase 13 — AI Engineering: RAG, Agents, Evals](#phase-13--ai-engineering-rag-agents-evals)
- [Phase 14 — MLOps/LLMOps](#phase-14--mlopsllmops)
- [Phase 15 — System Design & Architecture](#phase-15--system-design--architecture)
- [Phase 16 — Security, Auth, Privacy](#phase-16--security-auth-privacy)
- [Phase 17 — Interview & Career](#phase-17--interview--career)
- [Phase 18 — Capstones](#phase-18--capstones)
- [Recommended Interleaved Sequence for Phase 8](#recommended-interleaved-sequence-for-phase-8)
- [Platforms for Progress, Proof, Collaboration](#platforms-for-progress-proof-collaboration)
- [USAGE](#usage)
- [Changelog](#changelog)

---

## Progress Tracker Template

Maintain one row per atom you've touched. Full list of atoms lives below; the tracker is your *active* progress. Mark status, exercise count, project count, interview-question count, proof artifacts, and a 1–5 confidence rating.

| Atom ID | Title | Status | Exercises | Project | Interview Qs | Proof | Confidence |
|---|---|---|---|---|---|---|---|
| 0.1 | How Python executes code | Not started | 0/70 | 0/1 | 0/20 | — | 1/5 |
| 1.1.53.5 | Higher-level async patterns | Built | 55/70 | 1/1 | 15/20 | ✅ | 4/5 |
| … | | | | | | | |

---

## Status Definitions

- **Not started** — no work begun.
- **Learning** — reading/working through the atom; exercises incomplete; no project yet.
- **Practiced** — most exercises done; project begun or one-off build done.
- **Built** — project complete, tests pass, mini-project merged, blog post drafted.
- **Mastered** — can apply confidently in unfamiliar contexts; interviews answerable from memory; proof published.
- **Taught** — explained to someone else (blog post published, Loom recorded, peer taught).

Move up only when the *previous* status is genuinely earned. Skipping from *Learning* to *Mastered* is self-deception.

---

## Phase 0 — Setup & Professional Baseline

- 0.1 How Python executes code: source, AST, bytecode, CPython, PVM
- 0.2 Install Python, pyenv, venv, pip, uv, poetry
- 0.3 REPL, scripts, notebooks, VS Code, debugger
- 0.4 Project layout, `pyproject.toml`, requirements, lockfiles
- 0.5 Git, GitHub, commits, branches, PRs, code review
- 0.6 Reading docs, PEPs, errors, Stack Overflow correctly
- 0.7 Linting, formatting, type checking, pre-commit
- 0.8 Build-in-public, progress tracking, proof of work
- 🆕 0.9 Notebook tooling: Jupyter, papermill, nbval, nbconvert (reproducible notebooks)
- 🆕 0.10 Data analysis tooling: statsmodels, seaborn, plotly, ydata-profiling, sweetviz

---

## Phase 1 — Python Language Core

- 1.1 Syntax, indentation, comments, statements, expressions
- 1.2 Variables, names, assignment, dynamic typing, mutability
- 1.3 Built-in types: `None`, `bool`, `int`, `float`, `complex`, `str`, `bytes`, `bytearray`
- 1.4 Operators: arithmetic, comparison, logical, bitwise, membership, identity, precedence
- 1.5 I/O, `print`, `input`, f-strings, formatting
- 1.6 Control flow: `if`, `elif`, `else`, `match`/`case`
- 1.7 Loops: `for`, `while`, `break`, `continue`, `else`
- 1.8 Iterables, iterators, `range`, `enumerate`, `zip`, `reversed`, `sorted`
- 1.9 Lists: methods, slicing, comprehensions, copying
- 1.10 Tuples, `namedtuple`, unpacking
- 1.11 Dictionaries: methods, comprehensions, merge, ordering
- 1.12 Sets, `frozenset`, operations
- 1.13 Strings deep: Unicode, encoding, methods, regex intro
- 1.14 Functions: `def`, `return`, parameters, `*args`, `**kwargs`, defaults, keyword-only
- 1.15 Scope: LEGB, `global`, `nonlocal`, closures
- 1.16 Lambda, `map`, `filter`, `reduce`, `functools`
- 1.17 Comprehensions and generators
- 1.18 Iterators and generator functions
- 1.19 Decorators
- 1.20 Context managers
- 1.21 Exceptions: `try`/`except`/`else`/`finally`, `raise`, custom exceptions
- 1.22 Modules and imports
- 1.23 Packages, `__init__`, namespace packages
- 1.24 Virtual environments and dependency management
- 1.25 File I/O, `pathlib`, `os`, `shutil`
- 1.26 JSON, CSV, XML, YAML, pickle
- 1.27 Dataclasses, attrs, Pydantic intro
- 1.28 Type hints: `typing`, mypy, pyright
- 1.29 OOP: classes, objects, attributes, methods
- 1.30 Inheritance, MRO, `super`, composition
- 1.31 Dunder methods, operator overloading
- 1.32 Properties, descriptors, `__slots__`
- 1.33 Metaclasses, ABCs, protocols
- 1.34 Design patterns in Python
- 1.35 Testing: unittest, pytest, fixtures, mocks
- 1.36 Debugging, logging, warnings, assertions
- 1.37 Concurrency: threading, multiprocessing, GIL
- 1.38 Async: asyncio, async/await, tasks, queues
- 1.39 Performance: profiling, `timeit`, `cProfile`, optimization
- 1.40 Python internals: memory, GC, refcount, bytecode

---

## Phase 2 — DSA & Problem Solving in Python

- 2.1 Complexity: Big O, time, space, amortized
- 2.2 Arrays and lists
- 2.3 Strings algorithms
- 2.4 Hash maps and sets
- 2.5 Two pointers
- 2.6 Sliding window
- 2.7 Stacks
- 2.8 Queues and deques
- 2.9 Linked lists
- 2.10 Recursion
- 2.11 Backtracking
- 2.12 Sorting
- 2.13 Binary search
- 2.14 Trees
- 2.15 Binary search trees
- 2.16 Heaps and priority queues
- 2.17 Graphs: BFS, DFS
- 2.18 Shortest paths
- 2.19 Union-Find
- 2.20 Tries
- 2.21 Greedy
- 2.22 Dynamic programming 1D
- 2.23 Dynamic programming 2D
- 2.24 Bit manipulation
- 2.25 Math algorithms
- 2.26 Interval problems
- 2.27 Matrix problems
- 2.28 Topological sort
- 2.29 Advanced graph algorithms
- 2.30 Interview patterns capstone

---

## Phase 3 — Testing, Debugging, Quality

- 3.1 Unit testing
- 3.2 Integration testing
- 3.3 End-to-end testing
- 3.4 Test doubles, mocks, stubs, fakes
- 3.5 Property-based testing
- 3.6 Coverage and mutation testing
- 3.7 Debugging strategies
- 3.8 Logging and observability
- 3.9 Error handling architecture
- 3.10 Static analysis and type checking
- 3.11 Code review standards
- 3.12 Technical debt and refactoring

---

## Phase 4 — Backend Engineering

- 4.1 HTTP, REST, status codes, headers
- 4.2 FastAPI basics
- 4.3 Pydantic models and validation
- 4.4 Dependency injection
- 4.5 Routing, middleware, CORS
- 4.6 Authentication: sessions, JWT, OAuth2
- 4.7 Authorization: RBAC, ABAC
- 4.8 SQLAlchemy and ORMs
- 4.9 Alembic migrations
- 4.10 Background tasks
- 4.11 WebSockets
- 4.12 GraphQL
- 4.13 gRPC
- 4.14 Caching: Redis, in-memory
- 4.15 Rate limiting
- 4.16 Pagination, filtering, sorting
- 4.17 API versioning
- 4.18 Idempotency
- 4.19 File uploads
- 4.20 Email and notifications
- 4.21 Payment integration
- 4.22 Django deep dive
- 4.23 Flask deep dive
- 4.24 Microservices vs monolith
- 4.25 Backend capstone

---

## Phase 5 — Frontend for Full Stack

- 5.1 HTML semantics
- 5.2 CSS layout: flexbox, grid
- 5.3 Responsive design
- 5.4 JavaScript fundamentals
- 5.5 TypeScript fundamentals
- 5.6 DOM and events
- 5.7 Fetch and APIs
- 5.8 React fundamentals
- 5.9 React state and hooks
- 5.10 React Router
- 5.11 Forms and validation
- 5.12 State management
- 5.13 Next.js
- 5.14 Server components
- 5.15 Authentication on frontend
- 5.16 Accessibility
- 5.17 Performance
- 5.18 Testing frontend
- 5.19 Deployment
- 5.20 Full-stack capstone

---

## Phase 6 — Databases & Data Modeling

- 6.1 Relational model
- 6.2 SQL basics
- 6.3 Joins
- 6.4 Indexes
- 6.5 Transactions and ACID
- 6.6 Normalization
- 6.7 PostgreSQL deep dive
- 6.8 SQLite
- 6.9 NoSQL: MongoDB, Redis
- 6.10 Vector databases
- 6.11 Data modeling for apps
- 6.12 Query optimization
- 6.13 Migrations
- 6.14 Backups and recovery
- 6.15 Database capstone
- 🆕 6.16 Analytics SQL: window functions, CTEs, cohort analysis, funnel analysis, retention queries, time-based aggregations

---

## Phase 7 — DevOps, Cloud, CI/CD

- 7.1 Linux basics
- 7.2 Shell scripting
- 7.3 Docker
- 7.4 Docker Compose
- 7.5 CI/CD with GitHub Actions
- 7.6 Cloud basics: AWS/GCP/Azure
- 7.7 Deployment: Render, Railway, Fly.io, Vercel
- 7.8 Nginx and reverse proxy
- 7.9 Environment variables and secrets
- 7.10 Monitoring and logging
- 7.11 Infrastructure as Code
- 7.12 Kubernetes basics
- 7.13 Scaling
- 7.14 Cost optimization
- 7.15 DevOps capstone

---

## Phase 8 — Data Engineering & Statistical Analysis

**Phase 8 is split into two strands.**

- **8A — Data Engineering.** How to move, clean, store, and serve data at scale.
- **8B — Statistical Analysis, Inference & Causal Reasoning.** How to reason about data, run experiments, infer causation, and communicate findings.

Both strands are required for a data-capable AI/ML engineer. They interleave — see *Recommended Interleaved Sequence for Phase 8* below.

### Phase 8A — Data Engineering

- 8.1 NumPy
- 8.2 Pandas
- 8.3 Polars
- 8.4 Data cleaning
- 8.5 ETL/ELT
- 8.6 Airflow / Prefect
- 8.7 Data warehouses
- 8.8 Spark basics
- 8.9 Streaming
- 8.10 Data quality
- 8.11 Visualization (engineering-flavored: matplotlib, seaborn, plotly fundamentals — for *analysis depth see 8b.9*)
- 8.12 Statistical analysis (baseline intro — expanded fully in Phase 8B)
- 8.13 A/B testing (baseline intro — expanded fully in 8b.14–8b.15)
- 8.14 Feature stores
- 8.15 Data engineering capstone

### Phase 8B — Statistical Analysis, Inference & Causal Reasoning

**5 tracks. Track order is the teaching order within the track; tracks interleave with 8A (see recommended sequence).**

#### Track 1 — Foundations

- 🆕 8b.1 Descriptive statistics & data profiling
- 🆕 8b.2 Probability distributions in practice
- 🆕 8b.3 Sampling, CLT, standard error, bootstrap
- 🆕 8b.4 Confidence intervals
- 🆕 8b.5 Hypothesis testing fundamentals
- 🆕 8b.6 Common statistical tests
- 🆕 8b.7 Multiple comparisons & FDR
- 🆕 8b.8 Exploratory Data Analysis (EDA) workflow
- 🆕 8b.9 Visualization for analysis

#### Track 2 — Regression & Experimentation

- 🆕 8b.10 Regression as inference (statsmodels)
- 🆕 8b.11 Regression diagnostics & assumptions
- 🆕 8b.12 Logistic regression as inference
- 🆕 8b.13 GLMs beyond logistic (Poisson, negative binomial)
- 🆕 8b.14 A/B testing: design
- 🆕 8b.15 A/B testing: analysis & pitfalls

#### Track 3 — Causal Inference & Bayesian

- 🆕 8b.16 Causal inference foundations
- 🆕 8b.17 Quasi-experimental methods (DiD, PSM, IV, RDD)
- 🆕 8b.18 Bayesian inference basics

#### Track 4 — Time Series & Communication

- 🆕 8b.19 Analytics SQL (taught from analysis perspective; the atom lives at `6.16` but is reinforced here) ➡️ 6.16
- 🆕 8b.20 Time series analysis
- 🆕 8b.21 Data storytelling & communication
- 🆕 8b.22 Data analysis capstone

### Atom scope reference (Phase 8B)

- **8b.1** — Mean/median/mode, variance, std, quantiles, IQR, skewness, kurtosis, robust stats, missing-data patterns (MCAR/MAR/MNAR), outlier detection, automated profiling.
- **8b.2** — Normal, binomial, Poisson, exponential, uniform, log-normal, power law; Q-Q plots; distribution fitting; sampling from distributions.
- **8b.3** — Population vs sample; sampling distributions; CLT (what it does and doesn't say); standard error vs std; bootstrap resampling.
- **8b.4** — CIs for means, differences, proportions; correct interpretation; bootstrapped CIs; frequentist vs Bayesian credible intervals.
- **8b.5** — Null vs alternative; p-values (correct interpretation); Type I/II errors; statistical power; effect sizes; practical vs statistical significance.
- **8b.6** — t-tests, chi-square, Mann-Whitney, Wilcoxon, ANOVA; decision tree for choosing the right test.
- **8b.7** — Multiple-testing problem; Bonferroni, Holm, Benjamini-Hochberg; when to correct and when not to.
- **8b.8** — Univariate → bivariate → multivariate; missingness, outliers, distributions; Pearson, Spearman, Cramér's V; full case study.
- **8b.9** — matplotlib vs seaborn vs plotly; distribution, box, violin, pair, heatmap; small multiples; chart critique; analysis-viz vs stakeholder-viz.
- **8b.10** — OLS coefficients, standard errors, t-stats, p-values, CIs, R²/adjusted R², F-stat; sklearn vs statsmodels.
- **8b.11** — Linearity, independence, homoscedasticity, residual normality; residual and Q-Q plots; multicollinearity (VIF); influential points (Cook's distance, leverage).
- **8b.12** — Odds and odds ratios; coefficient interpretation; marginal effects; statsmodels vs sklearn.
- **8b.13** — Poisson regression; negative binomial; zero-inflated models.
- **8b.14** — Primary/secondary/guardrail metrics; MDE and sample size; randomization and stratification; pre-registration.
- **8b.15** — Frequentist (t-test, z-test) and Bayesian (beta-binomial) analysis; peeking; sequential testing; multiple-metric problem; novelty/primacy; Simpson's paradox.
- **8b.16** — Correlation vs causation; potential-outcomes framework; ATE/ATT/CATE; confounding; DAGs and backdoor criterion; colliders and mediators.
- **8b.17** — Difference-in-differences; propensity-score matching; synthetic control; IV; RDD; sensitivity analysis.
- **8b.18** — Priors, likelihoods, posteriors; conjugate priors; Bayesian A/B testing; when Bayesian beats frequentist; PyMC/Stan conceptual.
- **8b.19** — Window functions; cohort and retention queries; funnel analysis; time-based aggregations. ➡️ 6.16
- **8b.20** — Stationarity, differencing; decomposition; exponential smoothing, Holt-Winters; ARIMA family; MAPE, MASE, backtesting.
- **8b.21** — Audience analysis; executive-summary structure; chart selection for narrative; reports vs slides; dashboards (Streamlit, Plotly Dash).
- **8b.22** — End-to-end capstone: pick a public dataset, full EDA, hypothesis testing, causal reasoning where possible, written report + executive summary + 5-min Loom.

---

## Phase 9 — Math for AI

♻️ **Refocus note (v2.0):** applied statistics now lives in Phase 8B. In Phase 9, `9.4 Probability` becomes the *theory* of probability (random variables, joint distributions, expectation) and `9.5 Statistics` becomes *estimation theory* (MLE, sufficient statistics, asymptotic properties). Do not duplicate 8B content — reference it.

- 9.1 Linear algebra
- 9.2 Matrix operations
- 9.3 Calculus and gradients
- ♻️ 9.4 Probability (refocused: RVs, joint distributions, expectation)
- ♻️ 9.5 Statistics (refocused: estimation theory, MLE, sufficient statistics)
- 9.6 Optimization
- 9.7 Information theory
- 9.8 Linear regression math
- 9.9 Logistic regression math
- 9.10 Neural network math
- 9.11 Backpropagation
- 9.12 Evaluation metrics

---

## Phase 10 — Machine Learning

➡️ **Cross-references to Phase 8B (v2.0):**
- `10.4 Regression` — pair with `8b.10`, `8b.11`
- `10.12 Model evaluation` — pair with `8b.5`
- `10.19 Time series` — pair with `8b.20` (ML-overview here; depth in 8B)

- 10.1 ML lifecycle
- 10.2 Supervised learning
- 10.3 Unsupervised learning
- 10.4 Regression ➡️ 8b.10, 8b.11
- 10.5 Classification
- 10.6 Clustering
- 10.7 Dimensionality reduction
- 10.8 Decision trees
- 10.9 Random forests
- 10.10 Gradient boosting
- 10.11 SVM
- 10.12 Model evaluation ➡️ 8b.5
- 10.13 Cross-validation
- 10.14 Hyperparameter tuning
- 10.15 Feature engineering
- 10.16 Imbalanced data
- 10.17 Scikit-learn pipelines
- 10.18 Recommendation systems
- 10.19 Time series ➡️ 8b.20
- 10.20 ML capstone

---

## Phase 11 — Deep Learning

- 11.1 Perceptrons
- 11.2 Neural networks
- 11.3 Activation functions
- 11.4 Loss functions
- 11.5 Optimizers
- 11.6 Regularization
- 11.7 PyTorch basics
- 11.8 Training loops
- 11.9 CNNs
- 11.10 RNNs
- 11.11 LSTMs
- 11.12 Attention
- 11.13 Transformers
- 11.14 Transfer learning
- 11.15 Fine-tuning
- 11.16 GPU training
- 11.17 Model compression
- 11.18 Deep learning capstone

---

## Phase 12 — NLP, LLMs, Transformers

- 12.1 Text preprocessing
- 12.2 Tokenization
- 12.3 Embeddings
- 12.4 Word2Vec/GloVe
- 12.5 Transformer architecture
- 12.6 BERT
- 12.7 GPT
- 12.8 Hugging Face
- 12.9 Prompt engineering
- 12.10 Fine-tuning LLMs
- 12.11 LoRA/QLoRA
- 12.12 Quantization
- 12.13 RLHF
- 12.14 Evaluation
- 12.15 Hallucination mitigation
- 12.16 Safety and alignment
- 12.17 Multimodal models
- 12.18 Open-source LLMs
- 12.19 LLM APIs
- 12.20 NLP/LLM capstone

---

## Phase 13 — AI Engineering: RAG, Agents, Evals

- 13.1 AI engineering architecture
- 13.2 Vector embeddings
- 13.3 Vector databases
- 13.4 Chunking strategies
- 13.5 Retrieval
- 13.6 RAG pipelines
- 13.7 Hybrid search
- 13.8 Reranking
- 13.9 Query rewriting
- 13.10 Agents
- 13.11 Tool calling
- 13.12 Function calling
- 13.13 Multi-agent systems
- 13.14 Memory
- 13.15 Guardrails
- 13.16 Evals
- 13.17 Observability
- 13.18 Cost tracking
- 13.19 Latency optimization
- 13.20 Prompt versioning
- 13.21 AI app backend
- 13.22 AI app frontend
- 13.23 Deployment
- 13.24 Security
- 13.25 AI engineering capstone

---

## Phase 14 — MLOps/LLMOps

- 14.1 Experiment tracking
- 14.2 Model registry
- 14.3 Feature store
- 14.4 Model serving
- 14.5 Batch inference
- 14.6 Real-time inference
- 14.7 Monitoring drift
- 14.8 LLM observability
- 14.9 Prompt ops
- 14.10 CI/CD for ML
- 14.11 A/B testing models
- 14.12 Rollbacks
- 14.13 Governance
- 14.14 Compliance
- 14.15 MLOps capstone

---

## Phase 15 — System Design & Architecture

- 15.1 Requirements and constraints
- 15.2 Load balancing
- 15.3 Caching strategies
- 15.4 Databases at scale
- 15.5 Message queues
- 15.6 Event-driven architecture
- 15.7 Microservices
- 15.8 Monoliths
- 15.9 API gateways
- 15.10 Consistency patterns
- 15.11 Fault tolerance
- 15.12 Observability
- 15.13 Security architecture
- 15.14 AI system design
- 15.15 System design capstone

---

## Phase 16 — Security, Auth, Privacy

- 16.1 OWASP Top 10
- 16.2 Password storage
- 16.3 JWT and sessions
- 16.4 OAuth2/OIDC
- 16.5 Input validation
- 16.6 SQL injection
- 16.7 XSS/CSRF
- 16.8 Secrets management
- 16.9 Encryption
- 16.10 Privacy and compliance

---

## Phase 17 — Interview & Career

- 17.1 Resume and portfolio
- 17.2 GitHub profile
- 17.3 LinkedIn
- 17.4 Behavioral interviews
- 17.5 Python interviews
- 17.6 DSA interviews
- 17.7 Backend interviews
- 17.8 Full-stack interviews
- 17.9 ML/AI interviews
- 17.10 System design interviews
- 17.11 Take-home projects
- 17.12 Salary negotiation
- 🆕 17.13 Data-science interview prep

---

## Phase 18 — Capstones

- 18.1 Python CLI tool
- 18.2 Production REST API
- 18.3 Full-stack SaaS
- 18.4 Real-time app
- 18.5 Data pipeline
- 18.6 ML product
- 18.7 RAG knowledge assistant
- 18.8 AI agent platform
- 18.9 MLOps platform
- 18.10 Open-source contribution
- 🆕 18.11 Data Analysis & Decision Support Report (portfolio capstone: full EDA → hypothesis test → causal reasoning → executive summary + dashboard)

---

## Recommended Interleaved Sequence for Phase 8

Do not do all of 8A, then all of 8B. Interleave so each strand feeds the other.

1. **8A.1–8A.4** (NumPy, Pandas, Polars, Cleaning) — you need data-handling before statistics.
2. **8B.1–8B.9** (Foundations) — apply statistics on data you can now manipulate.
3. **8A.5–8A.15** (ETL, warehouses, Spark, streaming, data quality, feature stores, capstone) — engineering depth.
4. **8B.10–8B.22** (Regression, experimentation, causal, Bayesian, time series, storytelling, capstone) — advanced applied statistics.

This creates a T-shape: engineering breadth, statistical depth, meeting in the middle. When you reach Phase 9 (Math) and Phase 10 (ML), you already have a practitioner's foundation — the math will feel grounded, not abstract.

**Cross-phase note:** `6.16 Analytics SQL` can be taught immediately after `6.3 Joins` (it needs JOINs to be useful), but the *deep* analytics-SQL practice happens alongside `8b.19`.

---

## Platforms for Progress, Proof, Collaboration

- **Code/proof:** GitHub, GitLab, Codeberg
- **Practice:** Exercism, LeetCode, HackerRank, Codewars, CodeSignal
- **Data/ML practice:** Kaggle, Hugging Face, Weights & Biases
- **Statistics practice:** OpenIntro Statistics exercises, Statistical Rethinking (McElreath), Cross Validated (Stack Exchange)
- **Deploy:** Vercel, Render, Railway, Fly.io, AWS, GCP, Azure
- **Writing:** Dev.to, Hashnode, Medium, personal blog
- **Video/demo:** Loom, YouTube, TikTok/Shorts
- **Networking:** LinkedIn, X, Discord, Reddit, GitHub Discussions
- **Collaboration:** open source, pair programming, hackathons, Kaggle competitions, code reviews
- **Proof artifacts:** README, tests, CI badge, deployment URL, architecture diagram, ADR, benchmark, blog post, demo video, notebook with output

---

## USAGE

### Where to save

Save this file in a dedicated folder, e.g. `~/learning/curriculum.md`. Keep it in the root of your learning repo (the same repo where you track progress). If you want to keep the same file across machines, put it in a synced folder or a private GitHub repo.

### How to read it

- **Before starting any atom**, look up its ID here to confirm the title, phase, and cross-references. If the atom has a `🆕` marker, it's a v2.0 addition — the scope is described either in the phase list or in the "Atom scope reference" section (Phase 8B has the fullest scope list).
- **If the atom has a `♻️` marker**, check the refocus note directly under the phase heading — the title is the same, but the *scope* is narrower than the original. Do not re-teach the parts that moved to 8B.
- **If the atom has a `➡️` cross-reference**, treat the referenced atom as a sibling — read or re-read it after finishing this one.

### How to keep it current

- Add a **new row** to the Progress Tracker Template as soon as you start an atom. Don't wait until it's done.
- Update the row after every study session. Two minutes of updating prevents weeks of "wait, where was I?"
- Use the **Status Definitions** literally. If you can't teach the atom to someone else, it's not *Mastered*.
- **Confidence rating (1–5)** is for you, not for show. Be honest: 5/5 means you could pass an interview on it tomorrow. 3/5 means you can use it with references open. 1/5 means you'd need to re-read the atom.

### How it pairs with the atom template

This file tells you *what* to learn next. The `atom-template-general.md` file tells you *how* to have that atom taught to you, chunk by chunk, with checkpoints. The two files are used together:

1. **Open `curriculum.md`.** Find the next atom.
2. **Open `atom-template-general.md`.** Fill in the atom's ID, title, phase, prerequisites.
3. **Send the template to your AI tutor.** The tutor delivers the atom in chunks, paused at checkpoints.
4. **Answer each checkpoint** in your own words, or say "Continue" if you're confident.
5. **When the atom is done**, come back to `curriculum.md` and update the tracker row (status, exercise count, project, proof artifacts, confidence).
6. **Commit both files to your repo** with a message like `atom(1.1.53.6): complete checkpoint 3, tracker updated`. This is your build-in-public trail.

### How to handle additions and changes

- **Never delete existing atom IDs.** Even if an atom is superseded, keep the row with status `Superseded by X.Y` and a date. This prevents your tracker from becoming a graveyard of orphaned IDs.
- **New atoms get new IDs at the end of their phase** (e.g., `6.16` after `6.15`). Never renumber.
- **Scope changes get a `♻️` marker** with a dated refocus note. The title stays; the note explains what changed.
- **This file is versioned.** See the Changelog section at the bottom. Update it whenever you make a structural change.

### Weekly review ritual (5 minutes)

Every Sunday:
1. Open this file.
2. Read your tracker rows for the last week.
3. Mark any `Learning` atoms you can honestly promote to `Practiced`, `Built`, or `Mastered`.
4. Check the *Recommended Interleaved Sequence* — are you in the right strand for your current position?
5. Decide what next week's atom will be. Write it down in the tracker.

That's it. Small consistent updates beat infrequent heroic updates.

---

## Changelog

- **v2.0** — Restructured for data-capable AI/ML engineer goal. Added `0.9`, `0.10`, `6.16`, Phase 8B (22 atoms), `17.13`, `18.11`. Refocused 9.4, 9.5. Added Phase 10 cross-references. Added recommended interleave for Phase 8. Added this changelog, USAGE, and Platforms sections.
- **v1.0** — Original 19-phase curriculum with 8 as a single Data Engineering & Analysis phase, 9 as Math for AI, and no data-science additions.

---

*End of curriculum.md*