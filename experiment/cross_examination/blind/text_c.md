Health publishers have spent the last few years discovering something they should have understood sooner: high-intent traffic is not an asset if the business model requires turning private struggle into adtech exhaust.

That is the real issue. When someone is reading about depression, infertility, menopause, addiction, diabetes, or cancer, you are not looking at a generic "premium audience." You are looking at a record of vulnerability. Regulators see that more clearly now. Consumers certainly do. The market is starting to.

The old health publishing playbook belonged to a sloppier internet. Drop a pixel. Build a retargeting pool. Sync audiences to platforms. Push data into a clean room. Call the whole thing privacy-safe because the identifiers are hashed and the contracts are ornate. Then act mystified when the FTC asks the only question that matters: why did any of these companies need to know this person was reading about a sensitive health condition at all?

That question ruins most of the industry's defenses.

The FTC has been unusually direct in its actions against GoodRx, BetterHelp, and Monument. In each case, the agency treated the sharing of sensitive health information with advertising platforms as what it plainly was: a harmful disclosure of health data for marketing purposes. The lesson is not confined to digital health apps. Any publisher drawing audiences around symptoms, diagnoses, treatment decisions, recovery, or reproductive health should assume the same logic applies. If your monetization stack works by allowing a cluster of outside companies to infer that someone is likely dealing with a specific condition, the architecture itself is the problem.

Pixels failed first, and for obvious reasons. A tracking pixel is just an automated disclosure mechanism. The page loads, the browser calls a third party, and that third party learns that a device or account visited a page whose subject matter may itself reveal something intimate. In practice it is often worse than that: URL strings, conversion events, custom parameters, form interactions, hashed email addresses, mobile identifiers. The industry spent years hiding behind words like pseudonymous and measurement, as if the label changed the substance. It does not. If the outcome is that Meta, Google, or another intermediary can infer treatment interest, care-seeking behavior, medication category, or a likely condition, then the system is leaking health information. Calling it adtech does not make it less revealing.

Clean rooms were supposed to fix this. Mostly they laundered it.

The problem with most clean-room pitches is that they mistake controlled exposure for non-exposure. Yes, maybe nobody exports raw rows. Yes, maybe the join happens inside approved software. Yes, maybe the outputs are aggregated. But if a publisher contributes an audience built from highly sensitive health behavior and a marketer uses that system to learn overlap, optimize spend, or target against it, the central privacy harm is still there. The question is not whether someone downloaded a CSV. The question is whether the system gave another party usable knowledge that a person, browser, or matched identity is associated with a sensitive health topic.

That is where the industry keeps cheating. It treats privacy as a problem of disclosure format when it is really a problem of signal acquisition.

Once an advertiser, platform, or data partner has acquired actionable knowledge that this user is linked to addiction recovery, fertility treatment, HIV care, antidepressants, or some other sensitive category, the damage is already done. Pixel, clean room, identity graph, secure collaboration environment: different plumbing, same leak.

Health publishers need a more fundamental change. Stop designing monetization around data sharing. Design it around decision execution.

That is why trusted execution environments are actually interesting.

A TEE is not a legal theory and it is not a magic compliance box. It is a technical boundary. Code runs in an isolated environment; encrypted inputs go in; constrained outputs come out; the host, publisher, buyer, and infrastructure operator do not get to casually inspect the raw data while computation happens. That matters because advertising does not inherently require widespread distribution of sensitive information. It requires a decision.

Those are not the same thing.

The conventional system says: a page view appears, so broadcast context, identifiers, and behavioral clues to a crowd of outside parties and let each of them decide what the impression is worth. A TEE-based system says: keep the sensitive context sealed, let approved bidding logic run inside the enclave, and reveal only what is necessary for execution, such as the winning creative and clearing price. That is a radically different privacy posture, not a cosmetic one.

In a disciplined TEE auction for health media, the publisher does not spray page URLs, titles, cookies, email hashes, or condition-coded audience segments across the ecosystem. Buyers do not ingest visit-level evidence tied to sensitive pages. The infrastructure provider cannot simply peer into the inputs because it operates the box. The enclave processes encrypted auction inputs, returns a result, and exposes as little else as possible. Logging is restricted. Reporting is aggregated. Identity is not the fuel.

This is exactly the part many adtech companies dislike, because they are still attached to possession. They want the segment, the overlap report, the exportable audience, the option to activate later. For sensitive health traffic, that instinct is not just outdated. It is the compliance risk in its purest form.

