# Competitor App Teardown Method and Legal and App-Store Limits (incl. REA), as of 2026-10-12

> Research notes for a solo founder (Australia-based) who wants to study successful competitor mobile apps and build a better, differentiated version. **This is not legal advice.** Items marked **[LAWYER]** should be confirmed by an Australian IP lawyer, plus a US lawyer if the founder targets US users or relies on US law. Research date: 2026-10-12.
>
> **Method note:** The research environment's proxy blocked direct fetching of these sites: legislation.gov.au, AustLII (www/www6), law.cornell.edu, apple.com/legal, support.google.com, play.google.com, alrc.gov.au, mas.owasp.org and screensdesign.com. Findings attributed to those sources come from search-engine result summaries, not full-page reads, and are flagged "(search-summary)". Two kinds of sources were read in full: the REA repo files (README plus docs, via raw.githubusercontent.com), and developer.apple.com and developer.android.com pages.

---

## 1. REA (github.com/morluto/rea): what it analyzes, setup, disclaimer, and fit for legitimate competitive research

### Takeaway
REA ("Reverse Engineer Anything") is an MIT-licensed MCP server and CLI. It lets an AI coding agent (Claude Code, Codex, Cursor, Gemini CLI and others) statically and dynamically inspect binaries, Android APKs and devices, JS/Electron apps, websites and saved HAR/mitmproxy captures. Its own pitch is to "build a version" of a feature you see in another app. For a founder, its safe uses are narrow:
- inventorying which SDKs and frameworks a competitor's Android app ships (RevenueCat, Superwall, Firebase, React Native or Flutter, and so on)
- reading manifest permissions, locales and version facts
- inspecting your *own* captured traffic or a competitor's public website

Its decompile-and-reconstruct workflow is the part that creates legal and app-store risk. REA documents no way to decrypt FairPlay-protected App Store binaries.

### Cited Findings

