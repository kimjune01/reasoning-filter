Health publishers have spent the last few years learning an expensive lesson: high-intent traffic is only valuable if you can monetize it without turning your audience into evidence.

That sounds harsh, but it is the right framing. If someone is reading about depression, fertility, menopause, addiction, diabetes, or cancer, that is not just “premium audience data.” It is a record of vulnerability. Regulators know it. Consumers know it. And increasingly, the market knows it too.

The old playbook for monetizing health content was built for a less scrutinized internet. Drop in a pixel. Build retargeting pools. Match visitors into platform audiences. Push the data into a clean room. Tell everyone it is “privacy-safe” because the spreadsheet has hashes and the contract has legalese. Then act surprised when the FTC shows up and asks a very basic question: why did any of these parties need to know this person was reading about a sensitive health condition in the first place?

That question is the whole ballgame.

The FTC has been unusually clear here. In actions against GoodRx, BetterHelp, and Monument, the agency treated the disclosure of sensitive health information to ad platforms as exactly what it looked like: a harmful transfer of health data for advertising. The lesson is not limited to digital health apps. If you are a publisher attracting audiences around symptoms, diagnoses, treatment options, recovery, or reproductive health, you should assume regulators will look at your data flows with the same skepticism. If your monetization stack depends on multiple companies learning that a person is likely dealing with a specific health issue, your architecture is already on the wrong side of the trend.

And that is why so many “privacy-preserving” approaches failed. They were not really designed to preserve privacy. They were designed to preserve adtech economics while changing the vocabulary.

Tracking pixels failed first, and deservedly so. A pixel is basically an automated confession. The page loads, the browser calls a third party, and now that third party knows a device or user visited a page that can reveal something about health concerns. Sometimes it gets worse: query parameters, form events, conversion events, custom segments, hashed emails, mobile IDs. Companies told themselves the data was pseudonymous, or that the platform would only use it for “measurement,” or that they had consent language buried somewhere in the footer. But from a policy perspective, that is weak tea. If the result is that Meta, Google, or some other ad intermediary can infer a person’s condition, treatment interest, medication category, or care-seeking behavior, you are not winning a semantics contest. You are leaking health information.

Data clean rooms were supposed to be the sophisticated replacement. In practice, they mostly moved the same problem into a nicer room with better slides.

Here is the uncomfortable truth about clean rooms: they are often built to let two or more parties learn just enough about the overlap between audiences to keep targeted advertising alive. Maybe nobody exports raw rows. Maybe matching happens under controlled rules. Maybe the outputs are “aggregate.” Fine. But if a publisher contributes an audience derived from highly sensitive health behavior and a marketer matches against it, the privacy risk does not disappear just because the join happened inside approved software. The issue is not only whether someone downloaded a CSV. The issue is whether the system enabled a party to act on identifiable or linkable health-related signals about people.

That is the mistake the industry keeps making. It treats privacy as a disclosure problem when it is really an acquisition problem.

If the advertiser, platform, or data partner acquires usable knowledge that this browser, this person, or this matched identity is associated with a sensitive health topic, you have already lost the argument. It does not matter that the signal came via pixel, clean room, identity graph, or “secure collaboration environment.” Different plumbing, same leak.

Health publishers need a more radical shift: stop architecting monetization systems around data sharing, and start architecting them around decision execution.

This is where trusted execution environments, or TEEs, get interesting.

A TEE is not a policy. It is not a legal shield. It is not magic fairy dust. It is a technical boundary that lets code run in an isolated environment where data can be processed without being exposed to the host, the publisher, the buyer, or the platform operating the infrastructure. Think of it as a locked room with a provable rule set: approved code goes in, encrypted inputs go in, a constrained output comes out, and nobody gets to watch the raw materials while the work happens.

That matters because an ad auction does not actually require broad distribution of sensitive information. It requires a decision.

Those are not the same thing.

A health publisher has a page view. The old system says: broadcast the context, identifiers, and behavioral clues to multiple external parties so they can each decide how much the impression is worth. A TEE-based system says: keep the sensitive context sealed, let approved logic evaluate bids inside the enclave, and reveal only the minimum necessary output, such as which creative won and what price cleared.

That is a completely different privacy posture.

In a well-designed TEE auction for health media, the publisher does not spray URLs, page titles, cookies, email hashes, or health-interest segments across the ecosystem. Buyers do not ingest raw visit-level data tied to sensitive content. The infrastructure provider cannot casually inspect the inputs. The enclave receives encrypted auction inputs, runs approved code, and returns a decision. Logging is constrained. Outputs are minimized. Reporting is aggregated. Identity never becomes the fuel.

This is the point many adtech people resist, because they are still addicted to audience possession. They want the segment. They want the overlap report. They want the user list. They want to “activate” later. But for sensitive health traffic, that instinct is exactly the compliance problem.

