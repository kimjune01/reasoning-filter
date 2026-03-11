```text
NOVEL PASSAGES:
- "If the user taps, the embedding enters a TEE running on AWS Nitro Enclaves. The publisher encrypts the embedding with the enclave's public key, verified through remote attestation. The exchange operator's infrastructure routes the ciphertext but cannot decrypt it. Inside the enclave, the TEE computes distances against all advertiser positions, combines them with each advertiser's dynamic bids, budgets, and pacing rules, runs the full auction with `log(bid) - distance² / σ²`, and returns a winner ID and price. The embedding is destroyed after execution." — This feels novel as a concrete mechanism: confidential-computing-based ad exchange for health-intent matching, with a specific auction form and architectural claim that no human-visible health data is ever acquired.

- "Advertiser embeddings are public. An advertiser's position in embedding space is a claim of expertise: 'sports injury rehab for competitive athletes who need to keep training.'" — This feels novel as a framing. Embeddings are not just model artifacts here; they become public, declarative positioning statements for advertisers.

- "Phase one of the two-phase model runs entirely on the publisher's servers: cosine distance between the conversation embedding and cached advertiser positions, rendered as a proximity indicator. No data moves. No auction runs." — The two-phase gating design feels somewhat novel: local relevance preview first, auction only after explicit user action.

- "The two-phase model satisfies the standard by construction. Phase one shows a proximity indicator... Phase two requires the user to tap... The default state is no ad. The user who never taps never sends any data beyond the publisher's servers. Consent is expressed through action." — This feels novel as a specific consent mechanism tied to system architecture rather than banner text or contractual language.

- "The trust chain makes this gap impossible. Open-weight embedding models with published hashes, so anyone can reproduce the embedding. Published auction source code running inside an attested TEE, so anyone can verify the auction ran honestly. The publisher's matching is reproducible: same model, same advertiser catalog, same distances. The claim and the implementation are the same artifact." — This feels novel as a new connection: combining reproducible ML, public hashes, and enclave attestation into an auditable ad-market compliance framework.

- "Intent casting complies differently. No party acquires readable health information. The architecture proves it." — The core argument that legal compliance can rest on provable unreadability rather than mere policy promises feels like a novel synthesis, even if its components are known.

RECOMBINED PASSAGES:
- "Every FTC health data enforcement action required the same thing: a third party acquired identifiable health information." — Echoes standard legal/technical reasoning built around data transfer, third-party disclosure, and FTC enforcement summaries.

- "GoodRx sent prescription data to Facebook via tracking pixels. Facebook acquired it. BetterHelp sent mental health intake responses to Snapchat and Criteo. Cerebral sent diagnosis information to LinkedIn and TikTok." — Echoes known enforcement-case recaps and privacy-law commentary.

- "Data clean rooms were supposed to solve this... DCRs fail because the data still moves." — Echoes existing critiques of clean rooms in privacy, adtech, and antitrust discourse.

- "A user describing symptoms to a chatbot is further down the funnel than someone typing two words into a search box." — Echoes familiar performance-marketing and funnel-optimization logic.

- "Google serves pharmaceutical ads against 'depression symptoms' and PT ads against 'knee pain running' every day. The FTC has never pursued this, because matching a relevant ad to a voluntarily submitted query is search working correctly." — Echoes common distinctions between first-party search advertising and third-party tracking.

- "Cookie banners fail this. They are designed to be clicked through. Dark patterns make rejection harder than acceptance." — Echoes broad, well-represented critiques from privacy regulation, UX ethics, and consent scholarship.

- "Google retains health-intent search queries indefinitely and matches them against pharmaceutical advertisers; the data doesn't leave the building because Google is the building. Meta proposed using chatbot conversations for ad targeting with no opt-in. Both comply by being the only party in the room." — Echoes common arguments about vertically integrated platforms and first-party data advantage.

RECONSTRUCTABILITY: 78%

NOVELTY CONFIDENCE: 3/5 — Several passages contain an unfamiliar synthesis of FTC health-data doctrine, embeddings, TEEs, and auction design, but much of the surrounding argument is built from familiar privacy-law and adtech material.
```