**What REA is and how it pitches itself**
- REA is "One MCP for reverse engineering across binaries, applications, and runtime behavior". Its tagline is "See a feature you like. Understand how it works, down to the binary level." — [REA README](https://github.com/morluto/rea/blob/main/README.md)
- The README frames the use case as copying features. Verbatim: "See a feature in an app that you want in your own product? Ask your agent to investigate it with REA. It can inspect the app without its source code, explain how the feature works, show the evidence, and build a version for your project." — [REA README](https://github.com/morluto/rea/blob/main/README.md)
- Its example prompt is "Understand how search works in the Notes app, show me the evidence, and build a similar feature for my project." — [REA README](https://github.com/morluto/rea/blob/main/README.md)
- "Analysis runs locally, and results include the evidence and limitations behind each conclusion." On uploads, the README says: "REA analyzes targets locally. Your agent receives the tool results, and its model provider has its own data policy." This means decompiled competitor code is sent to whichever LLM provider the agent uses. — [REA README](https://github.com/morluto/rea/blob/main/README.md)

**Targets and their requirements** (from the README table, verbatim in substance)

| Target | What REA returns | Requirements |
| --- | --- | --- |
| Native binaries | Pseudocode, assembly, strings, symbols, calls and references | Hopper, Ghidra or IDA |
| JavaScript / Electron | Modules, imports, source maps, routes, IPC, native add-ons | Node.js and npm only |
| Websites | Page structure, scripts, network observations, screenshots | A Chrome-family browser |
| Saved network captures | Requests, responses, exposed payloads, source locations | HAR files; mitmdump on Linux for native mitmproxy captures |
| .NET assemblies | Static analysis only | — |
| Android APKs | Manifest declarations, classes, decompiled methods, references | Headless JADX and a full JDK |
| Android devices | Devices, packages, processes, logs, dumps, screen captures, APK/file transfers | Caller-supplied adb |
| JEB projects | — | A JEB client |
| Android resources | Decoded manifest, string tables, locales, version facts | Caller-supplied Apktool |
| Firmware | — | Binwalk or Unblob |
| Packages and resources | Includes "Apple bundle anatomy" | — |
| Process behavior | — | Linux or macOS PTY |
| WASM, EVM bytecode, recorded Linux crashes, offline ELF | — | Various caller-supplied tools |

Source: [REA README](https://github.com/morluto/rea/blob/main/README.md)

**Setup**
- Runtime: Node.js 22.x (>=22.19), 24.x (>=24.11) or 26+, plus npm.
- Quick start is `npx rea-agents setup`, which registers the MCP server and workflow instructions with backups. Alternatively, `npm install --global rea-agents` and then `rea --help`.
- Deep native analysis needs Hopper, Ghidra or IDA. Setup "can optionally install Hopper with approval". Static JS and .NET analysis need no native engine.
- The README says "REA changes quickly", so features may differ from these notes. **[possibly outdated]**

Source: [REA README](https://github.com/morluto/rea/blob/main/README.md)

**Android APK analysis**
- Requires "a full JDK 17 or newer" and "jadx-headless-mcp 0.7.1", set via `REA_JADX_MCP_JAR`.
- "REA does not install Java, an Android SDK, JADX, a device service or an emulator."
- The family is "present on repository main and in npm 4.1.0".
- The docs say the result "does not establish complete semantics or a byte-identical reconstruction".

Source: [REA Android analysis doc](https://github.com/morluto/rea/blob/main/docs/android-analysis.md)

**Android resources**
- Apktool 2.7.0+ decodes "resource tables and the binary manifest". The docs call this "the static triad for Android targets": JADX sources, JEB decompilation and Apktool resources. — [REA Apktool doc](https://github.com/morluto/rea/blob/main/docs/apktool-resource-analysis.md)

**ADB device analysis**
- Example commands include pulling an installed app's complete split-APK set from a device (`rea pull-adb-package emulator-5554 com.whatsapp ...`), then statically inspecting it.
- It can also read logcat, list processes, capture screens, and list app data directories.
- Some operations are "device-mutating": push files (the docs' example pushes `frida-server`), install, uninstall, start and stop apps.
- "UI interaction (`input`, `am`, `monkey`) is deliberately not exposed."
- Frida instrumentation is described as a separate lane (#1359) "behind explicit mutation-authority contracts".
- It was verified against an Android 14 (API 34) x86_64 emulator.

Source: [REA ADB doc](https://github.com/morluto/rea/blob/main/docs/adb-device-analysis.md)

**Network captures**
- HAR and mitmproxy inspection is "an offline operation: recorded URLs are never fetched, and no browser or proxy listener is started." REA analyzes captures you already made; it does not intercept a phone's traffic itself.
- Native mitmproxy decoding needs mitmdump 12.2.3 on Linux.
- Authentication headers and cookies are excluded structurally, and users can mark extra values as sensitive for redaction.
- "Historical evidence does not prove runtime attribution, execution or deployment authenticity."

Source: [REA web network captures doc](https://github.com/morluto/rea/blob/main/docs/web-network-captures.md)

**Website observation**
- Network observations keep method, status, MIME type, size and initiator, and "Cookies and authorization headers are never retained." — [REA browser observation doc](https://github.com/morluto/rea/blob/main/docs/browser-observation.md)

**Apple (iOS/macOS) analysis**
- REA can "project" an inventory for an "IPA, macOS `.app` directory, ZIP, or DMG". The projection is "execution-free". It reports paths, content hashes, bundle anatomy, "runtime-family hints" and bridge hypotheses.
- Framework hints match path segments such as `React.framework`, `ReactNative.framework`, `hermes.framework`, `Flutter.framework` and `UnityFramework.framework`.
- "It does not parse plist or CMS semantics or claim observed runtime calls." Plists are read with a separate `inspect_plist` tool.
- A grep of the Apple doc, README, Android, ADB, network and browser docs found **no mention of FairPlay, encryption or decryption**. REA does not document any iOS decryption capability.

Source: [REA Apple application analysis doc](https://github.com/morluto/rea/blob/main/docs/apple-application-analysis.md)

**REA's own disclaimer**
- Verbatim: "REA provides tools for lawful reverse-engineering research, analysis, and reconstruction. You are responsible for obtaining any required authorization and complying with applicable laws. The project does not endorse illegal or unauthorized use." — [REA README, Disclaimer](https://github.com/morluto/rea/blob/main/README.md)
- The README also warns: "We have not issued or endorsed any cryptocurrency or token. Tokens using the REA name are not affiliated with the project." — [REA README](https://github.com/morluto/rea/blob/main/README.md)

**Showcases**
- The README's showcases include an exact reconstruction: a DX-Ball function whose reconstruction "passes 3,205 original-x86 cases and reproduces all 63 compiled function bytes".
- They also include tracing Notion's Electron clipboard bridge. — [REA README](https://github.com/morluto/rea/blob/main/README.md)

**Repository facts** (volatile)
- MIT license.
- The README says "90,000 GitHub stars". A WebFetch of the GitHub page on 2026-10-12 reported about 104k stars and 22.9k forks.
- Top-level folders include `src`, `docs`, `bridge`, `third_party` and `website`.

Sources: [REA repo](https://github.com/morluto/rea), [REA README](https://github.com/morluto/rea/blob/main/README.md)

**iOS App Store encryption (FairPlay)** (secondary sources only)
- Apple encrypts App Store app binaries with FairPlay DRM. Security-testing literature describes decryption as requiring a jailbroken device, so it is not available through ordinary use of a purchased app.

Sources: [CREST "Modern iOS Pentesting: No Jailbreak Needed" slides](https://www.crest-approved.org/wp-content/uploads/2025/02/Modern-iOS-Pentesting_-No-Jailbreak-Needed-Slides-Noah-Farmer.pdf); [HackTricks iOS pentesting mirror](https://git.disroot.org/0x22bb/hacktricks/src/commit/f827912d99d5417d536f67842dfa59057c2325aa/ios-pentesting) (search-summary; OWASP MASTG itself could not be fetched)

**Android HTTPS interception limits**
- Android's own docs say: "By default, secure connections ... from all apps trust the pre-installed system CAs, and apps targeting Android 6.0 (API level 23) and lower also trust the user-added CA store by default." Apps targeting API 24+ trust only system CAs by default.
- Debug-only trust anchors are "completely ignored" when `android:debuggable` is false, and "app stores do not accept apps that are marked debuggable".
- Some apps also use certificate pinning.

Source: [Android Developers – Network security configuration](https://developer.android.com/privacy-and-security/security-config)

### Inferences

**Fit-for-purpose map for REA**

GREEN (low risk; facts, not expression). This applies to apps you lawfully installed:
- **SDK/framework inventory.** Read a competitor's Android manifest and class/package list (Apktool/JADX) or iOS bundle `Frameworks/` paths to see which third-party SDKs it ships. Examples: billing/paywall SDKs (RevenueCat, Superwall, Adapty), analytics (Firebase, Amplitude, Mixpanel), attribution (AppsFlyer, Adjust) and cross-platform runtimes (React Native/Hermes, Flutter, Unity). These are facts about the competitor's stack, not copyrightable expression. In practice you need only the namespace or framework names, never method bodies.
- **Manifest facts.** Permissions, declared locales, min/target SDK, deep-link schemes, and whether it uses push notifications, widgets or background services.
- **Your own traffic.** Running REA's HAR/browser observation on your *own* prototype, or on a competitor's **public website or web-to-app onboarding funnel** in a normal browser, to see which third-party endpoints load. Examples: analytics, a Stripe or paywall vendor, or an AI provider's domain if called from the client.

RED (out of scope for this methodology; do not do it):
- **Breaking into a competitor app's encrypted traffic or binary.** This includes defeating TLS trust or pinning, decrypting App Store binaries, and instrumenting or repackaging a competitor's release build. The Android defaults above mean a competitor's HTTPS traffic is not observable through ordinary use. Getting around that means defeating a protection the developer deliberately put in place, which:
  - breaches the store EULA and the developer's terms (Section 3)
  - may engage anti-circumvention law (DMCA s1201; Australian s116AN). Whether TLS or pinning counts as a "technological protection measure" protecting a copyright work is unresolved in my sources. **[LAWYER]**
  - is unnecessary for the founder's actual questions.
- **Decompiling to copy.** Reading or recreating a competitor's method bodies, UI layouts, strings, illustrations, sounds or animations for your own app. This is the "build a version" workflow REA advertises. For a commercial competitor it creates copyright risk in literal or non-literal copying (Sections 3 and 4), and it creates Apple 4.1 and 5.2 risk.
- **Extracting secrets.** Harvesting API keys, endpoints or credentials embedded in a competitor's app and calling their backend. That is unauthorized use of someone else's service and account, not research. **[LAWYER]** on computer-misuse law; not researched here.
- **Paywall bypass.** Unlocking paid features without paying.
- **Sending decompiled code to an LLM.** Uploading a competitor's decompiled proprietary code to a third-party model provider (REA's FAQ notes the provider sees tool results). This adds confidentiality and copyright-copying exposure.

**Better substitutes for "which AI provider / which backend does it use?"**
- The App Store privacy label lists data types collected, including by third-party SDKs (Section 2).
- The app's privacy policy and sub-processor list often name AI vendors.
- Job postings, the company's engineering blog and founder interviews often name the stack.
- A paid SDK-intelligence database (Appfigures SDK Intelligence, Section 2).
- The competitor's public web app, observed in a normal browser.

**Bottom line on REA:** REA is a powerful, legitimate tool whose disclaimer puts all authorization responsibility on the user. For this founder, its value is mostly:
- (a) quick SDK and framework fingerprinting of Android APKs you have lawfully installed
- (b) analyzing your own app's traffic and builds, for example to debug paywall or analytics events

Its "understand a feature and build a version" workflow should be replaced with clean-room product reasoning: observe behavior from the outside, then write your own spec, code and assets.

### Gaps
- REA's docs do not say how to lawfully obtain an iOS IPA, and they do not address FairPlay. I could not confirm whether REA's Apple inventory can read framework names inside an encrypted App Store IPA. My belief is that FairPlay encrypts executable code, not bundle resources or folder names, but that is unverified.
- REA's CLI guide (`docs/cli.md`) and MCP tool catalog were not read in full. There may be additional tools not covered here.
- The REA star count conflicts: the README says 90,000; the GitHub page fetch reported about 104k.

---

## 2. Non-invasive teardown methods and tools (what exists, what it costs)

### Takeaway
Most of what a founder needs (onboarding flows, paywall design and prices, SDK stack, complaints and feature requests, keywords and ads) is available without touching a competitor's code. The sources are: your own screen recordings of a normal install, design libraries (Mobbin, ScreensDesign, Superwall's template gallery), the App Store privacy label, SDK-intelligence databases (Appfigures), review-mining tools, ASO tools (Appfigures free Starter tier, Astro), and ad libraries (Meta Ad Library, TikTok Creative Center).

### Cited Findings

**Screen design libraries**
- **Mobbin** is described as a searchable library of real shipped-app screens and full flows, including onboarding, checkout and paywalls.
  - Free access is available; a paid Pro plan adds full search and Figma copy.
  - One directory cites 599,800+ screens, 320,000+ flows and 1,150+ production apps.
  - An official Mobbin MCP server reportedly launched May 12, 2026, and requires a paid plan.
  - All of this comes from third-party directories, not mobbin.com, so verify it. — [Toolworthy – Mobbin alternatives 2026](https://www.toolworthy.ai/blog/mobbin-alternatives); [GTM Directory – Mobbin](https://thegtmdirectory.com/tools/mobbin/md); [ChatForest – Mobbin MCP review](https://chatforest.com/reviews/mobbin-mcp-server/) (search-summary)
- **ScreensDesign** exists and has per-app onboarding and paywall pages, with recorded flows for apps such as Cal AI and Flo. It is described as offering "iOS onboarding, paywall and revenue benchmarks", plus a library, an MCP and paid pricing. — [ScreensDesign onboarding example](https://screensdesign.com/explore/apps/i-am/onboarding/); [ScreensDesign paywall example](https://screensdesign.com/explore/apps/i-am/paywall/); [Toolworthy](https://www.toolworthy.ai/blog/mobbin-alternatives) (search-summary; the homepage could not be fetched)
- **Superwall** docs list a "Template Gallery". Third-party sources disagree on its size:
  - "over 200 paywall templates ... updated daily" — [Toolradar – Superwall](https://toolradar.com/tools/superwall)
  - "10,000+ real-world paywall examples" — [The Swift Kit – RevenueCat vs Superwall](https://theswiftk.it.com/blog/revenuecat-vs-superwall-ios-paywalls)
  - Docs listing: [Superwall dashboard docs](https://superwall.com/docs/dashboard/llms-full.txt)
  - An indie-developer blog points to Superwall's paywall gallery for design ideas. — [Lickability blog](https://lickability.com/blog/monetizing-your-app-with-superwall) (search-summary)
- **RevenueCat** has no official paywall-examples gallery that I could find. It does publish teardown and paywall-strategy content (below). — (search-summary)

**SDK and stack intelligence**
- **Appfigures SDK Intelligence** claims to "reveal SDKs inside millions of iOS and Android apps", identifying SDKs and native APIs across ads, analytics, frameworks and notifications. It says it scans every app update. It is a paid product (pricing not verified). — [Appfigures SDK Intelligence](https://appfigures.com/products/sdk-intelligence) (search-summary)
- **App Store privacy labels** reveal a competitor's data collection, including SDKs. Apple requires developers to disclose "the practices of third-party partners whose code you integrate into your app". It defines third-party partners as "analytics tools, advertising networks, third-party SDKs, or other external vendors". Labels appear "on each app's product page". — [Apple – App privacy details](https://developer.apple.com/app-store/app-privacy-details/)

**ASO, keyword and ranking tools**
- **Appfigures** offers a free "Starter" plan; third parties say it tracks up to 5 apps. Paid tiers on the official page (search-summary): Connect $9.99/mo, Monitor $44.99/mo, Optimize $149.99/mo. A third-party profile listing a "$99/mo Pro" plan conflicts with this. — [Appfigures pricing](https://www.appfigures.com/pricing); conflicting: [stork.ai](https://www.stork.ai/en/appfigures)
- **Astro** (Mac-only, iOS keyword ASO tool):
  - $9/month billed annually ($108/yr) for unlimited keywords, with a free trial.
  - One report says that after an Apple algorithm change, its keyword data has been "frozen from before October 2025". **[possibly outdated / verify]**
  - The source is a competitor's (Sonar's) blog, so verify on tryastro.app. — [Sonar – Astro ASO pricing 2026](https://trysonar.app/blog/astro-aso-pricing)
- **Sensor Tower and AppTweak:** not verified in this research (see Gaps). Sensor Tower publishes free estimate-based blog analyses that are useful for category history, e.g. its Calm Q1 2019 revenue post. — [Sensor Tower blog – Calm revenue Q1 2019](https://sensortower.com/blog/calm-revenue-q1-2019)

**Ad libraries**
- **Meta Ad Library** can be searched by advertiser name, page ID or keyword. A per-advertiser active-ads view is the most useful for tracking competitors. A vendor blog claims it shows every active ad on Facebook, Instagram, Messenger and Audience Network. — [PageCrawl blog](https://pagecrawl.io/blog/meta-tiktok-ad-library-competitor-creative-monitoring); [Atria](https://www.tryatria.com/blog/how-to-find-your-competitors-ads) (search-summary)
- **TikTok Creative Center "Top Ads"**:
  - Filter by country, industry, objective, period and format.
  - Shows engagement, CTR percentile and budget tier.
  - It only shows ads whose advertisers authorized inclusion, so it is a curated sample, not a full competitor list. — [Moda – TikTok Creative Center](https://moda.app/blog/tiktok-creative-center)
  - Conflicting: Seer Interactive said the TikTok Ads Library did not show US ads at the time of writing, and that richer data needs a Business Center login. — [Seer Interactive](https://www.seerinteractive.com/insights/scope-out-competition-with-meta-tiktok-and-reddit-ads-libraries)
  - Also: [Airbridge – research competitor app ads for free](https://www.airbridge.io/en/blog/how-to-research-competitor-app-ads-for-free)

**Review-mining tools**
- Apify actors classify App Store and Google Play reviews into bugs, feature requests, competitor mentions and sentiment. Listed prices are "$50.00 / 1,000" app analyses and "from $1.00 / 1,000" reviews. — [Apify – App Store Review Miner](https://apify.com/automationnation/app-store-review-miner); [Apify – App Review Intelligence](https://apify.com/crashlattice57/app-review-intelligence)
- AppReview AI has a free tier of 3 analyses/month. — [Hunted – AppReview AI](https://www.hunted.space/product/appreview-ai)
- Kimola offers an App Store review scraper and analyzer. — [Kimola](https://kimola.com/scrape-and-analyze-app-store-reviews)
- Pricing for all review-mining tools came from search summaries and may have changed.

**Paywall and onboarding teardown content**
- RevenueCat's paywall guide says the onboarding paywall is often where most conversions happen. It reports onboarding accounting for about 50% of trial starts at Mojo. — [RevenueCat – Guide to mobile paywalls](https://www.revenuecat.com/blog/growth/guide-to-mobile-paywalls-subscription-apps.md) (search-summary)
- RevenueCat argues for earlier paywall placement: "It's time to stop being so cautious with paywall placement." — [RevenueCat – Paywall placement](https://www.revenuecat.com/blog/growth/paywall-placement.md) (search-summary)
- RevenueCat published a UX teardown of Noom's web-to-app onboarding: "113 screens build commitment before the paywall". It also published hard-vs-soft paywall case studies (Headspace, Lose It!) and a Jobs-to-be-Done onboarding redesign case study (Applica). — [RevenueCat blog author listing](https://www-docs.revenuecat.com/blog/author/daphne-tideman/posts/) (search-summary; exact article URLs not retrieved)
- A developer's measurement checklist covers onboarding completion, paywall views, dismissals, trial starts, purchases and restores. — [HackerNoon – RevenueCat paywall write-up](https://hackernoon.com/i-built-a-revenuecat-paywall-that-doesnt-hold-the-first-lesson-hostage)

### Inferences
- The highest-signal, lowest-risk loop is:
  - (1) Install each competitor as a normal user on a clean device. Screen-record onboarding, paywall, first session and cancellation, using a paid trial if needed and cancelling in time.
  - (2) Compare against ScreensDesign or Mobbin for historical variants.
  - (3) Read the privacy label and privacy policy for the SDK and vendor stack.
  - (4) Mine 1- to 3-star reviews for unmet needs.
  - (5) Pull their ads from the Meta Ad Library.
  - None of this requires decompiling.
- Keep screen recordings and screenshots as **internal research only**. Don't republish them, and don't trace over them in Figma for your own UI. Use them to write a feature/requirement spec in your own words, then design from that spec (clean-room style).
- For pricing history, recording the in-app price points shown on each competitor's store page and paywall at fixed intervals (monthly) is a free substitute for paid tools. I found no verified free price-history tool (see Gaps).

### Gaps
- Not verified: Sensor Tower's and AppTweak's current free tiers, AppFollow's features, Mobbin's and ScreensDesign's official pricing (their sites could not be fetched), a free in-app-purchase price-history tracker, and Exodus Privacy (Android tracker reports; I believe it exists but retrieved no source).
- Whether Superwall's gallery is public or requires a Superwall account was not confirmed.

---

## 3. Legal limits: copyright, trademarks/trade dress, ToS/EULA anti-decompiling clauses, Australian law (s47B–s47H, s116AN), US DMCA

### Takeaway
Copyright protects expression (code, UI art, copy, icons, sounds), not ideas, features, mechanics or business models. A rival app built from your own code and assets to solve the same problem is generally lawful. Liability comes from copying expression, from confusing branding (passing off / misleading conduct, trademarks), from breaching licence terms, and from circumventing technical protections.

Australia's decompilation and interoperability exceptions (s47D, and s116AN(3) for TPMs) are narrow and are aimed at **interoperability, not at building a substitute competitor**. **[LAWYER]**

### Cited Findings

**Ideas vs expression (Australia)**
- "Ideas, concepts or techniques cannot be protected by copyright. If the ideas (such as the plot of a book) are used by another author, this will only amount to an infringement if there has been a substantial reproduction of the work produced by the original author's skill and labour." — [Law Handbook SA – Copyright](https://lawhandbook.sa.gov.au/ch11s13.php)
- The Australian Copyright Council's fact sheet G010 is reported to say copyright does not protect ideas, information, styles, techniques, names, titles or slogans. (search-summary; fact sheet not read directly)

**Passing off and misleading conduct (Australia)**
- Passing off is "a trader's remedy designed to prevent rival traders from cashing in on an established reputation ... by adopting a similar name or other distinctive feature of a product". The Australian Consumer Law's misleading-or-deceptive-conduct prohibition "might also prevent the copying of an existing title." — [Law Handbook SA](https://lawhandbook.sa.gov.au/ch11s13.php)

**s47D (interoperability)** (search-summary of AustLII text)
- Copyright in a computer program is not infringed by a reproduction or adaptation if all of these hold:
  - it is made by or for the **owner or licensee** of the copy
  - its purpose is obtaining information necessary to independently make a program or article that **interoperates** with the original
  - it goes only to the extent reasonably necessary
  - the information is not readily available elsewhere
  - it is not made from an infringing copy.
- Introduced by the Copyright Amendment (Computer Programs) Act 1999.
- Sources: [AustLII – Copyright Act 1968 s47D](https://www6.austlii.edu.au/au/legis/cth/consol_act/ca1968133/s47d.html); [ALRC Report 122 – Exceptions for computer programs](https://www.alrc.gov.au/publication/copyright-and-the-digital-economy-alrc-report-122/17-computer-programs-and-back-ups/exceptions-for-computer-programs/)

**How narrow the exceptions are**
- The Federal Court in *CA Inc v ISI Pty Ltd* called s47D a "very limited exception".
- The ALRC noted that reproducing only "to the extent reasonably necessary" is often impractical.
- The Internet Industry Association called ss47B and 47D "seriously out of date".
- Source: [ALRC Report 122](https://www.alrc.gov.au/publication/copyright-and-the-digital-economy-alrc-report-122/17-computer-programs-and-back-ups/exceptions-for-computer-programs/) (search-summary)

**s47B and s47H (contracting out)**
- s47B is titled "Reproduction for normal use or study of computer programs". The exact text of s47B(3) was not retrieved. — [ALRC – Contracting out, current law](https://www.alrc.gov.au/publication/copyright-and-the-digital-economy-alrc-report-122/20-contracting-out/current-law-6/) (search-summary)
- s47H says: "An agreement, or a provision of an agreement, that excludes or limits, or has the effect of excluding or limiting, the operation of subsection 47B(3), or section 47C, 47D, 47E or 47F, has no effect." — [AustLII – s47H](https://20.austlii.edu.au/au/legis/cth/consol_act/ca1968133/s47h.html) (search-summary)
- The ALRC notes that s47H's effect on other exceptions is "ultimately unclear". — [ALRC – Contracting out](https://www.alrc.gov.au/publication/copyright-and-the-digital-economy-alrc-report-122/20-contracting-out/current-law-6/) (search-summary)

**s116AN (TPM circumvention, Australia)**
- s116AN creates civil liability for circumventing an access-control TPM.
- s116AN(3) exempts circumvention for interoperability, but only if all of these hold: the copy is non-infringing and lawfully obtained; the act won't infringe; it relates to elements not readily available; and its **sole purpose** is interoperability of an independently created program.
- Other exceptions: s116AN(2) covers the owner's permission and s116AN(4) covers encryption research.
- Source: [AustLII – s116AN](https://20.austlii.edu.au/au/legis/cth/consol_act/ca1968133/s116an.html) (search-summary)
- In 2024 the Federal Court found liability under s116AO (manufacturing or supplying a circumvention device) over a game-modification tool. — [Take-Two Interactive v Anderson (No 2) [2024] FCA 1459](https://www.judgments.fedcourt.gov.au/judgments/Judgments/fca/single/2024/2024fca1459) (search-summary; judgment not read)

**US DMCA s1201(f) (reverse engineering)**
- It permits circumventing a TPM on a computer program for "identifying and analyzing those elements of the program that are necessary to achieve interoperability of an independently created computer program with other programs".
- Conditions: lawful access, elements not previously readily available, and the analysis must not itself infringe.
- Courts read it as applying to computer programs only.
- Sources: [Duke CS – Copyright footnotes quoting §1201(f)](https://courses.cs.duke.edu/cps182s/fall02/cscopyright/Copyrights/Copyright-Footnotes.htm); [Stanford – DeCSS lawsuits summary](https://cs.stanford.edu/people/eroberts/cs201/projects/1999-00/dvd-css/lawsuits.htm); [Project DisCo – Interoperability and the 1201 report](https://project-disco.org/intellectual-property/070617-interoperability-and-the-copyright-offices-section-1201-report/) (search-summary; official text at law.cornell.edu / uscode.house.gov could not be fetched)
- Congress endorsed *Sega v. Accolade* (reverse engineering for interoperability as fair use) in the DMCA's legislative history. — [Project DisCo](https://project-disco.org/intellectual-property/070617-interoperability-and-the-copyright-offices-section-1201-report/) (search-summary)

**Contracts can override fair use in the US**
- *Bowers v. Baystate Technologies* (Fed. Cir. 2003) held a shrink-wrap clause prohibiting reverse engineering enforceable. It rejected Copyright Act preemption, even though reverse engineering had been treated as fair use. Judge Dyk dissented. — [Wikipedia – Bowers v. Baystate](https://en.wikipedia.org/wiki/Bowers_v._Baystate_Technologies,_Inc.); [WilmerHale – Shrink-wrap licenses and reverse engineering (2003)](https://www.wilmerhale.com/en/insights/publications/shrink-wrap-licenses-and-reverse-engineering-april-16-2003)

**Store EULA**
- Apple's standard Licensed Application EULA says apps are licensed, not sold. It prohibits copying (except as permitted), reverse engineering, disassembling, decompiling and attempts to derive source code. It carves out cases where "applicable law" prohibits the restriction, and open-source component licences. — [Apple Standard EULA](https://www.apple.com/legal/internet-services/itunes/dev/stdeula/) (search-summary; page could not be fetched; wording should be checked)

**Clone litigation (US)**
- *Tetris Holding v. Xio Interactive* (D.N.J., May 30, 2012) concerned Xio's "Mino". The court:
  - protected Tetris's artistic or expressive elements but not its functional mechanics
  - found Mino nearly identical in protectable expression
  - also found trade-dress infringement (likelihood of confusion).
- A permanent injunction followed in 2013. Commentators saw the case as narrowing the "we only copied the functional rules" defence for clones.
- Sources: [Loeb & Loeb summary](https://www.loeb.com/en/insights/publications/2012/06/tetris-holding-llc-v-xio-interactive-inc); [Proskauer New Media Law blog](https://newmedialaw.proskauer.com/2012/06/19/videogame-app-developer-breaks-the-rules-on-copyright-infringement/); [IPWatchdog – permanent injunction (2013)](https://ipwatchdog.com/2013/02/12/tetris-gets-permanent-injunction-against-xio/)

### Inferences
**"Clone the concept, not the code" in practice**
- OK to reuse: the problem solved; feature set; general flow patterns (quiz-style onboarding, then a personalized plan, then a paywall); pricing *structure* (weekly/annual, trial length); business model; tech-stack choices; generic UI conventions.
- Do NOT reuse:
  - their source or decompiled code
  - images, illustrations, icons, mascots, animations, sounds, fonts they licensed
  - onboarding questions and marketing copy verbatim
  - distinctive colour/layout combinations that make the app look like theirs (Tetris shows "look" can be protected even when mechanics are free)
  - their name, or a confusingly similar name or icon
  - screenshots or video of their app in your store listing.

**Interoperability is not competition.** s47D and s116AN(3) protect reverse engineering *to make something that works with* the original program. Building a competing substitute app is a different purpose. Do not assume they authorize decompiling a competitor to build a rival. **[LAWYER]**

**Contracts.** In Australia, s47H stops a EULA from overriding s47D or s47B(3) where those exceptions actually apply. In the US, *Bowers* suggests an anti-reverse-engineering clause can be enforced as a contract. If the founder sells to US users or the competitor sues in the US, contract exposure may exist even where copyright exposure doesn't. **[LAWYER]**

**Questions for an IP lawyer**
- (1) Does running and black-box observing a competitor app, plus reading its manifest and SDK names, fall within s47B(3) and/or outside infringement altogether?
- (2) Is any decompilation of a competitor app for "study" defensible in Australia when the goal is a competing product?
- (3) Do TLS, certificate pinning or FairPlay count as access-control TPMs under s116AN and DMCA s1201?
- (4) What is the exposure under app EULAs and the developer's own terms, given s47H in Australia vs *Bowers* in the US?
- (5) Clearing a name and icon via IP Australia trade mark searches and USPTO searches.
- (6) Whether recorded screenshots or video of competitors can be used internally only, or also in marketing comparisons.

### Gaps
- Not verified: s47B(3)'s exact wording; the current consolidated text of s47D, s47H and s116AN after any amendments since the ALRC 2013 report; Australia's trade mark and passing-off position on app icons and "get-up" (no source found); DMCA triennial exemptions (2024 cycle) relevant to apps; Australian or US computer-misuse statutes on using a competitor's API keys or backend.
- No Australian case specifically about mobile-app clones was found.

---

## 4. App-store policies on copycats, and documented clone removals and successful "better clones"

### Takeaway
Apple's 4.1 (Copycats), 4.3 (Spam) and 5.2 (IP) and Google Play's Impersonation, IP and Spam/Minimum-Functionality policies target three things: near-identical copies, borrowed names and icons, and low-value variants. A differentiated app in an existing category is allowed, but in saturated categories Apple explicitly requires a "meaningfully different or improved experience". Wordle clones were pulled in January 2022. Later entrants such as Calm and Cal AI won by differentiating, not copying.

### Cited Findings

**Apple App Review Guidelines (verbatim, fetched 2026-10-12; no last-updated date shown on the page)** — [Apple App Review Guidelines](https://developer.apple.com/app-store/review/guidelines/)
- **4.1(a):** "Come up with your own ideas. ... Don't simply copy the latest popular app on the App Store, or make some minor changes to another app's name or UI and pass it off as your own. In addition to risking an intellectual property infringement claim, it makes the App Store harder to navigate and just isn't fair to your fellow developers."
- **4.1(b):** "Submitting apps which impersonate other apps or services is considered a violation of the Developer Code of Conduct and may result in removal from the Apple Developer Program."
- **4.1(c):** "You cannot use another developer's icon, brand, or product name in your app's icon or name, without approval from the developer."
- **4.3(b):** "Don't submit apps that are indistinguishable from what's already widely available. ... Certain kinds of apps, such as dating, flashlight, sound effects, wallpaper, simple timers, and fortune telling, are well established on the App Store and we will not accept new submissions unless they offer a meaningfully different or improved experience." Apple "may remove these apps ... if they are not updated, improved, or do not attract customers."
- **4.3(a):** prohibits multiple Bundle IDs of the same app.
- **5.2.1:** "Don't use protected third-party material such as trademarks, copyrighted works, or patented ideas in your app without permission, and don't include misleading, false, or copycat representations, names, or metadata in your app bundle or developer name."

**Google Play Impersonation policy** (search-summary of the official page)
- It prohibits misleading users into thinking an app is connected to another developer, company or app.
- Listed examples: copying a business's logo to pass as its official app; copying a famous TV show's character and title in the icon; titles like "Justin Bieber Official" without rights; developer names implying a Google relationship.
- Source: [Google Play Console Help – Impersonation](https://support.google.com/googleplay/android-developer/answer/9888374)
- Search summaries also reported a Play policy statement that labelling an app "unofficial" does not cure use of copyrighted content without permission. The exact page was not confirmed.

**Google Play enforcement and naming practice**
- An impersonation strike led to suspension and removal of a fake "Notepad++" app. — [Notepad++ community thread](https://community.notepad-plus-plus.org/post/89163)
- An XDA guide advises placing trademarks at the end of a title prefixed with "for" (e.g. "Browser for X"). Modified spellings like "G00gle" are treated as confusing. — [XDA – Play Store policies and common mistakes](https://www.xda-developers.com/google-play-store-policies-and-common-mistakes-to-avoid/)

**Google Play Spam / Minimum Functionality**
- Copying content from another Play app without adding original content or value, and publishing multiple near-identical apps, are violations. Google removed the Mitron app citing its "spam and minimum functionality" policy. — [The Quint – Mitron removed](https://www.thequint.com/amp/story/tech-and-auto/tech-news/mitron-app-taken-down-from-google-playstore-found-violating-policy)
- Google's 2020 developer blog flags keyword-stuffed listings and abandoned apps. — [Android Developers Blog (Oct 2020)](https://android-developers.googleblog.com/2020/10/developer-tips-and-guides-common-policy.html) **[possibly outdated; current Play policy text not fetched]**

**Documented removal: Wordle clones (January 2022)**
- Apple removed numerous Wordle clones around January 11–12, 2022, after backlash over a clone released January 10 by developer Zach Shakked. Apple confirmed the removals to USA Today but gave no count.
- Clones using the "Wordle" name with identical rules were pulled. Some similar games that didn't use the name stayed.
- Sources: [Macworld](https://www.macworld.com/article/678335/wordle-clones-are-removed-from-the-app-store.html); [Game Developer](https://gamedeveloper.com/mobile/-i-wordle-i-clones-nuked-from-ios-app-store); [MobileSyrup](https://mobilesyrup.com/2022/01/12/apple-app-store-multiple-wordle-clones-remove/)
- Sources differ slightly on the date.

**Successful later entrant: Calm vs Headspace**
- Headspace launched in 2010 and Calm in 2012.
- Calm won Apple's App of the Year in 2017 and passed Headspace in downloads and revenue.
- Sensor Tower estimates for Q1 2019: Calm about $30M (up 132% year on year) vs Headspace $13.1M.
- These are third-party estimates.
- Sources: [Sensor Tower](https://sensortower.com/blog/calm-revenue-q1-2019); [The Hustle](https://thehustle.co/calm-headspace-meditation-wellness); [Appfigures insight (2021)](https://appfigures.com/resources/insights/20210827/3-why-did-headspace-do-that)

**Successful later entrant: Cal AI vs MyFitnessPal**
- Cal AI launched May 2024. It is a calorie tracker built around photographing meals, differentiating from incumbents' manual and barcode logging.
- Reported trailing-12-month sales exceeded $40M with 15M+ downloads. Growth relied heavily on a network of 250+ fitness influencers.
- MyFitnessPal acquired it. Sources disagree on timing (December 2025 close vs a March 2026 announcement) and on revenue ($30M–$50M; $50M is weakest).
- Co-founder and CEO is Zach Yadegari (a different person from the Wordle-clone developer).
- Sources: [Techleap](https://finder.techleap.nl/news/note/myfitnesspal-acquires-teen-built-cal-ai-after-40m-in-annual-sales); [Founded](https://www.founded.com/this-teenager-built-a-30m-a-year-calorie-app-in-high-school-then-sold-it-to-myfitnesspal-two-years-later/); [Let's Data Science](https://letsdatascience.com/news/cal-ai-sells-to-myfitnesspal-after-rapid-growth-f789c949)

### Inferences
- **Practical store-safe rules:**
  - Original name and icon, with no competitor brand in the title, keywords used carefully.
  - Original screenshots and copy.
  - A clearly stated differentiator in the first screenshot and the review notes. This matters most in Apple-listed saturated categories (dating, timers, wallpapers and so on), where 4.3(b) demands a "meaningfully different or improved experience".
  - One app per concept, not many variants.
- Both success cases changed the *core experience*: Calm's sleep stories and positioning, Cal AI's photo-first logging. Neither re-skinned the incumbent. That is the template for a "better version".

### Gaps
- Not fetched: the current Google Play Intellectual Property policy text (answer/9888072) and the full Impersonation page.
- No primary data on how often Apple rejects apps under 4.1 or 4.3 (Apple publishes aggregate rejection stats in its transparency report, but these were not retrieved).
- No documented Australian-founder clone dispute was found.

---

## 5. Step-by-step teardown checklist and template, and turning findings into a differentiated feature list

### Takeaway
Use a fixed per-competitor template filled only from lawful, outside-in observation:
- store page
- your own recorded install, onboarding, paywall and first week of use
- privacy label and policy
- reviews
- ad libraries
- SDK databases or an SDK-namespace check of an APK you installed

Then convert the gaps (unmet complaints, weak paywall or onboarding, missing features) into a ranked, differentiated feature list written in your own words before any design work starts.

### Cited Findings
- Onboarding is a primary conversion surface: about 50% of trial starts at Mojo came from the onboarding paywall. — [RevenueCat paywall guide](https://www.revenuecat.com/blog/growth/guide-to-mobile-paywalls-subscription-apps.md) (search-summary)
- Long, commitment-building onboarding (Noom: 113 screens before the paywall) is a documented pattern worth recording screen by screen. — [RevenueCat blog listing](https://www-docs.revenuecat.com/blog/author/daphne-tideman/posts/) (search-summary)
- Metrics to model for your own app: onboarding completion, paywall views, dismissals, trial starts, purchases, restores. — [HackerNoon](https://hackernoon.com/i-built-a-revenuecat-paywall-that-doesnt-hold-the-first-lesson-hostage)
- Privacy labels disclose third-party SDK data collection on each product page. — [Apple – App privacy details](https://developer.apple.com/app-store/app-privacy-details/)
- Review-mining tools classify reviews into bugs, feature requests, competitor mentions and sentiment. — [Apify Review Miner](https://apify.com/automationnation/app-store-review-miner)
- Meta Ad Library per-advertiser view; TikTok Top Ads is a curated, opt-in sample. — [PageCrawl](https://pagecrawl.io/blog/meta-tiktok-ad-library-competitor-creative-monitoring); [Moda](https://moda.app/blog/tiktok-creative-center)
- Apple will reject undifferentiated apps in saturated categories (4.3(b)). — [Apple guidelines](https://developer.apple.com/app-store/review/guidelines/)

### Inferences

**Per-competitor teardown template** (one doc or sheet per app; this structure is my synthesis)

**A. Store and market**
- App name, developer, URL (iOS and Android), category and rank, rating and count.
- Update cadence.
- Price points shown on the store page.
- Screenshot messaging (headline promise).
- Keywords it ranks for (Appfigures free tier, Astro).
- Estimated downloads and revenue (Appfigures or Sensor Tower estimates; label them as estimates).

**B. Core loop**
- The one job the app does.
- The trigger, action and reward cycle.
- Time-to-first-value in seconds or screens.
- Main screens and navigation.

**C. Onboarding** (screen-record a fresh install)
- Number of screens.
- Question types (goals, demographics, pain points).
- Personalization claims ("your plan is ready").
- Permission prompts and their order (notifications, tracking, health data).
- Account-creation point.
- Social proof used.

**D. Paywall**
- Placement: onboarding, feature gate, or after a usage limit.
- Hard vs soft (can you dismiss it?).
- Plans and prices (weekly, monthly, annual, lifetime) and trial length.
- Discount or exit offers.
- Copy angle.
- Restore and cancel visibility.
- Re-check monthly and log changes for a price history.
- Cross-check against ScreensDesign or Mobbin snapshots and the Superwall gallery.

**E. Retention**
- Streaks, reminders, progress views, widgets, social features, content drops.
- Notification strategy: log every push for 7–14 days (time, copy, frequency).
- Email and SMS after sign-up.

**F. Tech stack** (outside-in)
- Privacy-label data types.
- Privacy policy and sub-processors (AI vendors are often named).
- SDK intelligence (Appfigures).
- Optionally, SDK namespaces and frameworks from an APK you lawfully installed, read via REA/Apktool manifest and package listing only.
- Cross-platform framework hints.
- Never: decrypted binaries, intercepted competitor traffic, or extracted keys (see Section 1, RED).

**G. Review sentiment**
- Export 200–500 recent reviews per platform.
- Tag by theme: bugs, pricing complaints, missing features, onboarding friction, accuracy.
- Count the frequency of each theme and pull verbatim quotes for internal use.

**H. Acquisition**
- Meta Ad Library active ads: count, formats, hooks, offers, landing pages.
- TikTok Top Ads for category trends.
- Influencer and UGC patterns (Cal AI's influencer network is an example of a channel-led win).

**I. Risk notes**
- Their trademarks and name, distinctive visual identity, mascots and illustrations, and any patents mentioned. These are the things to steer clear of.

**From findings to a differentiated feature list**
- (1) Build a matrix with competitors as columns and template rows as rows. Mark table stakes (present in 3 or more competitors) vs differentiators.
- (2) From review tags, rank unmet needs by frequency and severity. These are the "better version" opportunities.
- (3) For each candidate feature, write a one-line user outcome in your own words (not the competitor's copy) and a reason it beats the incumbent: faster time-to-value, fairer paywall, better accuracy, missing platform, lower price, or a niche audience.
- (4) Choose one sharp wedge, like Calm's sleep or Cal AI's photo logging, and keep the rest at table stakes.
- (5) Run a "store-safety check" before design:
  - original name and icon, cleared with IP Australia and USPTO searches **[LAWYER]**
  - no competitor brand in metadata
  - visibly different visual language
  - a differentiator stated in the first screenshot and App Review notes (4.1 / 4.3(b))
- (6) Design and code from your written spec, not from competitor screenshots or decompiled output (clean-room practice).

### Gaps
- No single authoritative, published teardown template from RevenueCat, Growth.Design or Superwall was retrieved. The template above is a synthesis, not a quoted framework.
- Growth.Design case studies were not checked in this research.
- Benchmarks for "good" onboarding length, paywall conversion or trial-to-paid rates were not gathered (outside this scope; one paywall-audit resource claimed 79 sourced 2026 benchmarks but was not verified).
