## Swayam Bhageria

Software engineer. I build full-stack systems and applied-AI products end to end, take them
to production, and measure whether they actually work.

Based in Delhi, India. **Open to full-stack and applied-AI roles — onsite, remote, or
relocation.**

Day to day I work in a five-engineer team on an enterprise real-time broadcast/OTT
video-monitoring platform, across the stack: Kafka alarm streams fanned out to browsers over
a STOMP-over-SockJS layer with auto-reconnect driving a tiled video wall of live HLS, the
services behind it, and the Linux/RHEL deployment path that ships it.

---

### Live products

**[Facely](https://facely.shop)** — AI face-search for event photography · *live* · [write-up](https://github.com/SwayamBhageria/facely) · 2026
Guests upload one selfie and get back every photo they appear in. A 512-d InsightFace
embedding pipeline with FAISS vector search, on a queued auto-resuming index that survives
restarts mid-run. Indexed 6,830 faces from a 998-photo event on a 2-OCPU ARM VM; search
returns in ~1.9s with zero false positives. Full commercial stack: HMAC-verified payments,
streaming-zip downloads, Docker/Caddy/Cloudflare.
`FastAPI` `InsightFace` `FAISS` `Docker` `Oracle Cloud ARM`

**[ReviewHQ](https://reviewhq.online)** — AI review management for local businesses · *live* · [write-up](https://github.com/SwayamBhageria/reviewhq) · 2026
Monitors Google Business Profile reviews and drafts context-aware replies, with tone control
and Hindi/Hinglish/English detection driving prompt selection, behind a multi-model fallback
chain for provider degradation. OAuth 2.0, scheduled polling with backoff, webhook billing.
`FastAPI` `PostgreSQL` `Gemini` `OAuth 2.0`

**[OrderMender](https://ordermender.com)** — WooCommerce order-editing plugin · *live on [wordpress.org](https://wordpress.org/plugins/ordermender/)* · 2026
Gives a store a short, controlled editing window after checkout: orders pause in a
"Hold for Editing" status while the customer corrects their own address or notes before
fulfilment begins, instead of emailing support. Release runs three independent ways so a held
order can never strand. Published to the WordPress plugin directory after review.
`PHP` `WooCommerce` `WordPress Plugin API`

---

### Live tools

Deployed consoles you can open and drive. Each one measures a production system's real
operating point on public data, then prices the fix.

**[screening-operating-point](https://screening-operating-point.vercel.app)** — where sanctions screening actually loses recall · *live* · [source](https://github.com/SwayamBhageria/screening-operating-point) · 2026
The public benchmarks score the matcher; nothing published scores the step that decides which
names the matcher is shown. Joining 755,540 expert-labelled OpenSanctions pairs to Treasury's
OFAC list gives 7,922 retrieval probes with known answers: standard candidate generation
retrieves 58.6% of true matches, and the loss is not even — 93.6% recall for Latin-script
queries against 2.8% for Cyrillic and 0.0% for Arabic and Chinese. Romanising the query is six
lines of code and takes Cyrillic to 93.8%. Runs offline, no API key, matchers unmodified.
`Python` `record linkage` `JavaScript` `Vercel`

**[frame-budget-bench](https://frame-budget-bench.vercel.app)** — what a cheaper camera pipeline costs the metric it pays for · *live* · [source](https://github.com/SwayamBhageria/frame-budget-bench) · 2026
A camera watching a production line costs money per frame it analyses, so every deployment
analyses fewer. Measured over 38 sessions of 16 operators and 4,803 annotated actions with the
classifier assumed perfect, so no better model can answer it: 6 fps holds action recall at
99.98% and takes one accelerator from 6.2 to 28 cameras, but below 3 fps the loss stops being
even and tracks how fast each operator works (rho −0.92 at 0.33 fps). A time-in-work estimator
removes that bias to +0.03%.
`Python` `JavaScript` `time-series analysis` `Vercel`

**[Context Budget Lab](https://context-budget-lab.vercel.app)** — what an AI coding agent actually reads · *live* · [source](https://github.com/SwayamBhageria/context-budget-lab) · 2026
Measures the smallest context in which a question about a codebase stays answerable, checked
against the exact lines that answer it, grepped before the selector ever runs. BM25 with
import-graph expansion, scored against best-case grep and a local dense model over five
repositories spanning Python, TypeScript and C/CUDA. Six of nine questions beat grep, three
lose, and the losses are kept in the write-up.
`TypeScript` `Next.js` `BM25` `all-MiniLM-L6-v2`

---

### Benchmarks and analysis

**[claims-overturn-bench](https://github.com/SwayamBhageria/claims-overturn-bench)** — do insurance claim declines survive the ombudsman? · 2026
AI claims products are sold on speed and cost, both measured from the inside on the day the
claim closes. The number that arrives later and from outside is the share of declines that
don't hold up. A corpus of 1,533 published Financial Ombudsman decisions across 183 firms,
1,349 of them real claim disputes, with the verdict split from the facts and every input
scanned for leakage at build time and again at load. Of the upheld decisions the tagger
places, 88.7% fault how the claim was handled rather than whether it was covered. Ships a
checker returning nearest precedents with citations.
`Python` `retrieval` `public-record corpus`

**[tool-search-bench](https://github.com/SwayamBhageria/tool-search-bench)** — does an agent's tool search return the right tool? · 2026
91 hand-written cases across 23 toolkits with BM25 and dense-embedding baselines, run against
a live hosted tool router. A local embedding index beats the hosted router at five candidates,
0.846 to 0.736; the router wins on matched candidate budget over the full catalogue. Both
readings published, plus a confidence gate that removes about half the out-of-scope false
confidence at zero cost on the real cases.
`Python` `BM25` `bge-small-en-v1.5` `confidence gating`

**[leaderboard-error-bars](https://github.com/SwayamBhageria/leaderboard-error-bars)** — how much of a benchmark's ranking its own data supports · 2026
A public leaderboard ranks seven voice-agent platforms. Recovering the integer counts behind
its percentages shows ranks 2 and 3 differ by one scenario out of 82, and that no adjacent
pair in the top six separates at 95% even under the pairing most favourable to it. Also finds
a headline column computed over at least four different denominators. Exact McNemar and
Fisher in integer arithmetic, cross-validated against scipy; 90 tests; every published figure
generated by script, and it reproduces offline from a clean clone.
`Python` `exact statistics` `reproducible research`

---

### Systems

**[clinical-coder](https://github.com/SwayamBhageria/clinical-coder)** — agentic ICD-11 coding with a verifier · 2026
Takes a free-text consult note and returns diagnosis codes grounded in retrieved evidence, or
`no confident match`. Normalize → retrieve → propose → verify → finalize, where the verify
stage can reject or downgrade. Every result keeps the proposal alongside the final codes, so a
reviewer can watch the verifier working rather than take it on trust.
`Python` `Gemini` `retrieval grounding` `evaluation harness`

**[autonomous-job-finder](https://github.com/SwayamBhageria/autonomous-job-finder)** — unattended job discovery · 2026
Polls **235 company career boards across 20 ATS platforms** hourly, normalised to one schema,
scores each role with an LLM acting as judge, and alerts only genuine matches. Multithreaded
fetch with per-host rate limiting and per-board fault isolation, two-stage scoring to stay
inside free-tier quota, idempotent state committed back to the repo, and per-board anomaly
detection against a rolling median with an off-host dead-man's switch. No server, no database.
`Python` `Gemini` `GitHub Actions` `Slack API`

**[Schizophrenia detection from EEG](https://github.com/SwayamBhageria/Schizophrenia-detection)** — B.Tech thesis · 2025
CNN-LSTM over EEG spectrograms, with a Variational Autoencoder synthesising training data to
correct class imbalance. 97.1% accuracy, 97.1% F1.
`TensorFlow/Keras` `CNN-LSTM` `VAE` `MNE-Python`

---

### Stack

**Languages** TypeScript · Python · JavaScript · Java · SQL · Bash
**Frontend** Angular 17–21 · RxJS · Signals · Angular Material · video.js · Tailwind
**Backend** FastAPI · Node.js · Express · Spring Boot · REST · WebSockets (STOMP/SockJS) · Kafka · JWT · OAuth 2.0
**Data** PostgreSQL · MongoDB · MySQL · SQLite · FAISS
**AI / ML** LLM application development · retrieval and vector search · evaluation and benchmarking · prompt engineering · TensorFlow · Keras · scikit-learn
**Infra** Docker · Caddy · Nginx · Cloudflare · Vercel · Oracle Cloud · Linux/RHEL · RPM packaging · GitHub Actions

---

B.Tech in Electronics & Communication (AI & ML), **NSUT Delhi**, 2021–2025 · CGPA 8.4
CodeChef 3★ (1600+) · 500+ LeetCode

**[LinkedIn](https://linkedin.com/in/swayam-bhageria)** · **[bhageriaswayam@gmail.com](mailto:bhageriaswayam@gmail.com)**