What makes TEEs promising is not that they somehow bless health advertising. It is that they make a different architecture possible: one where value can be computed without transferring custody of the underlying sensitive signal.

That distinction matters more than most privacy rhetoric does.

A publisher can still classify inventory into carefully bounded contextual categories. A buyer can still express bidding preferences around those categories, brand safety rules, and pricing thresholds. But the critical move is that the sensitive context does not become a reusable asset circulating among platforms, data brokers, and measurement vendors. The auction can happen without producing a trail of evidence that a specific person was reading about IVF, relapse, menopause treatment, or oncology options.

That is the breakthrough, if the system is built with some discipline. Not better consent banners. Not tighter contractual language. Not a more elegant clean room. Structural non-acquisition.

Of course TEEs can be abused too. A badly designed enclave can recreate the same harms with more impressive jargon. If the inputs are too granular, the outputs too revealing, or the reporting too easy to reverse-engineer, then the box is just a more expensive way to keep doing the wrong thing. If buyers can target tiny cohorts, export user-level outcomes, or combine results with outside identifiers, you are back in the swamp immediately. Confidential computing does not redeem an undisciplined product.

The standard should be harsher than the industry prefers: no party should learn more about a person's health-related behavior than is strictly necessary to complete a lawful ad transaction.

That rules out user-level audience exports, retargeting based on sensitive page visits, identity matching against health-derived cohorts, event streams that expose condition-specific behavior, and measurement granular enough to reconstruct who saw what. It also means dropping the absurd pretense that pseudonymous equals harmless when the subject matter itself is deeply sensitive.

Some publishers will say this constrains yield. It probably does, at least against the inflated economics of the old model. But that old yield was propped up by regulatory arbitrage. It depended on the assumption that nobody would seriously challenge the routine disclosure of health-related browsing behavior to advertising platforms. That assumption is finished. Revenue built on lax enforcement and public ignorance was never durable revenue.

Publishers should stop grieving that margin.

There is still plenty of value in health traffic without person-level surveillance. Advertisers want trusted environments. They want relevance. They want to appear next to content people are actively using to make consequential decisions. What they increasingly do not need, and should not get, is quiet access to identifiable evidence about who those people are and what private problems they may be trying to solve.

That is why TEEs matter as more than infrastructure. They force a philosophical correction.

For two decades, adtech has operated on a simple reflex: better decisions require wider distribution of data. In health, that reflex looks less like innovation than carelessness. The better model is the reverse one: distribute less, constrain knowledge, and let computation happen where observation does not.

If you run a health publisher, the practical question is no longer whether you can afford to move away from pixels and identity-heavy monetization. It is whether you can afford to keep pretending those systems are defensible.

The next phase of health monetization will favor publishers that can prove restraint rather than merely promise it. Regulators are looking at actual data flows now, not just branding language. Users are increasingly aware that "personalized advertising" around health topics often means a chain of companies they have never heard of learned something intimate about them.

That is not a stable basis for a trust-based publishing business.

The future here is not a cleverer method for sharing health data. It is a serious method for not sharing it. Pixels could not do that. Clean rooms mostly did not. Trusted execution environments can, if the rules around them are strict enough to matter.

Background references: FTC on [GoodRx](https://www.ftc.gov/news-events/news/press-releases/2023/02/ftc-enforcement-action-bar-goodrx-sharing-consumers-sensitive-health-info-advertising), [BetterHelp](https://www.ftc.gov/news-events/news/press-releases/2023/07/ftc-gives-final-approval-order-banning-betterhelp-sharing-sensitive-health-data-advertising), [Monument](https://www.ftc.gov/news-events/news/press-releases/2024/04/alcohol-addiction-treatment-firm-will-be-banned-disclosing-health-data-advertising-settle-ftc), the FTC's [health information guidance](https://www.ftc.gov/business-guidance/resources/collecting-using-or-sharing-consumer-health-information-look-hipaa-ftc-act-health-breach), the FTC's [2024 HBNR update](https://www.ftc.gov/news-events/news/press-releases/2024/04/ftc-finalizes-changes-health-breach-notification-rule), and the joint FTC/HHS warning on [online tracking technologies](https://www.ftc.gov/news-events/news/press-releases/2023/07/ftc-hhs-warn-hospital-systems-telehealth-providers-about-privacy-security-risks-online-tracking).
