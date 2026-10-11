# Mobile-first AI product & startup landscape (state as of 11 Oct 2026)

Scope note: facts are dated inline. "Confirmed" = multiple independent outlets or primary/company source; "Reported" = single secondary source; "Rumor/unverified" flagged explicitly. Numbers from Sensor Tower / Appfigures / RevenueCat / Sacra are estimates unless stated as company-reported.

## KQ1. Hardware agents (Rabbit R1, Humane AI Pin, Meta Ray-Ban, OpenAI/Ive io, Limitless/Rewind, Plaud, Friend, Bee): what users wanted, what failed

### Takeaway
Every standalone "phone-replacement" AI gadget failed or was acqui-hired (Humane -> HP $116M; Limitless -> Meta; Bee -> Amazon; Rabbit in cash-conservation mode with unpaid staff); the only hardware that is actually selling is either a *peripheral to the phone* that does one job well (Plaud recorders: ~2M units, ~$100M software ARR; Meta glasses, ~69% share of a fast-growing but still small category) or a cheap passive recorder. Users rewarded reliability, a narrow job (capture/transcribe/remember), and phone-companion design; they punished latency, cloud dependence, always-on privacy exposure, and overpromised "agents".

### Cited Findings

**Humane AI Pin (shut down Feb 2025) - confirmed**
- HP paid $116M for Humane's IP (300+ patents), technology and most staff, not the hardware business; the Pin's cloud services were cut off ~10 days after the announcement, bricking calling, messaging and AI queries. Humane had sought a $750M-$1B sale in May 2024 - [The Decoder](https://the-decoder.com/humane-ends-its-ai-pin-in-ten-days-sells-technology-to-hp-for-116-million/); [Fortune, 19 Feb 2025](https://www.fortune.com/2025/02/19/hp-humane-deal-ai-pin-shutting-down)
- Returns reportedly exceeded sales by mid-2024; refunds were restricted to devices shipped on/after 15 Nov 2024; charging case had a fire-hazard warning - [TechCrunch, 22 Feb 2025](https://techcrunch.com/2025/02/22/the-fallout-of-hps-humane-acquisition/); [Business Insider NL](https://businessinsider.nl/humane-is-shutting-down-service-for-a-beleaguered-ai-pin-after-sale-to-hp-some-buyers-wont-get-a-refund)
- Lesson framing in coverage: overpromised as smartphone replacement; total cloud dependence meant shutdown = brick - [ComplexDiscovery](https://complexdiscovery.com/the-end-of-humane-ai-pin-hps-strategic-shift-toward-ai-integration/)

**Rabbit R1 - confirmed facts + reported trouble**
- Sold first 10,000-unit run in a day (Jan 2024); runs rabbitOS on AOSP - [Wikipedia](https://en.wikipedia.org/wiki/Rabbit_r1). A profile claims ~130,000 cumulative units; could not verify - [Yespress](https://yespress.io/rabbit-inc)
- Only ~5,000 of units sold were used daily as of Sept 2024 (Fast Company interview via 9to5Google) - [9to5Google](https://9to5google.com/2024/09/26/rabbit-5000-people-use-the-r1-daily/)
- Teardowns showed functions replicable by a free Android app and the promised "Large Action Model" not running on-device; demos shipped without key features; complex tasks took minutes vs seconds on a phone - [bad.technology](https://bad.technology/articles/rabbit-r1-ai-device-launches-as-a-slow-android-app-with-no-on-device-ai.html); [Cubix post-mortem](https://www.cubix.co/blog/the-rabbit-r1-failure/); hardcoded API key vulnerability - [enkambale](https://blog.enkambale.com/rabbit-r1-security-nightmare-ai-assistant-gone-wrong)
- "rabbit intern" (agent that builds apps/web tasks from a prompt) launched 3 Apr 2025 - [This Week in Startups ep. 2106](https://thisweekinstartups.com/2106); [rabbit newsroom](https://www.rabbit.tech/newsroom). rabbitOS 2 (Sept 2025) was a UI redesign; hardware unchanged - [SmartWorld.it](https://www.smartworld.it/news/rabbit-r1-rabbitos-2-aggiornamento-novita.html)
- Late 2025: Tom's Guide confirmed some employees on strike since Oct 2025 over unpaid wages; delayed pay to contractors/employees since start of 2025; Lyu blamed a blocked India launch and moved to "cash conservative mode"; company said a binding term sheet was signed, investor unnamed; next-gen hardware "three-in-one", not glasses or pendant, promised for 2026 - [Tom's Guide](https://www.tomsguide.com/ai/whats-next-for-rabbit-employees-say-they-havent-been-paid-for-months-while-company-teases-new-ai-hardware); [TechSpot](https://www.techspot.com/news/110256-rabbit-employees-they-havent-paid-months-but-r1.html); [DevX](https://www.devx.com/daily-news/rabbit-faces-funding-crunch-amid-unpaid-wages/); [Punto Informatico](https://www.punto-informatico.it/rabbit-r1-gadget-piu-deriso-2024-rivincita/)
- No confirmation found that the round closed or that a 2026 device shipped (gap).

**Limitless (ex-Rewind) -> Meta, Dec 2025 - confirmed**
- Meta acquired Limitless (~8 Dec 2025), terms undisclosed; team folded into Reality Labs wearables; pendant sales to new customers stopped; existing users supported >=1 year and moved to Unlimited plan free; non-pendant products (Rewind) sunset; analysts called it an acqui-hire for tech/talent - [BetaNews](https://betanews.com/2025/12/08/meta-has-acquired-limitless-a-startup-that-produces-ai-powered-wearables/); [eMarketer](https://www.emarketer.com/content/meta-acquires-ai-wearables-startup-limitless-fuel-device-ambitions); [AI Business](https://aibusiness.com/speech-recognition/meta-acquires-limitless)
- Prior funding ~$27.9M ($10M seed Nov 2022, $17.9M Series A May 2023) - [Clay](https://www.clay.com/dossier/limitless-funding) (aggregator; may be incomplete)
- Some UK/South Korea users reported devices stopped working post-deal - [eMarketer](https://www.emarketer.com/content/meta-acquires-ai-wearables-startup-limitless-fuel-device-ambitions)

**Bee -> Amazon (Jul 2025), still shipping - confirmed**
- Amazon bought Bee in July 2025; $49.99 wrist/clip device, optional ~$12/mo sub; shown at CES 2026; audio discarded after transcription; sports band fell off twice in a CES demo - [TechCrunch, 12 Jan 2026](https://techcrunch.com/2026/01/12/why-amazon-bought-bee-an-ai-wearable/); [Tom's Guide](https://www.tomsguide.com/ai/amazon-buys-wearable-ai-startup-bee-a-wrist-device-that-hears-and-transcribes-every-word-you-speak); [Storyboard18 CES 2026](https://www.storyboard18.com/digital/amazon-unveils-bee-a-wearable-ai-companion-at-ces-2026-87525.htm)
- TechCrunch hands-on (24 May 2026): summaries "relatively good", transcripts messy, speaker names manual, needs broad permissions (location, photos, contacts, calendar, notifications), cloud storage; author says fits professionals better than the marketed personal use; Alexa integration had not shipped; users want on-device processing (Bee demoed fully local to a YouTuber, no ship date) - [TechCrunch](https://techcrunch.com/2026/05/24/i-tried-amazons-bee-wearable-and-am-both-intrigued-and-slightly-creeped-out/)
- Tom's Guide reviewer called Bee "the most successful AI wearable" tried vs Humane, Rabbit, Friend - [Tom's Guide](https://www.tomsguide.com/ai/amazon-buys-wearable-ai-startup-bee-a-wrist-device-that-hears-and-transcribes-every-word-you-speak)

**Friend pendant - confirmed modest sales**
- By fall 2025: ~3,000 units sold, ~1,000 shipped, ~$348K revenue vs a far larger marketing budget; 2025 NYC subway campaign known more for backlash than sales. July 2026 "friend 2.0" relaunch: speaker + spoken personality, price up to $249, optional $10/mo for memory beyond 30 days - [The Gadgeteer, 31 Jul 2026](https://the-gadgeteer.com/2026/07/31/friend-ai-pendant-voice-wearable-249-price/)
- Launch price variously $99 / $129 / US$130 across sources - [Tom's Guide](https://tomsguide.com/ai/friend-is-a-dollar99-ai-necklace-that-wants-to-help-you-remake-the-movie-her); [Museum of Failure](https://museumoffailure.com/exhibition/friend-ai)

**Plaud - the hardware winner (company-reported + Sacra estimate)**
- >2M devices shipped cumulative; ~US$100M software ARR (CEO at SuperAI, June 2026); ~50% of device buyers upgrade to paid pro/unlimited - [AI Weekly](https://aiweekly.co/alerts/plaud-hits-100m-arr-on-2m-ai-notetaker-devices); [Plaud CES 2026 blog](https://jp.plaud.ai/blogs/news/ces-2026)
- Sacra estimate: ~$250M annualized revenue Sept 2025, +83% YoY, ~50/50 hardware (~25% gross margin) vs subscriptions - [Sacra](https://sacra.com/research/plaud-revenue-growth-valuation/) (paywalled; figures via search snippet, not audited)

**Meta Ray-Ban / Ray-Ban Display - confirmed early data**
- IDC via Reuters: 15,000 Ray-Ban Display units in first quarter of sales, 6% category share; Meta delayed global rollout citing strong US demand/supply squeeze (Jan 2026) - [Tuoi Tre/Reuters](https://news.tuoitre.vn/print/meta-delays-global-rollout-of-ray-ban-display-glasses-on-strong-us-demand-supply-squeeze-103260107103448135.htm)
- TrendForce (30 Jan 2026): Meta raised Display component orders 87.5% to 150,000; forecast 950K global AR-glasses shipments in 2026 (+53%) - [TrendForce](https://trendforce.com/presscenter/news/20260130-12908.html)
- EssilorLuxottica H1 2026: Meta AI-glasses revenue nearly doubled YoY; IDC puts Meta share at ~69%; Circana: smart-glasses category +233% to ~$436M in 12 months to May 2026 - [basic-tutorials](https://basic-tutorials.com/news/smart-glasses-are-booming-sales-of-meta-glasses-have-nearly-doubled/)

**OpenAI x Jony Ive "io" - confirmed deal, reported delay**
- $6.5B all-stock acquisition of io finalized July 2025; device described as pocket/desk "third core device", not wearable/in-ear - [Forbes AU](https://forbes.com.au/news/innovation/everything-we-know-about-openais-6-5-billion-purchase-of-jony-ives-io); [MacTrast](https://www.mactrast.com/2025/07/openais-acquisition-of-jony-ives-io-ai-hardware-company-is-final/)
- FT (Oct 2025, via secondaries): unresolved issues on assistant "personality", always-listening privacy, and compute capacity - [ChannelNews](https://www.channelnews.com.au/openai-and-jony-ives-secret-ai-device-hits-technical-delays/); [Notebookcheck](https://www.notebookcheck.net/OpenAI-s-first-device-with-designer-Jony-Ive-reportedly-faces-delays-over-technical-issues.1132703.0.html)
- Reported (single chain, PYMNTS citing 9to5Mac): consumer availability pushed to 2027 - [PYMNTS](https://www.pymnts.com/artificial-intelligence-2/2026/openai-delays-first-consumer-device-to-2027/). No official OpenAI confirmation found; no shipping device as of Oct 2026.

### Inferences
- The "passive capture + phone app" pattern (Plaud, Bee, Limitless pre-acquisition) is the only hardware category with proven willingness to pay; conversational "do anything" pucks (R1, Pin, Friend) are the pattern to avoid.
- Big Tech is buying the capture category (Meta/Limitless, Amazon/Bee, HP/Humane IP), which shrinks independent hardware white space but validates software-side "memory/transcript -> action" products that ride on the phone instead of new hardware.
- Cloud-dependent devices with no offline fallback create user-trust debt; an indie dev should keep anything they build useful even if the AI backend is down (local cache, export).

### Gaps
- No verified cumulative Rabbit unit figure after launch, no confirmation the late-2025 funding closed, and no evidence a 2026 Rabbit device shipped.
- No Display-specific full-year 2026 sales; only launch-quarter IDC data and component forecasts.
- Plaud figures are company statements/third-party estimates; no audited numbers.
- No primary OpenAI statement on io timing.

## KQ2. Mobile agent apps and "AI phone" plays: adoption and reviews

### Takeaway
The OS owners are winning the on-phone agent layer (Google's Gemini Intelligence announced 12 May 2026; Apple's iOS 27 App Intents 2.0 makes apps callable by Siri/agents). Third-party "AI phone" plays (Deutsche Telekom/Perplexity T Phone 3 at €149, Brain.ai Natural phone via SoftBank Japan, Honor YOYO, Nothing Essential Space) have shipped but none has published adoption numbers; Perplexity's distribution strategy is carriers + Samsung Bixby rather than a standalone agent app. OpenAI folded Operator into ChatGPT agent (Jul 2025) and has no Android-system-level agent.

### Cited Findings

**Google Gemini Intelligence (Android) - confirmed announcement**
- Announced 12 May 2026 at The Android Show: I/O Edition; computer-use-style agent that works across apps (e.g., pull reading list from Gmail and fill a cart; auto-browse to book appointments); purchases require user confirmation; won't start tasks unprompted; launches first on Samsung Galaxy and Pixel "this summer", broader Android later in 2026; also Gemini in Chrome for Android, Gboard "Rambler" dictation, "Create My Widget" - [Engadget](https://engadget.com/2170770/gemini-intelligence-brings-app-automation-to-android); [Gulf News](https://gulfnews.com/amp/story/technology%2Fwhat-is-googles-gemini-intelligence-how-ai-agents-will-reshape-control-of-your-android-phone-1.500539178); [YourStory](https://yourstory.com/ai-story/google-agentic-ai-android-vibe-coded-widgets)
- Earlier (Feb 2026) agentic Gemini features on Android were beta, limited to some models and initially US/South Korea - [Siecle Digital](https://siecledigital.fr/2026/02/26/gemini-passe-a-laction-sur-android/)

**OpenAI ChatGPT agent / Operator - confirmed**
- Operator launched Jan 2025 (US Pro research preview); core browser-control merged into "ChatGPT agent" 17 Jul 2025; standalone operator.chatgpt.com deprecated (sources cite 31 Aug 2025) - [OpenAI help](https://help.openai.com/en/articles/11794368); [presenc.ai tracker](https://presenc.ai/research/openai-operator-update-tracker-2026)
- Reviews note ChatGPT's Android app cannot control system settings, unlike Gemini; its mobile strength is voice - [Arahi](https://www.arahi.ai/blog/best-ai-assistant-for-android). No source found on agent-mode usage on mobile specifically (gap).

**Perplexity: Comet mobile + Assistant + distribution deals**
- Comet on Android went live Nov 2025 (initially invite-only, Pro/Max first) with voice mode, cross-tab summaries, ad blocker; Perplexity has released no Comet usage figures; Android prioritized for carrier/OEM interest - [etcentric](https://www.etcentric.org/?p=197482); [AlternativeTo](https://alternativeto.net/news/2025/11/perplexity-brings-its-agentic-web-browser-comet-to-android-with-voice-and-other-ai-features); [afaqs](https://www.afaqs.com/news/media/perplexity-brings-its-ai-powered-comet-browser-to-android-phones-10803217)
- Comet went free worldwide 23 Mar 2026 and is the only AI-first browser with iOS+Android apps - [Composite](https://composite.com/blog/best-new-ai-browsers)
- Android Authority hands-on (desktop, Jul 2025): assistant promising but slow - [Android Authority](https://www.androidauthority.com/perplexity-comet-hands-on-3577968)
- Samsung: Bloomberg (Jun 2025) reported talks to preload Perplexity, embed in Samsung Internet, and power Bixby, plus a Samsung investment; leaks say Bixby keeps simple on-device tasks, Perplexity handles complex/web queries on Galaxy S26 - [TechRadar](https://www.techradar.com/phones/samsung-galaxy-phones/the-samsung-galaxy-s26-series-could-have-perplexity-ai-baked-in); [Android Authority](https://www.androidauthority.com/galaxy-s26-gemini-bixby-3618888/); [BGR](https://bgr.com/2035807/bixby-perplexity-ai-integration-galaxy-s26/). Unverified: aggregator claim that Perplexity expects Bixby integration on 800M devices in 2026 - [createwith](https://www.createwith.com/tool/perplexity/updates/perplexity-to-launch-as-system-level-ai-on-samsung-galaxy-s26)

**Deutsche Telekom "AI-Phone" - confirmed launch, no sales data**
- T Phone 3 (€149) / T Tablet 2 (€199), launched Aug 2025 across DE, AT, HR, CZ, GR, HU, ME, MK, PL, SK; Perplexity Assistant via magenta key / double-tap power; 18-month Perplexity Pro included; €1 with tariff; T Phone 3 Pro €229 on sale 14 Oct (year unstated in source) - [Telekom press release](https://www.telekom.com/en/media/media-information/archive/our-ai-phone-brings-ai-for-everyone-1095198); [Mobile World Live](https://www.mobileworldlive.com/deutsche-telekom/deutsche-telekom-debuts-low-cost-ai-phone/); [CSI Magazine](https://www.csimagazine.com/csi/Deutsche-Telekom-launches-AI-phone-and-tablet-across-Europe.php)
- The 2024 MWC concept had involved Brain.ai + Qualcomm for an "app-less" phone; shipped product is Perplexity-based - [Generation-NT](https://www.generation-nt.com/actualites/ai-phone-smartphone-ia-perplexity-deutsche-telekom-2055837)

**Brain.ai / Natural - company press release only**
- Natural AI Phone launched in Japan 24 Apr 2026 via SoftBank retail; "Natural OS" replaces app grid; global expansion planned later 2026 - [StreetInsider PR](https://www.streetinsider.com/Press+Releases/Brain+Technologies+and+SoftBank+Launch+Natural+AI+Phone+in+Japan/26328294.html). Funding: $50M+ (2021, Emerson Collective, Goodwater) and $30M convertible (Feb 2024) - [TechCrunch 2021](https://techcrunch.com/2021/07/28/brain-technologies-raises-50m-for-the-launch-of-natural-a-natural-language-search-engine-and-super-app); [Wikipedia: Jerry Yue](https://en.wikipedia.org/wiki/Jerry_Yue). No independent review or sales data found.

**Honor YOYO agent**
- MWC 2025 demo: on-device agent reads app UI and completes OpenTable booking from one instruction; reviewers found it useful - [GadgetReview](https://www.gadgetreview.com/honor-unveils-revolutionary-ai-agent); [Xataka Android](https://www.xatakandroid.com/aplicaciones-android/tener-ia-movil-esta-bien-agente-mucho-mejor-magic-ai-honor-me-ha-parecido-util-como-impresionante/amp). 2026: YOYO integrated with JD.com's agent to push purchase cards in chat - [ifanr](https://www.ifanr.com/1675372)

**Nothing Essential Space**
- Centralized AI repository for screenshots/voice notes ("Flip to Record" on Phone 3); reviewers: bare-bones but promising; app code suggested a paid tier up to ~$120/yr after trial, Nothing says no pricing decision - [Tom's Guide](https://www.tomsguide.com/phones/android-phones/forget-apple-intelligence-nothing-phones-killer-ai-feature-just-got-better); [CO/AI](https://getcoai.com/news/nothings-ai-assistant-essential-space-could-cost-120-per-year-after-free-trial)

**Apple (iOS 27, WWDC 8 Jun 2026) - mostly secondary**
- App Intents became the single path for Siri/agents into third-party apps; SiriKit deprecated; App Intents 2.0 adds streaming, multi-turn, on-screen awareness; Siri composes multi-step cross-app actions; Foundation Models framework adds model abstraction (swap on-device/Gemini/Claude) - [codemeetai](https://codemeetai.substack.com/p/apples-worldwide-developers-conference); [Superwall](https://superwall.com/blog/3-things-for-developers-from-wwdc-2026); Apple session listing confirms App Intents/Foundation Models/Core AI/MLX were covered - [Apple WWDC26](https://developer.apple.com/videos/play/wwdc2026/8011/)
- Unverified: Taiwanese report that iOS 27 opens Siri to Gemini/Claude/ChatGPT via "Siri Extensions API" - [Inside.com.tw](https://www.inside.com.tw/article/41496-wwdc-26-developers)

### Inferences
- "Agent that drives other apps' UIs" is now an OS feature on both platforms; a third-party app competing head-on will be out-distributed. Indies should instead *publish* intents/actions that platform agents can call, or own a vertical data layer the OS agent can't.
- Perplexity's bet (carrier/OEM bundles, cheap handsets) suggests distribution, not features, is the moat for horizontal mobile assistants.

### Gaps
- No adoption numbers for DT AI-Phone, Brain.ai Natural phone, Honor YOYO, Nothing Essential Space, Comet mobile, or Perplexity Assistant.
- No data on ChatGPT agent usage on mobile or which plans have it on mobile.
- Samsung/Perplexity final terms not confirmed by an official release in sources found.

## KQ3. Breakout mobile AI app categories by revenue/downloads (2025-2026)

### Takeaway
Mobile AI spend is large and extremely concentrated: ChatGPT alone passed $3B lifetime mobile consumer spend (~$2.48B in 2025, ~44% of top-AI-app spend), while ChatGPT+DeepSeek+Gemini hold ~90% of assistant time spent. Outside assistants, the categories with real mobile revenue are photo/video editing (CapCut 736M MAU; 61% of RevenueCat photo/video apps now "AI"), companions (~$120M-$221M/yr category), dictation/notes (Wispr $2B valuation, Granola $1.5B, Plaud $100M ARR), and education (Gauth, Photomath, Brainly on the a16z mobile top 50). AI apps monetize early but churn ~30% faster than non-AI apps.

### Cited Findings

**Market size (Sensor Tower, 16 Jun 2026)**
- Time in GenAI apps: 17.2B hours H1 2025 -> ~36B hours H1 2026; AI-app IAP revenue > $4B in H1 2026 (+36% half-over-half); 200K+ apps mention AI; ~10B downloads H1 2026 (+25% YoY); ChatGPT hit 1B MAU in May 2026 (fastest ever); ChatGPT's share of AI "true audience" fell below 50% in Mar 2026; ChatGPT+DeepSeek+Gemini ~90% of assistant time Q1 2026; Claude US mobile ARPU <$0.50 (Sep 2025) -> $2.76 (May 2026) - [Sensor Tower press release](https://sensortower.com/press/sensor-tower-state-of-ai-2026-report-global-time-spent-on-generative-ai-apps-projected-to-more-than-double-year-over-year)
- Sensor Tower's Mar 2026 full-year forecast: >$10B IAP, 7.2B downloads, 43B hours for GenAI apps in 2026 (different framing) - [deeplearning.ai summary](https://www.deeplearning.ai/the-batch/state-of-mobile-2026-report-shows-ai-chatbot-search-and-assistant-growth-outpaces-gaming-social-and-more)

**ChatGPT mobile revenue (Appfigures)**
- Crossed $3B lifetime mobile consumer spend (Dec 2025); 2025 alone ~$2.48B, +408% from $487M in 2024 - [Appfigures](https://app.appfigures.com/resources/insights/chatgpt-hits-3b-consumer-spend)
- Aug 2025: $2B lifetime, $1.35B YTD, ~53x nearest rival Grok ($25.6M YTD); 44% share of top-AI-app spend; $2.91 lifetime spend/download vs Claude $2.55, Grok $0.75, Copilot $0.28; US ~38% of revenue - [TechCrunch](https://techcrunch.com/2025/08/15/chatgpts-mobile-app-has-generated-2b-to-date-earns-2-91-per-install); [9to5Mac](https://9to5mac.com/2025/08/15/appfigures-chatgpt-app-sees-a-673-increase-in-global-revenue-in-2025/)
- Apr 2026: ChatGPT, Gemini, Claude all in global top-10 most-downloaded apps; Apptopia: US GenAI chatbot DAU -1.5% Apr vs Mar - [Digital Information World](https://www.digitalinformationworld.com/2026/05/ai-apps-reach-three-spots-in-global-top.html)

**a16z Top 100 Gen AI Consumer Apps, 6th ed. (9 Mar 2026; mobile = Sensor Tower MAU Jan 2026)**
- Mobile top 50 (alphabetical on page): AI Gallery, AI Mirror, B612, Baidu AI Search, BeautyCam, BeautyPlus, Brainly, Canva, CapCut, Character.ai, ChatGPT, CiCi, Copilot, DeepSeek, Doubao, Edits, FaceApp, Facemoji, Gauth, Gemini, Grok, Hi Translate, Hypic, Learna AI, Lightroom, Meitu, Meituan, Meta AI, Microsoft Edge, Bing, Mivi, Notion, Nova, Papago, Perplexity, Photomath, Photoroom, Picsart, Pixverse, Polish, Polybuzz, QQ Browser, Remini, Seekee, Snow, VivaCut, VN, Wink, Yandex, YouCut - [a16z](https://a16z.com/100-gen-ai-apps-6/)
- ChatGPT ~900M WAU; 2.5x Gemini on mobile MAU; 2.2x Gemini in mobile sessions/user/month; US paid subs ChatGPT ~8x Claude, ~4x Gemini; Claude paid subs +200% YoY, Gemini +258% (Yipit); CapCut 736M mobile MAU; Sora >3M mobile DAU after a 20-day #1 run; Midjourney fell to #46; Yandex Browser/Alice 71M MAU; Notion AI attach rate 20% -> 50%+ in a year; Genspark $300M Series B + $100M run rate; Manus acquired by Meta Dec 2025 (~$2B est.); "consumers mostly interact with agents by text rather than through dedicated apps" (Poke via SMS; OpenClaw via WhatsApp/Telegram/Signal) - [a16z](https://a16z.com/100-gen-ai-apps-6/)
- Note-takers: Fireflies, Fathom, Otter, TL;DV, Granola combined ~20M web visitors; Wispr cited for dictation - [a16z](https://a16z.com/100-gen-ai-apps-6/)

**Retention/monetization (RevenueCat State of Subscription Apps, Mar 2026)**
- AI apps = 27.1% of apps on RevenueCat; Photo & Video 61.4% AI share, Business 19.1%, Travel 12.3%, Gaming 6.2%
- Annual churn 30% faster; annual retention 21.1% (AI) vs 30.7%; monthly retention 6.1% vs 9.5%; refund rate 4.2% vs 3.5%
- But: trial-to-paid 8.5% vs 5.6%; download->paid 2.4% vs 2.0%; realized LTV monthly $18.92 vs $13.59, annual $30.16 vs $21.37 - [TechCrunch, 10 Mar 2026](https://techcrunch.com/2026/03/10/ai-powered-apps-struggle-with-long-term-retention-new-report-shows); [Computing](https://www.computing.co.uk/news/2026/ai-powered-apps-struggle-retain-subscribers)

**Companions**
- Appfigures via TechCrunch (Aug 2025): 337 monetizing companion apps, $221M lifetime consumer spend as of Jul 2025, projected >$120M for FY2025 - [TechCrunch](https://techcrunch.com/2025/08/12/ai-companion-apps-on-track-to-pull-in-120m-in-2025)
- Character.ai: Sacra est. $30M annualized (Jul 2025) -> $50M (end 2025), $9.99 c.ai+ sub; banned open-ended chat for under-18s effective 25 Nov 2025 with age verification incl. facial recognition/ID fallback; teen backlash and "quit" posts; pivot to creation features - [Sacra](https://sacra.com/c/character-ai/); [TechCrunch, 29 Oct 2025](https://techcrunch.com/2025/10/29/character-ai-is-killing-the-chatbot-experience-for-minors/); [Bloomberg](https://www.bloomberg.com/news/articles/2025-10-29/character-ai-to-ban-children-under-18-from-talking-to-its-chatbots); [Sherwood](https://www.sherwood.news/tech/teens-are-upset-that-they-cant-speak-to-character-ai-chatbots-anymore)
- Replika: Sacra est. $24-30M/yr, ~2M MAU - [Roborhythms citing Sacra](https://roborhythms.com/ai-companion-app-market-2026). No Talkie revenue found.

**Voice notes / dictation / transcription**
- Wispr Flow: $280M Series B at $2B valuation led by Menlo (17 Aug 2026; one source says $260M), total ~$361M; revenue +150% for four straight quarters; ~100K businesses; iOS app Jun 2025, Android Feb 2026 - [AI Business](https://aibusiness.com/generative-ai/speech-to-text-ai-specialist-valued-at-2b); [AI Weekly](https://aiweekly.co/node/10188); [ValueAdd VC](https://valueaddvc.com/blog/wispr-flow-2b-valuation-280m-series-b-ai-dictation-2026)
- Granola: $125M Series C at $1.5B (Mar 2026, Index), total ~$192M; iOS app Apr 2025; API/MCP server; enterprise pivot - [TNW](https://thenextweb.com/news/granola-series-c-meeting-ai-enterprise-context); [TechCrunch May 2025 ($43M at $250M)](https://techcrunch.com/2025/05/14/ai-note-taking-app-granola-raises-43m-at-250m-valuation-launches-collaborative-features)
- Plaud: see KQ1. Otter: no revenue data found.

**AI browsers on mobile**
- Comet: only AI-first browser on iOS+Android, free since 23 Mar 2026. Dia: macOS only. Arc: maintenance mode. ChatGPT Atlas: conflicting reports it was retired Aug 2026 with agentic browsing moved to ChatGPT desktop app + Chrome extension (two secondary sources; unverified) - [Composite](https://composite.com/blog/best-new-ai-browsers); [Supercharge](https://www.superchargebrowser.com/library/best-ai-browsers-2026/); [Dupple](https://dupple.com/learn/best-ai-browser)

**AI keyboards**
- Acti (Singapore): agentic keyboard for iOS/Android that takes actions (draft reply, create meeting, run workflow), $5.3M seed led by BITKRAFT, launched 30 Jun 2026 - [Unite.AI](https://www.unite.ai/acti-raises-5-3m-to-turn-the-keyboard-into-an-ai-execution-layer/)
- Rizz-type dating keyboards exist (Rizzboard 4.4 stars/54 ratings, freemium) but no revenue data - [App Store](https://apps.apple.com/us/app/rizzboard/id6484164740); Fleksy SDK powers RizzGPT - [Fleksy](https://fleksy.com/blog/fleksys-virtual-keyboard-now-elevates-rizzgpt-ai-keyboard-across-multiple-platforms)

### Inferences
- Revenue follows (a) frequency (daily chat/edit/dictate) and (b) a tangible artifact (edited video, transcript, document). Pure "insight" apps without an artifact churn.
- The RevenueCat data says the indie opportunity is high-conversion, high-early-LTV products with a retention hook (data accumulation, history, streaks) to fight 30%-faster churn.
- Education, photo/video and translation dominate the mobile top 50 by MAU; chat assistants dominate by revenue. Finance/trading does not appear anywhere in the a16z mobile top 50.

### Gaps
- No category-level revenue split (chat vs photo vs companions) from Sensor Tower 2026 in accessible text.
- No Appfigures-specific retention data (only RevenueCat).
- Talkie, Otter revenue; mobile adoption numbers for any AI browser.

## KQ4. Personal-agent-from-phone pattern (OpenClaw, Claude Code remote, Happy/Omnara, Poke)

### Takeaway
"Run the agent on a box, talk to it from a messenger" became the dominant power-user pattern in 2026: OpenClaw hit ~347K GitHub stars (fastest-growing repo ever), its creator was hired by OpenAI (Feb 2026) with the project moved to a foundation, and official iOS/Android pairing apps shipped 29-30 Jun 2026; Poke (SMS/iMessage agent) did 100M+ messages in ~3 months and was bought by Cognition (Jul 2026). Anthropic's Claude Code gained official mobile access (Remote Control + cloud sessions in the Claude app), spawning a cottage industry (Happy, Omnara, SeaWork, Grass). What's missing: non-terminal setup, security, cost visibility, and sessions that survive a closed laptop.

### Cited Findings

**OpenClaw (ex-Clawdbot/Moltbot) - confirmed**
- Published Nov 2025 as Clawdbot, renamed OpenClaw late Jan 2026; fastest-growing open-source project in GitHub history; 347K+ stars by Apr 2026 - [Respan market map](https://www.respan.ai/market-map/compare/openclaw-vs-strands). a16z: 68K stars in weeks, then most-starred repo in early Mar 2026 passing React and Linux; "requires Terminal knowledge, so not yet mainstream" - [a16z](https://a16z.com/100-gen-ai-apps-6/)
- Reported: 1.5M weekly npm downloads by Mar 2026 - [MEXC news](https://www.mexc.com/tr-CT/news/874300) (low-quality source)
- 15 Feb 2026: OpenAI hired creator Peter Steinberger for its personal-agents team; OpenClaw moves to an OpenAI-sponsored foundation; a16z describes it as "acquired"; Meta also reportedly bid (dollar figures unverified) - [Bloomberg](https://www.bloomberg.com/news/articles/2026-02-15/openai-hires-openclaw-ai-agent-developer-peter-steinberg); [Tom's Guide](https://tomsguide.com/ai/openai-hires-the-developer-behind-openclaw-this-is-how-ai-agents-grow-up); [PureAI (190K stars at hire)](https://pureai.com/Articles/2026/02/17/OpenAI-Hires-OpenClaw-Founder-as-Agentic-AI-Debate-Intensifies.aspx)
- Telegram was the first and default channel; WPP Research test: ~19M tokens across 373 messages just to set up WhatsApp+Telegram channels - [WPP Research](https://cms.research.wpp.com/?p=1355); [ifanr](https://www.ifanr.com/1656512)
- Native iOS/Android apps announced 29/30 Jun 2026: pair phone to a self-hosted OpenClaw Gateway (Mac/PC/Linux) via QR/setup code; the app runs no model itself - [TechCrunch](https://techcrunch.com/?p=3137864); [Digital Trends](https://www.digitaltrends.com/?p=5986371); [WWWhatsnew](https://wwwhatsnew.com/2026/07/04/openclaw-android-ios-agente-ia-codigo-abierto-movil/)
- Security risk flagged as growing alongside ecosystem - [ifanr](https://www.ifanr.com/1656512)

**Poke (The Interaction Company) - confirmed**
- Agent over iMessage/SMS/Telegram; $15M seed at $100M (General Catalyst), later $10M (Spark) at $300M post; Apple cleared it for Messages for Business Jun 2026; 100M+ message exchanges in ~3 months; Cognition agreed to acquire it 23 Jul 2026 (reported nine-figure, unconfirmed) - [Dealroom](https://dealroom.co/companies/poke/); [StartupFortune](https://startupfortune.com/cognition-buys-poke-to-plant-its-ai-agent-inside-your-text-messages/); [sources.news "OpenClaw for normies"](https://sources.news/p/poke-openclaw-for-normies)

**Claude Code on phone - confirmed (official docs + coverage)**
- No standalone Claude Code mobile app; the Code tab in the Claude app hosts cloud sessions (run on Anthropic infra, survive closed laptop) and Remote Control (drives your own machine, which must stay on); pair via QR or claude.ai/code; requires claude.ai account (not Console API key / Bedrock) - [Claude Code docs: mobile](https://code.claude.com/docs/en/mobile)
- Remote Control shipped as research preview (sources differ: Max only vs Pro+Max) - [The Decoder](https://the-decoder.com/claude-code-sessions-now-accessible-from-any-device/); [Techzine](https://www.techzine.eu/news/devops/139101/remote-control-extends-claude-code-to-the-mobile-app/)
- Known pain: iPhone app "No sessions found" bug - [GitHub issue #64841](https://github.com/anthropics/claude-code/issues/64841); community posts on "plugging holes" in Remote Control - [dev.to](https://dev.to/shimo4228/claude-code-from-iphone-plugging-3-holes-in-remote-control-17cf)
- a16z: Claude Code reached $1B run-rate in six months; OpenAI Codex 2M WAU growing 25%/week (early Mar 2026) - [a16z](https://a16z.com/100-gen-ai-apps-6/)

**Third-party Claude Code mobile tools**
- Happy (slopus/happy): open-source (MIT), `npm i -g happy-coder`, QR pairing, E2E encryption, phone<->desktop handoff; components happy-cli/happy-server/mobile client - [Korben](https://korben.info/en/happy-claude-code-mobile-assistant.html); [Happy docs](https://www.mintlify.com/slopus/happy/quickstart)
- Omnara: YC-backed; supports Claude Code + Codex, voice input, Apple Watch - [YC](https://ycombinator.com/companies/omnara); [SeaWork comparison, Jul 2026](https://seawork.ai/en/blogs/omnara-vs-happy-vs-seawork/)
- Grass positions as the only tool covering all three major agents with sessions that keep running with laptop off; Anthropic's Remote Control "dies when laptop closes" - [CodeOnGrass blog, Jun 2026](https://codeongrass.com/blog/is-there-a-mobile-app-for-claude-code/) (vendor source)

### Inferences
- The messaging-channel interface (Telegram/iMessage/WhatsApp) beat dedicated apps for agents in 2026 because it needs no App Store review, has push built in, and works on every device; indies can ship an "agent" with zero native code.
- Everything in this pattern assumes a technical user with a server. The "normies" layer (Poke) was acquired within a year, signaling demand; a hosted, vertical, one-click agent reachable by chat remains open space.
- Missing pieces consistently cited: setup complexity (19M tokens to configure channels), security of always-on agents with broad permissions, cost visibility, and persistence when the host machine sleeps.

### Gaps
- No data on how many OpenClaw users run it via phone/Telegram; no Happy/Omnara user counts.
- No official plan-eligibility confirmation for Claude Code Remote Control beyond docs' "may not be in your plan" caveat.

## KQ5. Niche gaps often cited (notifications, in-app banking/trading actions, share-sheet, background agents, agentic keyboards, voice task completion, car, accessibility, elderly, kids)

### Takeaway
Most "obvious" niches are either structurally blocked by the platforms (background agents, accessibility-service automation on Android, acting inside banking apps) or being absorbed by OS vendors (Gemini in Android Auto/CarPlay Maps, Gemini Intelligence acting across apps, Siri App Intents). The open lanes are: share-sheet-first capture-to-action apps (ChatGPT's own users complain it's weak here), agentic keyboards (only one funded startup), vertical "proactive" agents that run server-side and push to the phone, and under-served populations (elderly: ElliQ is $600-1,000/yr hardware; kids: Character.ai exited under-18 open chat; blind/low-vision: Be My Eyes has 1M users but AI call-displacement unknown).

### Cited Findings

**Background / proactive agents on iOS**
- iOS background tasks traditionally get ~30 seconds; iOS 27 adds `LongRunningIntent` to extend background execution for App Intents with required progress reporting - [Apple docs](https://developer.apple.com/documentation/appintents/longrunningintent.md); [Blake Crosley](https://blakecrosley.com/blog/app-intents-ios-27-background-execution)
- Background execution is opportunistic; agents needing 30s-1h get suspended; checkpoint/resume recommended - [agent-native mobile patterns](https://cdn.jsdelivr.net/npm/compound-engineering-pi@0.2.4/skills/agent-native-architecture/references/mobile-patterns.md) (community guide, marked needs validation)
- Pre-WWDC report: Apple planned an App Store "lane"/framework where developers declare which functions agents may call - [AI Weekly](https://aiweekly.co/alerts/apple-plans-app-store-lane-for-ai-agents-at-wwdc)

**Android automation via Accessibility Service**
- Google Play policy (effective 15 Oct 2021) explicitly says automation tools, assistants, monitoring apps etc. are *not* accessibility tools; non-accessibility uses need a Permission Declaration Form plus prominent disclosure/consent; misuse leads to removal - [XDA](https://www.xda-developers.com/google-trying-limit-apps-accessibility-service/); [ptkd](https://ptkd.com/journal/android-accessibility-service-abuse-security). No 2026 policy naming AI agents found (gap) - but Google's own Gemini Intelligence now occupies that role (see KQ2).

**Share-sheet to agent**
- Claude: select text anywhere -> Share -> Claude; Shortcuts integration adds Claude to Share Sheet - [Anthropic support](https://support.anthropic.com/?q=shake)
- ChatGPT users complain sharing always creates a new chat and that "ChatGPT Plus is losing everyday usage to better-integrated competitors" (Grok appears directly in Share Sheet) - [OpenAI community thread 1](https://community.openai.com/t/ios-share-sheet-allow-choosing-an-existing-chat-instead-of-always-creating-a-new-one/1389070); [thread 2](https://community.openai.com/t/ios-share-sheet-integration-chatgpt-plus-is-losing-everyday-usage-to-better-integrated-competitors/1400200)
- Raycast iOS Share Extension exposes AI Commands from any app - [Raycast manual](https://manual.raycast.com/ios/share-extension.md)

**Notification/inbox triage**
- Search found only email triage (Superhuman split inbox, now part of Grammarly; Gmail Gemini summary cards rolled out May 2025; Shortwave etc.); no funded startup doing AI triage of *push notifications* on mobile - [Leave Me Alone](https://leavemealone.com/blog/ai-email-organizers/); [echai](https://echai.ventures/how-founders-use-ai/productivity/how-do-founders-get-to-inbox-zero-with-ai-email-tools-superhuman-ai-gemini-shortwave); [thisandthat](https://www.thisandthat.chat/blog/inbox-platforms-triaging-notifications/)

**Agentic keyboards**
- Acti ($5.3M seed, Jun 2026) is the only funded "keyboard that takes actions" found; analysts note Apple/Google/AI labs all want the same surface - [Unite.AI](https://www.unite.ai/acti-raises-5-3m-to-turn-the-keyboard-into-an-ai-execution-layer/)

**AI acting inside banking/trading apps**
- Only first-party: Robinhood Cortex (plain-English buy/sell equities & crypto, research, settings; ~1M users per Q1 2026 call; Gold-subscriber targeted; extended to advisors via TradePMR Jun 2026) - [Robinhood support](https://robinhood.com/us/en/support/articles/cortex); [Ecosistema Startup](https://ecosistemastartup.com/?p=83399); [ai2.work](https://ai2.work/blog/robinhood-pushes-cortex-ai-into-advisor-workflows-via-tradepmr). Public.com Alpha exists as in-app research assistant; no user data - [Walnut](https://walnutinvest.com/resources/which-brokers-have-an-ai-assistant). No third-party app found that acts inside a bank/broker app on mobile.

**Car**
- Gemini rolled into Android Auto (2025-26); Google initially said no CarPlay, but May 2026 Google Maps gained Gemini support on CarPlay; GM adding Gemini to 2022+ vehicles; user complaints about crashes/performance after updates - [Driven Car Guide](https://www.drivencarguide.co.nz/news/googles-gemini-ai-assistant-rolls-into-android-auto/); [autoevolution Gemini tag](https://www.autoevolution.com/newstag/gemini/); [TechCrunch](https://techcrunch.com/?p=3006286)

**Accessibility (blind/low-vision)**
- Be My Eyes: 10M+ volunteers, 1M+ blind/low-vision users, 150+ countries, 180 languages (12 Mar 2026 milestone); Be My AI built on GPT-4 vision since 2023; company has not published how much AI displaced human calls - [Yespress](https://yespress.io/be-my-eyes); [CivicTech Guide](https://civictech.guide/projects/be-my-aitm)

**Elderly**
- ElliQ (Intuition Robotics): $600-$1,000/yr subscription; state-agency pilots (NY Office for the Aging; 95% self-reported loneliness reduction, program-reported); units limited to participating counties and funding - [Spectrum News, 15 May 2026](https://spectrumlocalnews.com/us/snplus/your-mental-health/2026/05/15/ai-companions-for-older-adults-); [NY OFA](https://aging.ny.gov/node/14371). No 2026 user counts found.

**Kids**
- Character.ai removed open-ended chat for under-18s (25 Nov 2025) with ID/face verification fallback - [TechCrunch](https://techcrunch.com/2025/10/29/character-ai-is-killing-the-chatbot-experience-for-minors/). No funded kid-specific mobile AI agent found in this research (gap).

### Inferences
- Any indie "agent" that needs to run continuously on the phone or drive other apps' UIs is building on sand; the durable architecture is server-side agent + push/messenger delivery + share-sheet/Shortcut/App Intent entry points.
- Share-sheet-first UX is a visible, cheap differentiator: even ChatGPT is criticized for it, and it maps directly onto "send a tweet/post to an analyzer" use cases.
- Finance is the one large consumer vertical where OS agents and labs have *not* shipped acting agents (regulatory exposure), leaving room for structured-idea tracking rather than execution.

### Gaps
- No 2026 Google Play policy text on AI agents specifically; no documented App Store rejection cases for agent apps found.
- No startup data for push-notification triage, kids' agents, or third-party in-bank agents.

## KQ6. Business constraints: store policy, fees, API costs, retention, what monetizes

### Takeaway
Fees are loosening but unsettled: Google cut Play commission to 20% (Epic settlement, Mar 2026); Apple still charges 27% on US external-link purchases while the Ninth Circuit remand and a Supreme Court petition play out (stay granted 6 Apr 2026), and EU DMA tiers cap at ~20%. Unit economics hinge on usage skew (median user ~$0.80/mo to serve vs $40+ for a 95th-percentile user), so rate limits and tiering are mandatory; AI apps convert and earn early (RLTV +39-41%) but churn 30% faster, so retention mechanics decide survival.

### Cited Findings
- Apple/Epic status (6 Apr 2026): 27% commission on external payments still applies; Ninth Circuit upheld contempt (Dec 2025), denied rehearing (Mar 2026), remanded to set a rate, then stayed its mandate 6 Apr; Apple to petition Supreme Court; only a few devs (Spotify, Kindle, Patreon) use external links - [TechCrunch](https://techcrunch.com/2026/04/06/apple-epic-games-lawsuit-supreme-court-appeal-app-store-commission/)
- Google settled with Epic Mar 2026 and cut Play commission to 20% - [TechCrunch](https://techcrunch.com/2026/04/06/apple-epic-games-lawsuit-supreme-court-appeal-app-store-commission/)
- EU DMA layered fees: combined maximum on external payments up to ~20% (third-party guide) - [Funnelfox](https://blog.funnelfox.com/apple-app-store-fees-2026-eu-dma/); [Adapty](https://adapty.io/blog/alternative-payments-in-the-app-store). Unverified Aug 2026 headline: Apple seeking 15% on outside payments, risk of zero - [ProPakistani](https://propakistani.pk/2026/08/19/apple-wants-15-from-outside-app-payments-it-could-end-up-with-zero/amp/)
- Inference cost skew: median user ~$0.80/mo vs $40+ for 95th percentile on the same plan; a power user can cost 100x a light user; typical Plus-type user $3-8/mo inference vs $20 price; AI gross margins 55-70% (or Bessemer 20-60%) vs 70-90% SaaS; recommend per-cohort contribution margin and ads on free tier - [Beyond10x](https://beyond10x.substack.com/p/the-math-behind-your-20-subscription); [Thrad](https://www.thrad.ai/content/ai-app-unit-economics-and-monetization); [Monetizely](https://www.getmonetizely.com/articles/the-economics-of-ai-first-b2b-saas-in-2026-margins-pricing-models-and-profitability); [tianpan](https://tianpan.co/blog/2026-04-17-pricing-ai-features-unit-economics) (all vendor/commentary sources)
- Retention/conversion: see RevenueCat figures in KQ3 - [TechCrunch](https://techcrunch.com/2026/03/10/ai-powered-apps-struggle-with-long-term-retention-new-report-shows)
- What monetizes on mobile: assistants (ChatGPT $2.48B 2025), photo/video (61% AI share), companions ($120M+/yr), dictation/notes (Wispr/Granola/Plaud valuations), hardware+sub bundles (Plaud ~50% paid conversion) - see KQ1/KQ3 citations. Claude's ARPU 5x rise shows a smaller app can lift ARPU fast - [Sensor Tower](https://sensortower.com/press/sensor-tower-state-of-ai-2026-report-global-time-spent-on-generative-ai-apps-projected-to-more-than-double-year-over-year)
- Messaging-channel agents (Poke on iMessage) got Apple Messages for Business clearance, bypassing app review for the core surface - [StartupFortune](https://startupfortune.com/cognition-buys-poke-to-plant-its-ai-agent-inside-your-text-messages/)

### Inferences
- For an indie, web-first billing plus a thin mobile client (or messenger-channel delivery) avoids both the 27/30% fee and the agent-policy ambiguity; Google's 20% makes Android IAP more tolerable than iOS.
- Cheap models for the median user and hard caps/tiers for the tail are table stakes; usage-based or credit tiers map better to agentic workloads than flat subs.

### Gaps
- No App Store review guideline text specific to AI agents found; no data on rejection rates.
- No primary (audited) margin data for consumer AI apps.

## KQ7. Finance/trading-specific mobile AI: ideas from social posts, share-sheet-to-analysis, tracked P&L; what traders say is missing

### Takeaway
Nothing found that does the full loop "social post -> structured trade idea -> tracked P&L" on mobile. Adjacent winners monetize *copying verified people* (Autopilot: 3M downloads, ~$1B AUM, $99/yr, $8M raise Nov 2025; Dub: $47M raised, copy-trade Pelosi/others) or *verified positions as social proof* (AfterHour, $4.5M seed). Idea-from-tweet tools are tiny (MacroThis Chrome extension; Alpstein crypto with 3 upvotes; Finfluencers.trade leaderboard with no reviews). Finance is absent from the a16z mobile top 50. Regulators keep prosecuting Discord/Twitter signal sellers (SEC/DOJ Atlas Trading, ~$100M), which argues for transparent, auditable tracking over "signals".

### Cited Findings
- Autopilot (Pelosi tracker app): $8M raise (Nov 2025) to expand to NYC; ~$1B under management; 3M downloads; $99/yr subscription; links brokerage to follow portfolios; disclaimer that congressional trades lag up to 45 days and app is "more for entertainment"; pivoting to a general insider-trading portfolio after Pelosi's retirement (term ends Jan 2027) - [Techleap/Finder](https://finder.techleap.nl/news/feed/autopilot-raises-8m-expands-operations); [ABC fact check](https://abcnews4.com/news/nation-world/nancy-pelosi-stock-trades-spark-legislation-and-investing-app-frenzy-lawmakers-congress-trading); [Benzinga, Mar 2026](https://www.benzinga.com/news/politics/26/03/51248325/exclusive-pelosi-tracker-creator-reveals-top-3-lawmakers-to-watch-new-trump-white-house-stock-strategy)
- Dub (copy trading): $30M Series A (May 2025, Notable Capital, Neo) + $5.5M SVB venture debt; total $47M; earlier $17M seed (Tusk; backers incl. Dara Khosrowshahi, Nathan Rodland); free tier to copy up to two people; expanding to crypto and event contracts - [Fortune](https://fortune.com/article/copy-trading-dub-30-million-series-a-notable-capital-neo); [Finance Magnates](https://www.financemagnates.com/forex/us-copy-trading-platform-dub-secures-17-million-in-funding-investment/). No 2026 round found.
- AfterHour: "traders put their money where their mouth is" (verified positions); $4.5M seed (Jun 2024; General Catalyst, Pear, Founders Fund among investors); no 2026 news - [VCBacked](https://www.vcbacked.co/company/afterhour); [CB Insights](https://www.cbinsights.com/company/afterhour/financials)
- Robinhood Cortex: ~1M users (Q1 2026 call), natural-language trading/research for Gold; Robinhood framing retail's future as "betting" (Axios, Dec 2025) - [Robinhood](https://robinhood.com/us/en/support/articles/cortex); [Axios](https://www.axios.com/2025/12/17/ai-robinhood-stock-market)
- Tweet-to-trade tools: MacroThis Chrome extension turns a tweet into trades with conviction/risk levels, no P&L tracking shown - [Chrome Web Store](https://chromewebstore.google.com/detail/dgalakiobajmopegnnpihhlmohniimle); Alpstein generates crypto positions (entry/SL/TP) from news with live P&L, 3 Product Hunt upvotes - [hunted.space](https://www.hunted.space/product/alpstein); Bollwerk Trade Ideas feed with entry/target/stop - [Bollwerk docs](https://app.bollwerk.ai/documentation/trade-ideas); Finfluencers.trade tracks influencer performance via verified signals, leaderboards, no user reviews (Mar 2026) - [PeerPush](https://peerpush.com/p/finfluencerstrade); historical Trump2Cash bot (2017) - [Boing Boing](https://boingboing.net/2017/02/10/google-x-engineer-writes-a-bot.html)
- Paper-trading/idea-journal apps: On Paper (iOS, options, multiple sandbox portfolios, 2.9 stars/159 ratings); BlazeTrade (options journal, unusual-trade alerts, paper trading; vendor claims) - [App Store: On Paper](https://apps.apple.com/us/app/on-paper-investing-playground/id1522044982); [WTOP paper-trading roundup, Aug 2026](https://wtop.com/news/2026/08/5-of-the-best-sites-for-paper-trading-stocks/)
- Fraud backdrop: SEC + DOJ charged 8 Twitter/Discord influencers (Atlas Trading) in a ~$100M (SEC) / $114M (DOJ) pump-and-dump; voice chats they believed private were recorded - [The Wealth Advisor](https://www.thewealthadvisor.com/article/sec-charges-8-social-media-influencers-alleging-100m-pump-and-dump-stock-scheme); [InvestmentNews](https://investmentnews.com/?p=230293). Brazil's CVM also pursued Fintwit influencers - [Suno](https://www.suno.com.br/noticias/?p=292900)
- Benzinga guidance on FinTwit: "trust only after verifying"; people whose positions are working may be promoting them - [Benzinga](https://www.benzinga.com/22/07/28108081/how-to-manage-fintwit-and-other-social-media-platforms)

### Inferences
- Demand signal is for *accountability of other people's calls* (Autopilot/Dub/AfterHour all sell verification or copying of real positions), not for more AI-generated signals. A share-sheet -> structured idea -> auditable paper P&L product sits between "copy a verified trader" apps and journaling apps, and no funded mobile player occupies it.
- The absence of finance in the a16z mobile top 50 plus Robinhood's first-party Cortex means third-party execution is unlikely to win; tracking/accountability and public track records are the defensible layer.
- Regulatory posture (SEC/DOJ cases, Autopilot's "entertainment" disclaimer) suggests positioning as tracking/education, with explicit no-advice framing, and surfacing caller track records as the core value.

### Gaps
- No direct Reddit (r/wallstreetbets, r/options) or fintwit threads surfaced articulating what users want in idea-tracking tools; web search returned app listings, not community complaints. This should be sampled manually (Reddit search, X) before product decisions.
- No revenue figures for Autopilot, Dub, AfterHour; no 2026 funding news for Dub/AfterHour.
- No evidence of a mobile app doing tweet -> tracked P&L at scale; the lack of findings is itself the signal but should be confirmed with App Store/Play Store keyword searches.
