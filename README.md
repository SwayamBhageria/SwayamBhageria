## Swayam Bhageria

Software engineer in Delhi, India. I build and ship full-stack and applied-AI products
end to end — usually solo, usually all the way to production and paying users.

Currently a software engineer at **Interra Systems**, working on a real-time
broadcast/OTT video-monitoring platform: Kafka event streams fanned out over WebSockets
to a live tiled video wall, in Angular and TypeScript.

---

### Things I've shipped

**[Facely](https://facely.shop)** — AI face-search for event photography · *live*
Guests upload one selfie and get back every photo they appear in. InsightFace embedding
pipeline with FAISS vector search, on a queued auto-resuming index that survives
restarts. Indexed 6,830 faces from a 998-photo event; searches return in ~1.9s at 0.972
confidence with zero false positives.
`FastAPI` `InsightFace` `FAISS` `Docker` `Caddy` `Oracle Cloud ARM`

**[ReviewHQ](https://reviewhq.online)** — AI review management for local businesses · *live*
Monitors Google Business Profile reviews and drafts context-aware replies with tone and
Hindi/Hinglish/English detection, behind a multi-model fallback chain for provider
degradation.
`FastAPI` `PostgreSQL` `Gemini` `OAuth 2.0` `Razorpay` `Twilio`

**[autonomous-job-finder](https://github.com/SwayamBhageria/autonomous-job-finder)** — unattended job discovery · *source available*
Polls 130 company career boards every 30 minutes across 14 different ATS adapters,
scores each role with an LLM acting as judge, and alerts only genuine matches. Parallel
fetch with per-board fault isolation, two-stage scoring to stay inside free-tier quota,
and idempotent state committed back to the repo. No server, no database.
`Python` `Gemini` `GitHub Actions` `Concurrent Futures`

**[Schizophrenia detection from EEG](https://github.com/SwayamBhageria/Schizophrenia-detection)** — B.Tech thesis
CNN-LSTM hybrid over EEG spectrograms, with a Variational Autoencoder synthesising
training data to correct class imbalance. 97.1% accuracy, 97.1% F1.
`TensorFlow/Keras` `CNN-LSTM` `VAE` `MNE-Python` `OpenCV`

---

### Stack

**Languages** TypeScript · Python · JavaScript · Java · SQL · Bash
**Frontend** Angular · RxJS · Signals · Angular Material · Tailwind
**Backend** FastAPI · Node.js · Express · Spring Boot · REST · WebSockets · Kafka
**Data** PostgreSQL · MongoDB · MySQL · FAISS
**ML / AI** TensorFlow · Keras · scikit-learn · LLM application development · vector search
**Infra** Docker · Nginx · Caddy · Cloudflare · Linux · GitHub Actions

---

B.Tech in Electronics & Communication (AI & ML), NSUT Delhi · CodeChef 3★ · 500+ LeetCode

[LinkedIn](https://linkedin.com/in/swayam-bhageria) · [Email](mailto:bhageriaswayam@gmail.com)
