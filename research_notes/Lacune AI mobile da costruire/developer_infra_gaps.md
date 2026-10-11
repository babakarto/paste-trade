# Developer-side infrastructure and tooling gaps for building AI agents / AI features on mobile (iOS + Android), as of 11 October 2026

Scope note: this is an evidence-backed opportunity map. Each key question below separates what **exists and works**, what **exists but is immature**, and what is **missing**. All dates are stated explicitly; everything is as of 2025–Oct 2026. Where only secondary sources were available this is flagged. Star counts are from the GitHub pages as fetched on 2026-10-11.

---

## KQ1. MCP on mobile: clients, servers, "phone as MCP server", and what Claude/ChatGPT mobile apps support

### Takeaway
Mobile MCP today is almost entirely "remote MCP consumed from a phone" (Claude mobile app) or "a desktop MCP server that drives a phone via ADB/Xcode" (mobile-next/mobile-mcp). The "phone as MCP server exposing its own capabilities" category exists only as a handful of small Android projects (the largest ~700 stars) that depend on Accessibility Service or Shizuku, with no iOS equivalent at all; Android's official answer (AppFunctions) is explicitly described by Google as "the mobile equivalent of MCP tools" but is experimental and Gemini-gated.

### Cited Findings

**Exists and works**
- Claude mobile apps (iOS/Android) support remote MCP connectors; Anthropic's support article states web connectors are available to all users on Claude Mobile, services connected on web/desktop appear on iOS/Android at next login, and "Installing connectors on mobile is currently in beta." Custom (remote MCP) connectors are listed only for Claude web, Cowork and Claude Desktop; free users are limited to one custom connector — [Anthropic Support: Pre-built web connectors using remote MCP](https://support.claude.com/en/articles/11176164-pre-built-web-connectors-using-remote-mcp)
- Third-party guides date mobile remote-MCP support to 26 July 2025 and note new servers must be added on claude.ai web, after which they sync to mobile; local (stdio) MCP servers are not available on mobile because mobile apps can't run local scripts — [DEV Community: How to set up remote MCP on Claude iOS/Android](https://dev.to/zhizhiarv/how-to-set-up-remote-mcp-on-claude-iosandroid-mobile-apps-3ce3); [clauder-navi iPad MCP guide](https://www.clauder-navi.com/en/claude-ipad-mcp/)
- mobile-next/mobile-mcp (Apache-2.0): 9.0k stars, 801 forks, 459 commits, 33 tools (device mgmt, app lifecycle, screenshots, accessibility-tree element listing, tap/swipe/type, logs/crashes). It runs on a **host computer** (requires Xcode / Android Platform Tools; uses `xcrun simctl` and `adb`), supports iOS simulator, iOS real device over USB, Android emulator and Android real device over adb; HTTP mode uses Streamable HTTP at `/mcp` and accepts unauthenticated connections unless `MOBILEMCP_AUTH` is set; telemetry on by default — [GitHub: mobile-next/mobile-mcp](https://github.com/mobile-next/mobile-mcp)
- Maestro ships an MCP server inside its CLI (`claude mcp add maestro -- maestro mcp`) with tools `list_devices`, `inspect_screen`, `run`, `take_screenshot`, plus Maestro Cloud tools — [Maestro MCP](https://maestro.dev/mcp)

**Exists but immature ("phone as MCP server")**
- danielealbano/android-remote-control-mcp (MIT): 697 stars, 101 forks, 974 commits. An Android app that runs an MCP server **on the phone** (Ktor+Netty, Streamable HTTP JSON-only at `/mcp`, default `127.0.0.1:8080`, optional `0.0.0.0`, static bearer token and/or built-in OAuth 2.1 server, Cloudflare Quick Tunnels / ngrok for remote access). Exposes "57 MCP Tools across 14 Categories" (screen introspection, gestures, text input, files, app management, camera, intents, notifications, location, sharing). Accessibility Service is "required… nothing works without it"; on Android 13+ sideloads it may be blocked by "Restricted settings". Distributed as APK from GitHub Releases (GMS and FOSS flavors); Play Store listing not stated. Claude.ai/ChatGPT OAuth connectors need a public HTTPS tunnel. Privacy-mode name detection benchmark shows 0.8% detection. No iOS support. Labelled "for research and educational purposes only" — [GitHub: danielealbano/android-remote-control-mcp](https://github.com/danielealbano/android-remote-control-mcp)
- shizzgar/android-shizuku-mcp: MCP server running in Termux that exposes a single universal shell tool routing high-privilege commands via Shizuku's `rish`; needs Termux, Termux:API, Shizuku via Wireless Debugging or root; Apache-2.0; ~3 stars per directory listing — [glama.ai listing](https://glama.ai/mcp/servers/j97byge8zk); [remoteopenclaw listing](https://www.remoteopenclaw.com/mcp/shizzgar/shizuku-mcp)
- "Mythara" is described in the awesome-shizuku changelog (Aug 2026) as an open-source local-first agentic AI OS layer for Android running 65+ on-device tools (calls, SMS, calendar, …) via Shizuku; I could not locate/verify its repo URL, license or star count — [GitHub: timschneeb/changelog-awesome-shizuku](https://github.com/timschneeb/changelog-awesome-shizuku)
- Apple Shortcuts ↔ MCP: all found servers run on a Mac and expose "run shortcut" (recursechat/mcp-server-apple-shortcuts, Apache-2.0) or generate `.shortcut` files (Kalypsokichu-code/apple-shortcuts-mcp-server); the only iOS-side pattern found is a Shortcut POSTing to a self-hosted `/mcp` endpoint — [Glama: Apple Shortcuts MCP](https://glama.ai/mcp/servers/gi0gb63sum); [augmentcode listing](https://www.augmentcode.com/mcp/mcp-server-apple-shortcuts)
- Google positions AppFunctions as "the mobile equivalent of MCP tools": "MCP standardizes how agents connect to server-side tools, while AppFunctions provide the same mechanism for Android apps", and says agents are likely to consider remote MCP tools and local AppFunctions together. Status: Experimental, API "subject to change", Android 16 (API 36) only; Gemini integration in private preview with trusted testers as of May 2026 — [Android Developers: Overview of AppFunctions](https://developer.android.com/ai/appfunctions)

**ChatGPT mobile**
- OpenAI's help article on Developer Mode / full MCP connectors (English version returned HTTP 403 on fetch) is, in translated copies, described as a beta rolling out gradually for Business/Enterprise/Edu with write actions; third-party guides describe setup only via web Settings → Connectors. I found **no** OpenAI statement about MCP connector availability in the iOS/Android ChatGPT apps — [OpenAI Help 12584461 (de)](https://help.openai.com/de-de/articles/12584461-developer-mode-apps-and-full-mcp-connectors-in-chatgpt-beta); [sticklight ChatGPT MCP guide](https://sticklight.com/help/mcp/chatgpt-mcp)

### Inferences
- The "phone as MCP server" niche is open: the biggest Android project is <1k stars, requires Accessibility Service (now a Play-policy problem, see KQ3), is sideload-only and carries a research-only disclaimer. Nothing comparable exists for iOS because iOS has no public API to read other apps' notifications, drive other apps' UIs, or run a persistent background HTTP server.
- A legitimate Android MCP server that exposes **first-party data** (contacts, calendar, SMS, call log, location, clipboard, health via Health Connect, notifications via NotificationListenerService) over Streamable HTTP with OAuth, using normal runtime permissions rather than Accessibility Service, appears not to exist as a polished product — that is a fillable indie gap, with the caveat that any claude.ai/ChatGPT connector needs a public HTTPS endpoint (tunnel or relay).
- For iOS, the closest fillable gap is an App Intents + Shortcuts-based "tool bridge" (Shortcuts "Use Model" action + App Intents schemas), not MCP proper.

### Gaps
- Could not confirm whether ChatGPT iOS/Android apps surface custom MCP connectors (OpenAI page 403).
- No reliable star count/URL for Mythara; no verified data on whether android-remote-control-mcp is on Play/F-Droid.
- No found project exposes Health Connect / HealthKit data as MCP tools.

---

## KQ2. Apple: what a third-party AI agent can legitimately do on iOS and where it hits a wall

### Takeaway
Apple gives developers a rich but tightly bounded surface — App Intents (now the only route into Siri), Foundation Models with Tool protocol (on-device ~4K-token budget in iOS 26; multimodal, PCC server model and third-party `LanguageModel` providers in iOS 27 betas), Visual Intelligence via `IntentValueQuery`, and the Shortcuts "Use Model" action — but a third-party app cannot act across other apps, run persistently in the background, or download/execute code (2.5.2). Apple enforced 2.5.2 against vibe-coding apps (Replit, Vibecode blocked; Anything removed 26 March 2026) and was reported in May 2026 to be exploring a sanctioned path for agent apps; nothing in the 8 June 2026 guidelines mentions agents.

### Cited Findings

**Exists and works (iOS 26, shipped fall 2025)**
- Foundation Models framework: on-device model with Tool protocol for tool calling and `@Generable` structured output; third-party reviewers describe it as "trained for basic tool-calling and structured data output" with a ~4K-token budget shared across prompt and response (session throws on overflow), guardrail false positives, device/Apple-Intelligence availability checks required — [MacStories iOS 26 review ch.8](https://www.macstories.net/stories/ios-and-ipados-26-the-macstories-review/8); [Natasha The Robot: FoundationModels limitations](https://www.natashatherobot.com/p/apple-foundation-models)
- Shortcuts gained the "Use Model" action (On-Device / Cloud / ChatGPT options, with Follow Up) at WWDC25 — [Apple WWDC25 session 260](https://developer.apple.com/videos/play/wwdc2025/260/); [9to5Mac 2025-06-16](https://9to5mac.com/2025/06/16/shortcuts-app-has-chatbot-like-apple-intelligence-powers-in-ios-26/)
- Visual Intelligence integration via `IntentValueQuery` (takes a `SemanticContentDescriptor`, returns `AppEntity` instances); interactive snippets surface in Spotlight/Visual Intelligence/Siri (third-party write-up, not verified against Apple docs) — [blakecrosley.com: App Intents 2.0 in iOS 26](https://blakecrosley.com/blog/app-intents-2-ios-26-additions)
- Background: `BGContinuedProcessingTask` (iOS 26+) continues user-initiated, user-visible work after the user leaves the app, with dynamic registration; developers report unpredictable expiry for large jobs (≈10GB downloads failing, ≈3GB OK); force-quit kills all background tasks — [Apple Dev Forums 805554](https://developer.apple.com/forums/thread/805554); [DEV: WWDC 2025 background APIs](https://dev.to/arshtechpro/wwdc-2025-ios-26-background-apis-explained-bgcontinuedprocessingtask-changes-everything-9b5)

**Announced at WWDC26 (8 June 2026; developer betas; GA expected fall 2026) — exists but immature**
- Foundation Models: image input with `@Generable`; a Private Cloud Compute server model with no API key and no token cost to the developer, **gated to App Store Small Business Program members with <2M downloads** (entitlement required), with a user daily cap raisable via iCloud+; third-party models via a `LanguageModel` protocol (Google and Anthropic shipping Swift packages for Gemini and Claude; Core AI and MLX ship open-source conformances); multi-session "agentic" APIs (`DynamicProfile`); an open-source utilities package with dynamic tool discovery ("skills") and context management; Instruments shows every prompt/tool call; `fm` CLI on macOS 27; framework to be open-sourced incl. Linux. No new tool-calling API shown; no context-window figure stated — [Apple WWDC26 special presentation 382](https://developer.apple.com/videos/play/wwdc2026/382/); [Superwall: 3 things from WWDC 2026 (26 Jun 2026)](https://superwall.com/blog/3-things-for-developers-from-wwdc-2026)
- Siri routes exclusively through App Intents; apps fitting a built-in App Intent Domain get natural-language import/export; on-screen awareness via `.appEntityIdentifier(...)`; `IndexedEntity` semantic index; `IntentDonationManager.donate`; schema adoption gives automatic confirmation/authentication handling; new `AppIntentsTesting` framework — [WWDC26 382](https://developer.apple.com/videos/play/wwdc2026/382/); [Superwall](https://superwall.com/blog/3-things-for-developers-from-wwdc-2026)
- Core AI announced as the Core ML successor for running developers' own LLMs/generative models on-device (secondary sources; details such as 70B/30 tok/s figures conflict) — [InfoQ 2026-06](https://infoq.com/news/2026/06/apple-core-ai-wwdc); [Callstack: On-device AI after WWDC 2026](https://callstack.com/blog/on-device-ai-after-wwdc-2026-whats-new)
- Xcode 27: agents from Anthropic/OpenAI/Google plus any ACP agent; plugins based on Anthropic's plugin format bundling skills, MCP tools and ACP agents; macOS 27 kernel-level file-access approval for agents — [WWDC26 382](https://developer.apple.com/videos/play/wwdc2026/382/)
- One Substack summary says EU and China get developer APIs but not consumer Siri AI features at launch (unverified) — [codemeetai Substack](https://codemeetai.substack.com/p/apples-worldwide-developers-conference)

**Walls / policy**
- App Store Review Guidelines (Last Updated June 8, 2026): 2.5.2 — apps "may not download, install, or execute code which introduces or changes features or functionality of the app, including other apps"; 3.1.1 bans own unlock mechanisms "such as license keys, augmented reality markers, QR codes, cryptocurrencies…"; 5.1.2(i) requires disclosure and explicit permission before sharing personal data "with third-party AI"; 4.7 allows "chatbots" as non-embedded software with developer responsibility. **No clause mentions agents, LLMs, or autonomous actions** — [Apple App Store Review Guidelines](https://developer.apple.com/app-store/review/guidelines/)
- Enforcement: The Information reported Apple blocked updates to Replit and Vibecode; "Anything" was removed 26 March 2026 after updates had been blocked since December; Apple cited 2.5.2 and told 9to5Mac the action targeted guideline violations, not vibe coding as a concept; proposed compromises included opening generated apps in a separate browser — [9to5Mac](https://9to5mac.com/?p=1045859); [The Decoder](https://the-decoder.com/apple-reportedly-blocks-vibe-coding-apps-from-publishing-updates/); [Gigazine 2026-03-31](https://gigazine.net/gsc_news/en/20260331-apple-pulls-vibe-coding-app-anything/)
- 13–14 May 2026: The Information (syndicated by Bloomberg) reported Apple is exploring how to allow AI-agent apps in the App Store; concerns cited are unreviewable generated code (malware) and IAP bypass; one proposed constraint would bar agents with sweeping system access; Apple has not confirmed — [AppleInsider 2026-05-13](https://appleinsider.com/articles/26/05/13/despite-risks-apple-seeks-ways-to-bring-more-ai-to-the-app-store); [PYMNTS](https://www.pymnts.com/apple/2026/apple-prepares-app-store-for-autonomous-ai-agents/); [OECD.AI incident record](https://oecd.ai/en/incidents/2026-05-14-66b8)
- BYOK precedent: Sept 2024 rejection under 3.1.1 — "the app uses API keys to unlock or enable functionality"; App Review said it was "investigating"; no recorded resolution — [Apple Dev Forums 763884](https://developer.apple.com/forums/thread/763884)
- I found no documented App Store rejection of a specific "AI agent" app under a 2026 agent-specific rule; vendor blogs attribute AI-app rejections to 4.2 (thin wrappers), 4.3 (spam) and 2.5.2 — [vp0.com](https://vp0.com/blogs/does-apple-reject-ai-generated-apps.md); [superappp 2026 guide](https://www.superappp.com/blog/why-apps-get-rejected-from-the-app-store-2026-guide)

### Inferences
- Legitimate iOS agent surface = (a) inside your own app with Foundation Models/Core AI/cloud LLM; (b) exposing your app's actions/entities to Siri, Spotlight, Shortcuts and Visual Intelligence via App Intents; (c) orchestrating other apps only through Shortcuts actions they publish. Cross-app GUI automation, notification reading, and always-on background agents are structurally unavailable, not merely discouraged.
- The PCC server-model gating (<2M downloads, Small Business Program) is explicitly indie-friendly: small teams get a free cloud LLM tier that large competitors cannot use, which is a monetization/cost-structure advantage worth building around once iOS 27 ships.
- Apple's stated inability (May 2026) to reconcile agents with 2.5.2 means "agent that generates and runs code on-device" remains the one category to avoid on iOS until a policy change.

### Gaps
- No Apple primary doc fetched on iOS 26/27 Foundation Models context limits or exact tool-calling changes; 4K figure is from reviewers.
- Live Activities and Action button: no agent-specific sources found; not covered.
- Could not retrieve the primary AppleInsider/The Information text (403); relied on syndications.
- Whether EU/China API availability differs is unverified.

---

## KQ3. Android: walls and openings (Accessibility policy, AppFunctions, Computer Control, Gemini Nano, Shizuku, developer verification)

### Takeaway
Android is bifurcating: Google is shutting the Accessibility-Service back door for autonomous agents (Play policy effective 28 Jan 2026: "an app that autonomously initiates, plans, and executes actions or decisions" is ineligible) while opening two front doors that are **not available to independent developers** — Computer Control (privileged `ACCESS_COMPUTER_CONTROL`, OEM-preloaded assistants only, preview) and AppFunctions (experimental; Gemini pipeline private preview). On-device Gemini Nano via ML Kit GenAI Prompt API is real but hardware-gated; Shizuku/wireless-ADB remains the de-facto power-user route and is at (unconfirmed) risk.

### Cited Findings

**Walls**
- Play "Accessibility API" policy: AccessibilityService is "not designed and cannot be requested for remote call audio recording" or "an app that autonomously initiates, plans, and executes actions or decisions"; use must be documented in the listing; non-assistive apps must complete an accessibility declaration in Play Console, show prominent in-app disclosure and obtain consent; developers should prefer narrower APIs — [Google Play policy: Permissions and APIs that Access Sensitive Information](https://support.google.com/googleplay/android-developer/answer/16558241)
- The January 2026 Play newsletter lists this under "Starting January 28": "any use of the API that enables an app to autonomously initiate, plan, and execute actions or decisions is prohibited" — [Android Developers: Play Monthly, January 2026](https://developer.android.com/newsletter/play-monthly/2026/content/january)
- Computer Control: "allows OEM-preloaded AI assistants to perform task automation on selected apps"; requires the **privileged** `ACCESS_COMPUTER_CONTROL` permission; one active session at a time covering up to six target apps run sequentially on a secure background virtual display ("similar to casting"); system consent dialog; target apps need no changes; assistant navigates by analyzing screenshots; status **Preview**, limited set of target apps; page updated 2026-05-13 — [Android Developers: Android Computer Control](https://developer.android.com/ai/computer-control)
- The `VirtualDeviceManager` reference is reported to say ComputerControl is limited to allow-listed agent apps holding `ACCESS_COMPUTER_CONTROL` and the current ASSISTANT-role holder, with a denylist and user opt-in (from search summary; the page itself was too large to parse) — [VirtualDeviceManager reference](https://developer.android.com/reference/kotlin/android/companion/virtual/VirtualDeviceManager)
- Pre-release reporting described an "Agent control of other apps" privacy settings page in Android 16 QPR2 and a Pixel-10-only "Screen automation" special app access in QPR3 Beta 2 (Jan 2026) with Always allow / Ask every time (default) / Do not allow — [HuaweiCentral](https://www.huaweicentral.com/android-16-qpr2-could-turn-your-phone-into-a-smarter-ai-agent/amp/); [androidmagazine.eu 2026-01-17](https://androidmagazine.eu/en/2026/01/17/android-16-dostane-neuveritelnou-funkci-aplikace-vam-pomohou-ovladat-jine-aplikace/)
- Developer verification: registration requirement starts 30 Sept 2026 in Brazil, Indonesia, Singapore and Thailand, global in 2027; applies to certified devices; sideloading from unverified developers requires an "Advanced Flow" (developer mode, 24-hour wait, restart, biometric) with 7-day or indefinite windows; ADB installs unaffected — [Android Authority (June 2026)](https://www.androidauthority.com/p-3679204/); [Bayton enterprise FAQ](https://bayton.org/android/android-enterprise-faq/google-play-developer-verification-enterprise/)
- Shizuku/on-device ADB risk: after CVE-2026-0073 (fixed 2026-05-01), a Google ADB maintainer in an Issue Tracker thread proposed binding adbd only to the wireless interface (not loopback); the analysis rates implementation "Unverified" and notes no official Google statement as of 27 July 2026 — [braindetox.kr analysis (2026-07-27)](https://braindetox.kr/en/posts/android_adb_restriction_2026.html)

**Exists but immature (openings)**
- AppFunctions: Android 16 (API 36) + Jetpack `androidx.appfunctions` with `@AppFunction(isDescribedByKDoc = true)` / `@AppFunctionSerializable`, XML schema generated and indexed by the OS; callers need `EXECUTE_APP_FUNCTIONS` (protection level not stated on page); test with `adb shell cmd app_function list-app-functions`; Experimental; Gemini integration private preview with trusted testers as of May 2026; EAP accepting registrations without guaranteed access — [Android Developers: AppFunctions](https://developer.android.com/ai/appfunctions)
- ML Kit GenAI APIs (Prompt API, summarization, proofreading, rewriting, image description, speech recognition) run on AICore; most features Beta, speech Alpha; available on MediaTek Dimensity, Snapdragon and Tensor devices (API 26+) — [ML Kit GenAI overview](https://developers.google.com/ml-kit/genai); [InfoQ 2025-06](https://www.infoq.com/news/2025/06/google-mlkit-genai-gemini-nano)
- Gemini Nano claimed on >140M devices as of 21 July 2026; Nano 4 built on Gemma 4; third-party blogs say Nano 4 / "Gemini Intelligence" needs 12GB RAM and Nano v3+ (unconfirmed against Google docs; the 12GB footnote appears tied to the consumer feature) — [ninetwothree.co: Gemini Nano 4](https://www.ninetwothree.co/blog/gemini-nano-4-device-support); [DEV: 12GB RAM floor](https://dev.to/mr_manushukla/gemini-intelligences-12gb-ram-floor-an-android-ai-fallback-plan-for-2026-jeh)
- LiteRT-LM: official docs list tool use "for agentic workflows, with constrained decoding"; v0.14.0 added streaming of tool-call tokens in C/Swift and full tool calling in LiteRT-LM.js; function-calling demo with FunctionGemma in AI Edge Gallery — [LiteRT-LM overview](https://developers.google.com/edge/litert-lm/overview)
- ADK for Kotlin 1.0 GA announced 9 Sept 2026: on-device agents via LiteRT-LM and ML Kit (beta), hybrid via Firebase AI Logic, state in Room and AppSearch; a 1.1.0 appears to exist — [Google Developers Blog](https://developers.googleblog.com/en/announcing-adk-for-kotlin-10-building-production-ready-ai-agents-in-kotlin-android-and-beyond/); [InfoQ 2026-09](https://www.infoq.com/news/2026/09/google-adk-1-0-released/); [ProAndroidDev tutorial](https://proandroiddev.com/building-on-device-ai-agents-on-android-with-google-adk-part-1-the-engine-architecture-bf5639a2f439)
- Shizuku: Android 7+, modes Root / Wireless Debugging (Android 11+) / PC; must be restarted after every reboot in wireless mode; agent projects built on it include AutoGLM-For-Android (vision model + Shizuku taps), Operit AI, Ruto-GLM, Mythara — [Shizuku user manual](https://shizuku.rikka.app/guide/setup/); [AutoGLM-For-Android](https://www.sourcepulse.org/projects/21990844)
- Automation apps: MacroDroid 5.59.2 added an "AI LLM Query" action; Tasker 6.5 added an AI helper for building routines (model unspecified) — [APKMirror MacroDroid 5.59.2](https://www.apkmirror.com/?p=11586678); [Yahoo/Android Police on Tasker AI](https://tech.yahoo.com/articles/taskers-ai-helper-just-made-203236595.html)

### Inferences
- A Play-distributed third-party app that drives other apps' UIs autonomously is now policy-noncompliant (Accessibility) and technically excluded (Computer Control is OEM/privileged). The only compliant cross-app path for an indie is to **be a target**: publish AppFunctions and wait for Gemini GA, or accept sideload/F-Droid distribution with Shizuku — which the Sept 2026 developer-verification "Advanced Flow" makes harder for mainstream users.
- Fillable gaps: (1) AppFunctions tooling — schema linting, a local test harness/"fake agent" that calls your functions (today testing is via `adb shell cmd app_function`), and a cross-app AppFunctions registry/explorer; (2) a first-party-data MCP/AppFunctions bridge using normal permissions (see KQ1); (3) a Shizuku-based agent toolkit with an explicit "non-Play" distribution story.

### Gaps
- `EXECUTE_APP_FUNCTIONS` protection level (whether a third-party agent app can hold it) is not stated in Google docs I fetched.
- Final shipping status/name of the QPR2 "Agent control of other apps" page unconfirmed.
- No official Google statement on restricting on-device ADB.
- Android Auto limitations for AI agents and Notification Listener policy specifics were not researched.

---

## KQ4. Agent SDKs and frameworks for mobile; what developers find painful

### Takeaway
Server-side agent SDKs (Claude Agent SDK: Python/TypeScript, runs the Claude Code binary; no mobile target) and client-side chat SDKs (Vercel AI SDK with Expo polyfills) are mature only for the "phone as thin client to a backend" pattern. Fully on-device agent stacks exist (llama.rn 1.1k stars, Cactus 6.1k, react-native-executorch 1.8k, LiteRT-LM/ADK Kotlin GA, Apple Foundation Models) but are fragmented, New-Architecture-only, memory-constrained and inconsistently support tool calling. The dominant documented pain is secret handling: a 2026 study found 282 of 444 AI iOS apps leaking LLM credentials.

### Cited Findings

**Exists and works (backend-first)**
- Claude Agent SDK is "programmable in Python and TypeScript", "a library that runs the Claude Code binary"; other languages must shell out to the CLI (`-p --output-format json`); Anthropic "does not allow third party developers to offer claude.ai login or rate limits for their products" — API keys only. No mention of mobile/browser targets — [Claude Agent SDK overview](https://code.claude.com/docs/en/agent-sdk/overview)
- Vercel AI SDK Expo guide: requires Expo 52+; must pass `expo/fetch` as the `fetch` option for streaming; mobile may throw "Property `structuredClone` doesn't exist" and needs `@ungap/structured-clone` + `@stardazed/streams-text-encoding` polyfills for `structuredClone`, `TextEncoderStream`, `TextDecoderStream`; deployed Expo API routes may buffer streams — workaround is hosting the endpoint as a separate Vercel Function — [AI SDK: Expo getting started](https://ai-sdk.dev/docs/getting-started/expo)
- React Native's native fetch does not support streaming; community wrappers return the full response instead — [react-native-vercel-ai (sourcepulse)](https://www.sourcepulse.org/projects/1838423); "Invalid hook call useChat in Expo" thread — [Vercel Community](https://community.vercel.com/t/invalid-hook-call-usechat-in-react-native-expo/9268)
- Firebase AI Logic Flutter plugin (`firebase_ai`) needs no backend but supports only Gemini/Imagen models; Firebase AI Logic "server prompt templates" (Jan 2026) move "sensitive prompt logic from the client" to Firebase servers — [ITNEXT: Firebase AI Logic vs Genkit](https://itnext.io/choosing-the-right-ai-framework-for-flutter-firebase-ai-logic-vs-genkit-68888721efa7); [Play Monthly Jan 2026](https://developer.android.com/newsletter/play-monthly/2026/content/january)
- Genkit Dart announced early 2026 for multi-step tool-calling agents in Dart/Flutter — [theflutterk.it blog](https://theflutterk.it.com/blog/flutter-ai-genkit-vs-firebase-ai-vs-openai)

**Exists but immature (on-device)**
- llama.rn (mybigday): 1.1k stars, 126 forks; v0.10+ requires RN New Architecture; iOS Metal (Apple7+ GPU, no simulator Metal), Android arm64-v8a/x86_64 only, OpenCL on Adreno 700+, experimental Hexagon NPU on SM8450+; universal tool calling via Jinja templates with JSON fallback; GBNF/JSON-schema structured output; multimodal via mmproj (needs `ctx_shift: false`, no remote media URLs, session save excludes multimodal state); CPU-only on Apple Silicon hits SIGILL; many TTS models unreliable — [GitHub: mybigday/llama.rn](https://github.com/mybigday/llama.rn)
- Cactus (cactus-compute): 6.1k stars, 515 forks; Swift/Kotlin/Flutter/RN/Python/Rust bindings; tool calling; "Cactus Hybrid" cloud fallback by confidence threshold (needs API key); models Liquid/Gemma/Whisper/Parakeet/Qwen + 26M-param "Needle" tool-calling model; CQ2 quantization drops GSM8K from 73.67 to 0.40; benchmarks Apple-only; license not named on page — [GitHub: cactus-compute/cactus](https://github.com/cactus-compute/cactus)
- react-native-executorch (Software Mansion): ~1.8k stars; iOS 17+/Android 13+; RN 0.83+ or Expo SDK 55+ dev builds; New Architecture required; no Expo Go; XNNPACK/Core ML/MLX/Vulkan; LLM example LFM2.5-1.2B; tool calling not mentioned — [GitHub: software-mansion/react-native-executorch](https://github.com/software-mansion/react-native-executorch)
- Memory: react-native-executorch docs warn "Lower-end devices might not be able to fit LLMs into memory"; a ~4GB model crashed in an Android app where 2GB worked (PyTorch forums) — [react-native-executorch memory management](https://www.mintlify.com/software-mansion/react-native-executorch/advanced/memory-management); [discuss.pytorch.org](https://discuss.pytorch.org/t/android-large-model-4gb-on-android-app-is-crashing/223543)
- Vercel AI SDK v5 tool-call issues cited by third parties: #7857 "Tool calling parts order is wrong", #7258 "Unsupported tool part state: input-available" (unverified) — [skills.sh ai-sdk-expert](https://skills.sh/cin12211/orca-q/ai-sdk-expert)

**Secrets / cost control (the documented pain)**
- Wake Forest study: of 444 AI-powered iOS apps, 282 exposed LLM credentials; 54 sent static provider keys in HTTP headers/query strings, often alongside system prompts; only ~28% fixed post-disclosure; naive proxying is bypassable, layered defenses (payload encryption, WebSocket) drove bypass to near zero; researchers say hiding keys server-side is insufficient without auth/authz — [Help Net Security 2026-06-22](https://www.helpnetsecurity.com/2026/06/22/llm-api-credential-leakage-ios-apps/); [Cyber Security News 2026-08-28](https://cybersecuritynews.com/ai-ios-apps-leaking-llm-credentials/); [Approov analysis](https://approov.io/blog/mitigating-llm-credential-leaks-in-ios-apps-key-insights-from-a-study)
- GitGuardian (secondary): LLM credential leaks up 81% YoY to 1.2M — [enterno.io](https://enterno.io/en/s/how-to-secure-ai-api-keys)
- Apple's iOS-27 PCC model: "no account setup, authentication, or API key, and no token cost to the developer", user daily cap — removes the secret problem entirely for eligible small developers — [WWDC26 382](https://developer.apple.com/videos/play/wwdc2026/382/)

### Inferences
- No vendor offers a mobile-native "agent runtime" (loop + tools + permissions + sessions) that runs on the phone; Claude Agent SDK, OpenAI Agents SDK and Managed Agents assume a server/sandbox. Omnara's self-description — a hosted agent loop with per-tool approve/ask/block that mobile clients consume — is the architecture indies currently reach for.
- Fillable gaps: (1) an App-Attest/Play-Integrity-gated LLM relay with per-user budgets and spend caps packaged for indies (the study shows this is the single most common failure); (2) a unified on-device tool-calling layer that abstracts llama.rn/ExecuTorch/LiteRT-LM/Foundation Models with capability detection and memory-aware model selection; (3) an Expo/RN streaming + tool-call transport that works without hand-rolled polyfills.

### Gaps
- No OpenAI Agents SDK mobile documentation was found or checked.
- No Reddit/HN primary developer complaints retrieved (search returned forums/docs only).
- Flutter AI Toolkit and Google AI Edge Gallery details not independently verified.

---

## KQ5. Remote-agent-from-phone tooling (Claude Code, Codex, Happy, Omnara, channels, terminals)

### Takeaway
Driving a coding agent from a phone is now mainstream and officially supported: Claude Code lives in the Claude app's Code tab (cloud sessions, Remote Control, Dispatch) with push notifications for approvals, and Codex entered the ChatGPT app on 14 May 2026. Open-source Happy (24.1k stars) and Omnara (2.9k) add E2E encryption, multiplayer and model-agnostic approvals. Remaining holes are voice input, phone-native diff review, cost caps, and anything that works without a laptop or a GitHub-hosted repo.

### Cited Findings

**Exists and works**
- Claude app (iOS/Android) is the client for cloud sessions, Remote Control (local machine) and Dispatch (Desktop app); requires a claude.ai account (no Console API key / Bedrock); `/mobile` prints a QR; attachments from phone reach the local session (photos saved under `~/.claude/uploads/`); permission modes from the app: cloud = Accept edits/Plan/Auto, Remote Control = Manual/Accept edits/Plan/Auto, **no Bypass permissions**; terminal-only commands include `/plugin`, `/resume`; Dispatch is Pro/Max only — [Claude Code docs: mobile](https://code.claude.com/docs/en/mobile)
- Remote Control: Pro/Max/Team/Enterprise, Team/Enterprise owners must enable a toggle; `claude remote-control`, `/rc`; `--spawn worktree`, `--capacity` (default 32), `--permission-mode`, `--chrome`; TLS via Anthropic API with short-lived scoped credentials; optional Trusted Devices (passkey step-up); push notifications with two `/config` toggles — "Push when Claude decides" and "Push when actions required" (permission prompts/questions), no per-event config; pushes suppressed while typing in the terminal or via `CLAUDE_CLIENT_PRESENCE_FILE`; permission prompts and `AskUserQuestion` stay open until answered, other forwarded dialogs expire after 5 min (`dialogExpiry`); `/mcp` from mobile returns text only and connector OAuth must be completed from a terminal on the host; shell `!` prefix doesn't work from mobile; sessions resumable ~4 hours after server stop — [Claude Code docs: Remote Control](https://code.claude.com/docs/en/remote-control)
- Channels (research preview): Telegram, Discord, iMessage plugins (Bun) push messages into a running local session; pairing-code allowlists; channels declaring the permission-relay capability can forward permission prompts so you approve/deny remotely; `-p` non-interactive mode disables multiple-choice and plan approval; Team/Enterprise must enable `channelsEnabled` — [Claude Code docs: Channels](https://code.claude.com/docs/en/channels)
- Codex in the ChatGPT iOS/Android app (preview, 14 May 2026, all plans incl. Free/Go in supported regions): phone acts as remote control for Codex on the dev machine; start tasks, read terminal output, inspect diffs, approve risky commands, switch model, notifications; later extended to Codex for Windows — [Axios 2026-05-14](https://axios.com/2026/05/14/openai-brings-codex-to-your-phone); [ainauten setup guide](https://news.ainauten.com/markdown/codex-goes-mobile-how-to-set-it-up-on-ios-and-android)
- Happy (slopus/happy, MIT): 24.1k stars, 2.1k forks, 2,565 commits; `happy claude` / `happy codex` / Grok; Expo mobile+web client, CLI wrapper, encrypted relay server; E2E encryption; multiplayer sessions; free, reuses existing subscriptions; apps on App Store and Play — [GitHub: slopus/happy](https://github.com/slopus/happy)
- Omnara (omnara-ai/omnara, Apache-2.0; YC S25): 2.9k stars; REST API + Postgres event log + stateless workers + `omnarad` outbound daemon; per-tool policy run/ask/block with agent waiting on approval; Slack/Discord/GitHub integrations; Claude Code/Codex/Cursor connect as MCP clients; cloud free with BYO keys/machines, else pay-as-you-go; page compares to Claude Managed Agents ($0.08/active session-hour + tokens) — [GitHub: omnara-ai/omnara](https://github.com/omnara-ai/omnara); marketing claims one-tap push approvals and mobile diff view — [Product Hunt](https://www.producthunt.com/products/omnara)
- Hook-based push services: Pushary ($9.99/mo) pushes on finish/permission prompt; claude-remote-approver (free) forwards permission requests to phone with CLI fallback on timeout — [Pushary](https://pushary.com/claude-code-notifications); [GitHub: yuuichieguchi/claude-remote-approver](https://github.com/yuuichieguchi/claude-remote-approver)

**Exists but immature / missing**
- Official docs list no voice input for Claude Code mobile; Happy's README does not mention push, voice or diff review; Omnara's README does not mention push or voice (see repo fetches above).
- Push delivery can be delayed by iOS Focus modes / notification summaries and Android battery optimization — [Claude Code docs: Remote Control](https://code.claude.com/docs/en/remote-control)
- Channels are allowlist-only (Anthropic-maintained plugin list) during preview; flags hidden from `--help` — [Claude Code docs: Channels](https://code.claude.com/docs/en/channels)

### Inferences
- The Anthropic and OpenAI first-party mobile clients have absorbed the "see output, approve, steer" layer; indie value has moved to (a) model-agnostic/multi-harness control planes (Happy, Omnara), (b) per-user cost caps and spend dashboards (not found in any first-party mobile client), (c) voice-first steering, (d) rich on-phone diff review with inline comments, and (e) persistent "no laptop needed" execution for non-GitHub projects.
- Cursor background agents from phone: no sources found in this pass; treat as a gap.

### Gaps
- Cursor, Conductor, OpenClaw mobile clients and SSH/mosh terminal apps (Termius, Blink) were not covered by retrieved sources.
- Codex mobile plan/feature details rely on press coverage, not an OpenAI doc.
- No data on Happy/Omnara MAU or App Store ratings.

---

## KQ6. Testing, observability and evaluation of mobile agents

### Takeaway
Research benchmarks are strong and saturating (AndroidWorld top scores >90%, MobileWorld successor tops out at 51.7% with GPT-5), and QA tooling (Maestro MCP, mobile-mcp, device farms) lets coding agents operate devices — but there is no product-grade observability/eval harness for *shipping* mobile agents (trace capture of on-device tool calls, replay, regression suites on real devices), apart from Apple's new Instruments/Evaluations framework for Foundation Models.

### Cited Findings
- AndroidWorld (ICLR 2025): launch baseline 30.6% task success — [ICLR 2025 poster](https://iclr.cc/virtual/2025/poster/28677); aggregated 2026 leaderboards show 97.4% pass@1 for several entries (mixed self-reported) — [benchmarklist AndroidWorld](https://benchmarklist.com/benchmarks/androidworld/); BenchLM snapshots: Qwen3.7 Plus 81.0% (29 Jul 2026), Qwen3.8-Omni-Flash 87.1% (22 Sep 2026) — [BenchLM AndroidWorld](https://benchlm.ai/benchmarks/androidworld)
- MobileWorld (ACL 2026 long paper, arXiv 2512.19432): 201 tasks across 20 apps, adds agent–user interaction, MCP tool integration and longer tasks; best agentic framework (GPT-5 + UI-Ins-7B) 51.7%; best end-to-end GUI model (Doubao-1.5-UI-TARS) 20.9%; avg 27.8 steps vs 14.3 on AndroidWorld; 62.2% cross-app vs 9.5% — [arXiv 2512.19432](https://arxiv.org/html/2512.19432v3); [ACL Anthology 2026.acl-long.278](https://aclanthology.org/2026.acl-long.278/)
- Maestro MCP in CLI: `list_devices`, `inspect_screen`, `run` (YAML flows), `take_screenshot`, Maestro Cloud tools; agents "self-correct until it passes" — [Maestro MCP](https://maestro.dev/mcp); [TestGuild: Agentic AI for Mobile QA](https://testguild.com/agentic-ai-mobile-testing-maestro/); teams build internal device farms due to Maestro Cloud limits — [Avenue case study](https://avenuetech.substack.com/p/case-avenue-execucao-de-testes-automatizados)
- mobile-mcp exposes device logs, crash listing and screen recording; Mobile Next Cloud offers remote physical devices — [GitHub: mobile-next/mobile-mcp](https://github.com/mobile-next/mobile-mcp)
- Apple (WWDC26): Instruments shows every prompt, tool call and model output at runtime; an Evaluations framework with an `evaluates` Swift Testing trait and model judges for "evaluation-driven development"; `fm` CLI for scripting — [WWDC26 382](https://developer.apple.com/videos/play/wwdc2026/382/)
- Android AppFunctions testing is via `adb shell cmd app_function list-app-functions` — [Android Developers: AppFunctions](https://developer.android.com/ai/appfunctions)

### Inferences
- Evaluation of GUI agents is well served academically; evaluation of *developer-built* in-app agents (tool-call correctness, latency, cost per task on real devices across OEM/RAM tiers) has no Android-side equivalent of Apple's Instruments+Evaluations — a fillable gap (OpenTelemetry-style tracing for on-device tool calls, device-farm matrix for Gemini Nano/LiteRT-LM availability).

### Gaps
- No sources on device farms specifically for agent evaluation (Firebase Test Lab/AWS Device Farm agent use) were retrieved.
- Mobile-agent-bench variants beyond AndroidWorld/MobileWorld/GhostEI/MIRAGE not surveyed.

---

## KQ7. Security and trust layer: permissions, confirmation UX, undo, spend limits, prompt injection

### Takeaway
Platforms are converging on OS-mediated consent for agents (Android Computer Control system dialog + handover for confirmations; Apple schemas with automatic confirmation/authentication; Claude Code permission prompts forwarded to phone), while research shows GUI agents remain systematically vulnerable to environmental injection via overlays, spoofed notifications and user-generated content (23–30% attack success in MIRAGE). Undo, per-task spend caps on mobile, and injection defenses for third-party agents are essentially absent.

### Cited Findings
- Android Computer Control: system consent dialog on session request; assistant hands control back for "transaction confirmation or required acknowledgements"; user can take over manually — [Android Computer Control](https://developer.android.com/ai/computer-control)
- Play Accessibility policy forbids changing settings without permission, working around platform security/privacy controls, or deceptive UI changes; requires disclosure/consent for non-assistive uses — [Google Play policy](https://support.google.com/googleplay/android-developer/answer/16558241)
- Apple App Intents schemas provide "confirmation and authentication handling" automatically; macOS 27 adds kernel-level file-access approvals for Xcode agents — [WWDC26 382](https://developer.apple.com/videos/play/wwdc2026/382/)
- Apple guideline 5.1.2(i): disclose and get explicit permission before sharing personal data "with third-party AI" — [App Store Review Guidelines](https://developer.apple.com/app-store/review/guidelines/)
- Claude Code: Bypass permissions cannot be selected from the mobile app; permission prompts stay open until answered; channel permission relay means "anyone who can reply through the channel can approve or deny tool use" — [Claude Code mobile](https://code.claude.com/docs/en/mobile); [Channels](https://code.claude.com/docs/en/channels)
- GhostEI-Bench (arXiv 2510.20333, v3 March 2026): environmental injection via deceptive overlays / spoofed notifications / popup SMS in live Android emulators; agents show "pronounced vulnerability" and "systematically fail to perceive and reason about manipulated UIs"; judge-LLM over trajectories; no defense proposed — [arXiv 2510.20333](https://arxiv.org/abs/2510.20333)
- MIRAGE (May 2026): 1,111 samples, 10 apps, 11 attack intents, injection via user-generated-content regions in screenshots; all five evaluated VLM agents vulnerable at 23–30% success — [chatpaper MIRAGE](https://chatpaper.com/de/paper/287358); [emergentmind 2605.28116](https://www.emergentmind.com/papers/2605.28116)
- android-remote-control-mcp's own "Privacy Mode" detects names at 0.8% — "best-effort mitigation, not a guarantee" — [GitHub repo](https://github.com/danielealbano/android-remote-control-mcp)
- Credential exposure at scale (282/444 apps) and recommendation of backend authz + layered proxy defenses — [Help Net Security](https://www.helpnetsecurity.com/2026/06/22/llm-api-credential-leakage-ios-apps/)
- Omnara is the only surveyed tool with a declared per-tool run/ask/block policy model — [GitHub: omnara-ai/omnara](https://github.com/omnara-ai/omnara)

### Inferences
- Missing for indie builders: a reusable "agent permission + confirmation + undo" SDK for in-app agents (scoped capabilities, dry-run previews, reversible action log), a per-user/per-task spend-cap component with mobile-visible budgets, and an injection filter for notification/screen text fed to models. None of these exists as a library in the sources found.

### Gaps
- No sources found on undo/rollback mechanisms for mobile agent actions.
- No sources on spend limits in first-party mobile agent clients.
- GhostEI-Bench numeric results not extracted (abstract only).

---

## KQ8. Distribution and economics (fees, BYOK, local-only moat, EU DMA, verification/sideloading)

### Takeaway
Fee pressure is easing in two places (US external-payment links currently uncommissioned pending the Supreme Court's review of Epic v. Apple; EU DMA tiers with a 5% core technology commission for alternative distribution from 1 Oct 2026 per one report) but BYOK remains a 3.1.1 risk on iOS, Apple's free PCC model tier is reserved for <2M-download Small Business Program developers, and Android's developer-verification rollout (30 Sept 2026, 4 countries) raises the cost of sideload-only distribution for Shizuku/Accessibility-based agents.

### Cited Findings
- US: Apple has not charged commission on external-link payments for nearly a year; Ninth Circuit (Dec 2025) upheld the contempt finding but remanded to set a reasonable rate; Apple petitioned SCOTUS May 2026; Justice Kagan denied a stay; as of 16 Aug 2026 the Court agreed to hear a limited part, merits pending — [MacRumors 2026-06-11](https://macrumors.com/2026/06/11/apple-fights-back-against-epic/); [TechSpot](https://www.techspot.com/news/112956-apple-fight-epic-over-app-store-fees-reaches.html); [TNW 2026-05-06](https://thenextweb.com/news/supreme-court-apple-epic-contempt-stay-denial)
- EU: one report says from 1 Oct 2026 Apple phases out acquisition/store-services fees in favour of a 5% core technology commission for apps from the web or third-party marketplaces, 26% for App Store apps using Apple payments, 20% with independent processors, 15% for link-outs; another describes a 12–20% CTC from 1 Jan 2026 — sources conflict — [wnhub.io](https://wnhub.io/news/stores-and-publishing/item-51820); [Funnelfox: App Store fees 2026](https://blog.funnelfox.com/apple-app-store-fees-2026-eu-dma/)
- Guideline 3.1.3 exemptions (reader, multiplatform, enterprise, person-to-person, goods outside app, free stand-alone companions, ad management) and the US-storefront carve-out for steering — [App Store Review Guidelines](https://developer.apple.com/app-store/review/guidelines/)
- BYOK: 3.1.1 rejection text "the app uses API keys to unlock or enable functionality" (Sept 2024, unresolved) — [Apple Dev Forums 763884](https://developer.apple.com/forums/thread/763884); 3.1.3(b) vs 3.1.1 tension debated without resolution — [Apple Dev Forums 740710](https://developer.apple.com/forums/thread/740710)
- Apple PCC server model: no token cost to developer, limited to Small Business Program developers with <2M downloads, user daily cap raisable with iCloud+ — [WWDC26 382](https://developer.apple.com/videos/play/wwdc2026/382/)
- Apple reportedly weighs IAP-bypass risk as a reason to restrict agent apps — [PYMNTS](https://www.pymnts.com/apple/2026/apple-prepares-app-store-for-autonomous-ai-agents/)
- App submissions surged to 235,800 in Q1 2026 (+84% YoY, Sensor Tower) — [PYMNTS vibe-coding crackdown](https://www.pymnts.com/apple/2026/apple-cracks-down-on-vibe-coding-services-in-app-store/)
- Android developer verification: 30 Sept 2026 in BR/ID/SG/TH, global 2027; unverified sideloads need "Advanced Flow"; ADB installs unaffected; EMM-installed apps exempt — [Android Authority](https://www.androidauthority.com/p-3679204/); [Bayton FAQ](https://bayton.org/android/android-enterprise-faq/google-play-developer-verification-enterprise/)
- Omnara cloud pricing (no platform fee, BYO keys) vs Claude Managed Agents ($0.08/active session-hour + tokens) — [GitHub: omnara-ai/omnara](https://github.com/omnara-ai/omnara)

### Inferences
- The clean indie monetization patterns on iOS today are: paid/subscription app whose AI runs on-device (Foundation Models/Core AI/llama.rn — zero marginal cost, no key to leak, no 3.1.1 ambiguity) or, from iOS 27, Apple's free PCC tier for small developers; BYOK remains legally grey and should be positioned as "connect your account" not as a feature unlock.
- On Android, Play-compliant AI features (ML Kit GenAI, AppFunctions-as-target) are low-risk; agent apps that need Accessibility/Shizuku should plan for GitHub/F-Droid/Obtainium distribution and accept the Sept-2026+ verification friction.

### Gaps
- EU fee figures conflict across sources; no Apple primary document fetched.
- No data on Play Store fee treatment of AI subscriptions specifically.
- No sources found quantifying BYOK app approvals in 2025–2026 beyond the single forum thread.
- TestFlight constraints for AI apps not researched.

---

## Cross-cutting opportunity map (synthesis of the above; each item traces to cited findings)

**Fillable now by an indie/small team (evidence of demand + no incumbent):**
1. Android first-party-data MCP/AppFunctions bridge using normal runtime permissions (contacts, calendar, SMS, Health Connect, NotificationListener) with OAuth 2.1 + Streamable HTTP and a hosted relay for claude.ai/ChatGPT connectors — nothing beyond ~700-star Accessibility-based projects exists (KQ1, KQ3).
2. AppFunctions developer tooling: schema linter, local "fake agent" harness, cross-app function explorer — Google testing today is `adb shell cmd app_function` and Gemini is private preview (KQ3, KQ6).
3. Indie-grade LLM relay with App Attest/Play Integrity, per-user budgets, spend caps and leak scanning — 282/444 apps leak keys (KQ4, KQ7).
4. On-phone agent control plane features the first-party clients lack: voice steering, inline diff comments, cost dashboards, multi-harness (Claude Code + Codex + Cursor) (KQ5).
5. Android on-device agent observability (tracing of tool calls, device-matrix availability for Gemini Nano/LiteRT-LM) — Apple ships Instruments/Evaluations, Android has nothing comparable (KQ6).
6. iOS App Intents "tool bridge" packaging: expose app actions to Siri/Shortcuts/Visual Intelligence and to the Shortcuts "Use Model" action with schema adoption, plus the iOS-27 `LanguageModel` protocol — Apple's own agent surface, zero policy risk (KQ2).

**Walls not fillable by indies (route around, don't build into):**
- Cross-app autonomous GUI control on Play-distributed Android (Accessibility policy since 28 Jan 2026; Computer Control is OEM-privileged) and on iOS (no API) (KQ2, KQ3).
- Code-generating/executing agent apps on iOS (2.5.2; Replit/Vibecode/Anything enforcement, March 2026) (KQ2).
- BYOK as a feature unlock on iOS (3.1.1) (KQ8).
- Claude Agent SDK on-device (API-key only, runs Claude Code binary; claude.ai login not permitted for third parties) (KQ4).
