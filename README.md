## Swayam Bhageria

Software engineer. I build full-stack systems and applied-AI products end to end, take them
to production, and measure whether they actually work.

Based in Delhi, India. **Open to full-stack and applied-AI roles — onsite, remote, or
relocation.**

Credited with **[CVE-2026-92537](https://www.wordfence.com/threat-intel/vulnerabilities/id/ed68a4ff-a2aa-4df7-96b1-f094bce4b9b7)**, a vulnerability in a WordPress plugin running on 200,000+ sites.

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

### Security research

**[CVE-2026-92537](https://www.wordfence.com/threat-intel/vulnerabilities/id/ed68a4ff-a2aa-4df7-96b1-f094bce4b9b7)** — Newsletter plugin for WordPress · 200,000+ active installs · 2026
Unauthenticated exposure of a subscriber's authentication token (CVSS 5.3, CWE-522), verified
and published by Wordfence and fixed in 9.4.0. Found with an AI-assisted audit pipeline:
models read plugin source and flag leads, and a lead is reported only after it reproduces on a
live install, fails on a negative control, and clears a duplicate check against public vulnerability
databases.
`PHP` `WordPress` `security research` `LLM agents`

---

### Selected work

**[autonomous-job-finder](https://github.com/SwayamBhageria/autonomous-job-finder)** — unattended job discovery · 2026
Polls **235 company career boards across 20 ATS platforms** hourly, normalised to one schema,
scores each role with an LLM acting as judge, and alerts only genuine matches. Multithreaded
fetch with per-host rate limiting and per-board fault isolation, two-stage scoring to stay
inside free-tier quota, idempotent state committed back to the repo, and per-board anomaly
detection against a rolling median with an off-host dead-man's switch. No server, no database.
`Python` `Gemini` `GitHub Actions` `Slack API`

**[insurance-voice-ci](https://github.com/SwayamBhageria/insurance-voice-ci)** — a regression gate for AI voice agents on insurance calls · 2026
Plays scripted callers against an agent, rebuilds the audio timeline of each call, and scores
compliance on the words that actually reached the caller rather than what the model wrote.
When a caller interrupts, the transcript still holds the full Medicare disclaimer: for
gemini-3.5-flash-lite, 12 of 12 interrupted callers never heard it finish. Keeping only the
played words in the model's history took that to 0 of 12. 385 calls across 28 scenarios and
4 models, all replayed offline by `make check`.
`Python` `voice agents` `LLM evaluation` `CI`

**[screening-operating-point](https://screening-operating-point.vercel.app)** — where sanctions screening actually loses recall · *live* · [source](https://github.com/SwayamBhageria/screening-operating-point) · 2026
The public benchmarks score the matcher; nothing published scores the step that decides which
names the matcher is shown. Joining 755,540 expert-labelled OpenSanctions pairs to Treasury's
OFAC list gives 7,922 retrieval probes with known answers: standard candidate generation
retrieves 58.6% of true matches, and the loss is not even — 93.6% recall for Latin-script
queries against 2.8% for Cyrillic and 0.0% for Arabic and Chinese. Romanising the query is six
lines of code and takes Cyrillic to 93.8%. Runs offline, no API key, matchers unmodified.
`Python` `record linkage` `JavaScript` `Vercel`

**[Context Budget Lab](https://context-budget-lab.vercel.app)** — what an AI coding agent actually reads · *live* · [source](https://github.com/SwayamBhageria/context-budget-lab) · 2026
Measures the smallest context in which a question about a codebase stays answerable, checked
against the exact lines that answer it, grepped before the selector ever runs. BM25 with
import-graph expansion, scored against best-case grep and a local dense model over five
repositories spanning Python, TypeScript and C/CUDA. Six of nine questions beat grep, three
lose, and the losses are kept in the write-up.
`TypeScript` `Next.js` `BM25` `all-MiniLM-L6-v2`

---

### Also built

- **[silent-wrong-bench](https://github.com/SwayamBhageria/silent-wrong-bench)** — when text-to-SQL is wrong, does anything say so? Across 600 published runs, 74–83% of failures returned a confident wrong number with no error.
- **[frame-budget-bench](https://frame-budget-bench.vercel.app)** — what a cheaper factory-camera pipeline costs: 6 fps holds action recall at 99.98% and takes one accelerator from 6.2 to 28 cameras. *Live console.*
- **[claims-overturn-bench](https://github.com/SwayamBhageria/claims-overturn-bench)** — 1,533 Financial Ombudsman decisions: 88.7% of the upheld ones the tagger places fault how the claim was handled, not whether it was covered.
- **[tool-search-bench](https://github.com/SwayamBhageria/tool-search-bench)** — does an agent's tool search return the right tool? A local embedding index beats a hosted router at five candidates, 0.846 to 0.736; the router wins on a matched candidate budget.
- **[frame-oracle](https://github.com/SwayamBhageria/frame-oracle)** — a frame-exact CI gate for video exports: decodes every output frame back to its source and reports black frames at cuts, late clips, lost frames and audio drift.
- **[clinical-coder](https://github.com/SwayamBhageria/clinical-coder)** — agentic ICD-11 coding from free-text notes, with a verifier stage that can reject or downgrade the proposed codes.

---

### Stack

**Languages** TypeScript · Python · JavaScript · Java · SQL · Bash
**Frontend** Angular 17–21 · RxJS · Signals · Angular Material · video.js · Tailwind
**Backend** FastAPI · Node.js · Express · Spring Boot · REST · WebSockets (STOMP/SockJS) · Kafka · JWT · OAuth 2.0
**Data** PostgreSQL · MongoDB · MySQL · SQLite · FAISS
**AI / ML** LLM application development · retrieval and vector search · evaluation and benchmarking · prompt engineering · TensorFlow · Keras · scikit-learn
**Infra** Docker · Caddy · Nginx · Cloudflare · Vercel · Oracle Cloud · Linux/RHEL · RPM packaging · GitHub Actions

---

B.Tech in Electronics & Communication (AI & ML), **NSUT Delhi**, 2021–2025 · CGPA 8.4\
Thesis: [schizophrenia detection from EEG](https://github.com/SwayamBhageria/Schizophrenia-detection), CNN-LSTM with VAE augmentation, 97.1% accuracy\
[CodeChef](https://www.codechef.com/users/swayam_b) 3★ (1600+) · [500+ LeetCode](https://leetcode.com/u/Swayambhageria/)

**[LinkedIn](https://linkedin.com/in/swayam-bhageria)** · **[bhageriaswayam@gmail.com](mailto:bhageriaswayam@gmail.com)**