Health monetization has to become more like confidential computing and less like data brokerage.

What would that look like in practice?

A publisher could classify inventory into carefully designed, non-exploitative contextual categories. Not “women trying to get pregnant right now in Seattle,” but something like “women’s health education” or “chronic care information,” depending on what is appropriate and lawful. A buyer could submit bidding logic that says, in effect, “I am willing to pay this amount for this type of context, under these brand safety rules, with no user-level export.” The auction would run inside the TEE. The winner would receive only what is needed to render the ad and measure delivery within strict limits. No party would receive raw evidence that a named or identifiable person visited a page about IVF, addiction recovery, HIV treatment, or antidepressants.

Notice what changed: the system monetizes intent without transferring possession of the underlying sensitive signal.

That is the breakthrough. Not “better consent.” Not “stronger contracts.” Not “cleaner clean rooms.” Structural non-acquisition.

To be clear, TEEs are not automatically compliant. You can still build a bad system inside a fancy box. If the inputs are too granular, the outputs too revealing, or the reports too easy to reverse-engineer, you can recreate the same harms with better cryptography. If the enclave lets buyers target tiny audiences, export user-level results, or combine auction outcomes with outside identifiers, you are back in the swamp. The technical isolation only matters if the product rules are equally strict.

So the standard should be simple: no party should learn more about a person’s health-related behavior than is strictly necessary to serve a lawful, privacy-respecting ad transaction.

That means no user-level audience exports.
No retargeting based on sensitive page visits.
No identity matching against health-derived cohorts.
No event streams that leak condition-specific behavior.
No measurement outputs granular enough to reconstruct who saw what.
And no pretending that “pseudonymous” means harmless when the subject matter is inherently sensitive.

Some publishers will object that this limits yield. Maybe in the short term, yes. But let’s be honest about the alternative. The pixel-era yield was artificially inflated by regulatory arbitrage. It worked because the industry assumed no one would seriously challenge the routine disclosure of health-related browsing behavior to ad platforms. That assumption is gone. The revenue attached to that model was never stable; it was contingent on lax enforcement and public ignorance.

Health publishers should stop mourning the old margin and start building the durable one.

There is real value in high-intent health traffic even without person-level surveillance. Advertisers want adjacency to trusted content. They want moments of relevance. They want environments where users are actively researching decisions. What they do not need, and increasingly should not be allowed to get, is the ability to quietly accumulate identifiable evidence about who those users are and what private issues they may be facing.

That is why I think TEEs are more than a technical upgrade. They are a philosophical correction.

For twenty years, adtech has assumed the way to make better decisions is to distribute more data to more parties. In health, that assumption is not just outdated. It is reckless. The better model is the opposite: distribute less data, constrain who can learn what, and let computation happen where observation cannot.

If you are a health publisher, the question is no longer whether you can afford to abandon pixels and identity-heavy monetization. The question is whether you can afford not to.

Because the market is moving toward systems that can prove restraint, not just promise it. Regulators are looking at actual data flows, not branding language. And audiences are increasingly aware that “personalized advertising” around health topics often means “someone I never heard of learned something intimate about me.”

That is a terrible foundation for a trust-based publishing business.

The next generation of health monetization will belong to publishers that understand a hard but liberating truth: you do not need to expose sensitive health information to sell a valuable impression. You need to create a system where value can be priced without vulnerability being transferred.

Pixels could not do that.
Clean rooms mostly did not do that.
Trusted execution environments can, if they are used with discipline.

That is the path forward: not a cleverer way to share health data, but a serious way to stop sharing it.

Background references: FTC on [GoodRx](https://www.ftc.gov/news-events/news/press-releases/2023/02/ftc-enforcement-action-bar-goodrx-sharing-consumers-sensitive-health-info-advertising), [BetterHelp](https://www.ftc.gov/news-events/news/press-releases/2023/07/ftc-gives-final-approval-order-banning-betterhelp-sharing-sensitive-health-data-advertising), [Monument](https://www.ftc.gov/news-events/news/press-releases/2024/04/alcohol-addiction-treatment-firm-will-be-banned-disclosing-health-data-advertising-settle-ftc), the FTC’s [health information guidance](https://www.ftc.gov/business-guidance/resources/collecting-using-or-sharing-consumer-health-information-look-hipaa-ftc-act-health-breach), the FTC’s [2024 HBNR update](https://www.ftc.gov/news-events/news/press-releases/2024/04/ftc-finalizes-changes-health-breach-notification-rule), and the joint FTC/HHS warning on [online tracking technologies](https://www.ftc.gov/news-events/news/press-releases/2023/07/ftc-hhs-warn-hospital-systems-telehealth-providers-about-privacy-security-risks-online-tracking).