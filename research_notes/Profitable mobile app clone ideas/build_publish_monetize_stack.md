# Build, Publish and Monetize Stack: Cheapest and Fastest Path to iOS + Google Play (late 2026, about US$1,000, about 1 month, non-developer)

Verification note: all items were checked on **2026-10-12** unless stated otherwise. In this session the page-fetch tool could load only a few official pages in full: Apple's App Review Guidelines, Apple's Small Business Program page and Anthropic's vision docs. Most other official pages (rork.com, revenuecat.com, superwall.com, adapty.io, ai.google.dev, support.google.com, flutterflow.io) failed DNS lookup in the fetch tool. For those, figures come from search-engine extracts of the official URLs, cited as the official page and marked "(search extract)". Third-party sources such as competitor blogs and aggregators are labelled. Toward the end of the session the web-search budget ran out, so a few items are listed as unverified in Gaps.

---

## 1. Which AI/no-code builders produce real native iOS + Android apps and publish to both stores?

### Takeaway
For a non-developer who needs both stores, the strongest low-cost choice is **Rork Pro (~$20/mo)**. It has built-in App Store build and upload with no Mac needed, builds a signed Android AAB, and has built-in RevenueCat. Its expensive "Max" tier is iOS-only. The best no-lock-in alternative is **Expo (React Native) + an AI coding agent (Claude Code or Cursor, ~$20/mo) + Expo EAS free tier**, but it requires using a terminal. FlutterFlow ($39/mo Basic) is the mature visual option. Base44, Lovable and Bubble-style tools reach the stores mainly by wrapping a web app (WebView), which carries Apple 4.2 "minimum functionality" risk.

### Cited Findings

**Rork** (rork.com; AI builder for mobile apps)
- Plans per Rork docs: Free = 35 credits/month in major markets (5 elsewhere), capped at 5/day. **Rork Pro = $20/month, 100 credits**, "covers iPhone (SwiftUI), Android, and web apps", email support. **Rork Max from $200/month** (1,000 credits) up to $1,800/month (10,000 credits) and adds iPad, Apple Watch, Vision Pro, native games, iOS widgets. A credit is roughly one AI request. Rork's FAQ says credits currently cannot be bought separately — [Rork docs: Plans & Subscriptions](https://docs.rork.com/introduction/subscriptions) (search extract); [Rork pricing](https://rork.com/pricing) (search extract)
- A third-party page says Pro tiers run $20–$100/month for 100–500 credits and estimates about $0.20 per AI message — [vp0.com Rork pricing 2026](https://vp0.com/blogs/rork-pricing-plans-2026/) (third-party; competitor blog). Rork's older FAQ says paid plans run "$25 to $200+" and that Pro exports a React Native/Expo project while Max exports a native SwiftUI Xcode project. That FAQ is stale and conflicts with the current docs — [Rork FAQ](https://rork.com/faq) (search extract)
- Publishing: Rork has built-in App Store publishing. It builds and uploads on Rork's machines, so **no Mac or Xcode is needed**. You still need your own Apple Developer account and must finish the listing in App Store Connect. For Android, Rork builds an AAB, signs it with a stable upload key and can push it to your **internal testing track**. You create the app record in Play Console and submit releases there yourself. **"Rork Max apps are iOS-only and cannot be published to Google Play."** — [Rork docs: Publishing](https://docs.rork.com/faq/publishing) (search extract)
- In-app purchases: both Pro and Max have **built-in RevenueCat integration** ("ask Rork to set up payments"). Real subscriptions still need setup in App Store Connect and RevenueCat, plus TestFlight for the final purchase test. Rork warns that the App Store will reject the app without a **privacy policy, terms and conditions, and a visible EULA** — [Rork docs: RevenueCat paywall guide](https://docs.rork.com/payment-guides/revenuecat-copied-1) (search extract)
- Code export: existing Expo projects can still be built, published and exported to GitHub. Rork has a docs page titled "What happened to Expo?", which suggests newer projects moved off Expo — [Rork docs: What happened to Expo?](https://docs.rork.com/expo) (search extract). Push notifications and camera support were not confirmed (see Gaps).
- Vendor case studies (self-reported marketing): two brothers aged 14 and 17 with no coding skills had Hockey AI live by Jan 7 and reached 2,000+ downloads, $1K/month and 114 TestFlight builds in about a month. They spent about $1,000 on influencers against nearly $2,000 revenue. Price: $6.99/month or $39.99/year, with a 3-day trial on the yearly plan — [Rork blog: Hockey AI](https://rork.com/blog/eli-hockey-ai-case-study). Wrestle AI: $131,863 in 6 months — [Rork blog](https://rork.com/blog/george-wrestle-ai-case-study). 3AK Track: $17,460 in 28 days, "verified by RevenueCat" — [Rork blog](https://rork.com/blog/3ak-case-study)

**Expo + AI coding agent (Claude Code / Cursor)**
- Expo EAS Free plan: $0, up to **15 Android + 15 iOS builds/month** on the low-priority queue, with no overages (builds stop until the quota resets). **Starter: $19/month with $45 of build credit** and 3,000 EAS Update MAU (Free: 1,000). Production: $199/month — [Expo pricing](https://expo.dev/pricing); [Expo billing FAQ](https://docs.expo.dev/billing/faq/) (search extracts). A 2023 changelog showing 30 free builds is outdated.
- Claude Pro (includes Claude Code) is listed at about $20/month, with Max at $100/$200. Cursor Pro is about $20/month on a credit pool — [morphllm comparison](https://www.morphllm.com/comparisons/cursor-vs-copilot); [aicodereview.cc Cursor pricing](https://aicodereview.cc/blog/cursor-pricing) (third-party; not verified on the official pages)
- Bolt.new's Expo guide has you install Node.js, Git and the EAS CLI and run builds from the terminal. Bolt generates code but cannot sign or publish — [newly.app Bolt alternatives (Oct 2026)](https://newly.app/compare/bolt-new-alternatives); [vp0.com](https://vp0.com/blogs/can-bolt-new-publish-to-app-store-and-google-play/) (third-party/competitor). Bolt Pro is about $25/month on token billing — [vp0.com Bolt pricing](https://vp0.com/blogs/bolt-new-pricing-2026-explained) (third-party)

**FlutterFlow** (visual builder, Flutter code)
- Free plan: no code download, no APK download, no one-click store deployment, and 5 lifetime AI requests. **Basic is about $39/month billed monthly** (one listing says $29/month annual) and unlocks code download, APK download and app-store deployment. Growth is $80 for the first seat and $55 for the second, and adds GitHub integration — [nocode.mba](https://nocode.mba/articles/flutterflow-pricing), [vp0.com](https://vp0.com/blogs/flutterflow-pricing-plans-2026/), [toolradar](https://toolradar.com/tools/flutterflow/pricing) (third-party, dated June–Aug 2026; official page not reachable)
- RevenueCat is a documented integration, but **purchases do not work on web builds** — [FlutterFlow docs: RevenueCat](https://docs.flutterflow.io/integrations/payments/revenuecat/) (search extract). Push notifications deploy Cloud Functions to your Firebase project — [FlutterFlow docs: Push](https://docs.flutterflow.io/concepts/notifications/push-notifications/) (search extract). Firebase Cloud Functions require the paid Blaze plan; see Q5. App Store deploy needs a bundle ID, an App Store Connect API key and an issuer ID, then "Deploy To App Store" — [FlutterFlow docs: App Store deployment](https://docs.flutterflow.io/deployment/apple-app-store-deployment/) (search extract)

**a0.dev** (React Native/Expo AI builder)
- Free: 1 project with limited messages/credits. Pro from $20/month. Higher tiers up to about $800/month. Publishing to both stores is reported, with a guided App Store Connect / Play Console connection — [vp0.com a0 pricing](https://vp0.com/blogs/a0-dev-pricing-2026-explained); [vp0.com can a0 publish](https://vp0.com/blogs/can-a0-dev-publish-to-app-store-and-google-play) (third-party competitor; no official page found)

**Vibecode** (Expo/React Native AI builder)
- Docs: App Store publishing requires an Apple Developer Program membership ($99/year) and a free Expo account. Apps are React Native + Expo and compile to native iOS/Android. App Store deploy is web-app only — [Vibecode docs: deploy to App Store](https://www.vibecodeapp.com/docs/getting-started/deploy-app-store.md) (search extract)
- Plans: Free, Plus $20, Pro $50 (source download), Max $200. Credits pass through ($1 = $1 of AI usage) — [vp0.com Vibecode pricing](https://vp0.com/blogs/vibecode-pricing-plans-2026); [aitoolscoop](https://aitoolscoop.com/tool/vibecode/) (third-party)
- Apple blocked updates to the Vibecode and Replit iOS apps in 2026 under guideline 2.5.2. This concerns their own on-phone builder apps, not apps built with them — [MacRumors](https://macrumors.com/2026/03/30/apple-pulls-vibe-coding-app/); [The Next Web](https://thenextweb.com/news/vibe-coding-apple-app-store-surge-crackdown)

**Anything (formerly Create.xyz)**
- Free / Pro $19/month / Max $199/month, plus credit packs of $10–$200, per App Store IAP listings and a review — [apppricinglab IAP tracker](https://apppricinglab.com/iap/apple/6751247034); [superappp review](https://www.superappp.com/blog/anything-ai-app-builder-review-2026) (third-party). Mobile output is described as Expo/React Native.
- Apple removed Anything's own iOS app around 26–30 March 2026 under 2.5.2 — [MacRumors](https://macrumors.com/2026/03/30/apple-pulls-vibe-coding-app/); [Medianama](https://www.medianama.com/2026/04/223-apple-vibe-coding-app-ban-anythng/). One source says it returned by April 3 — [appdrift.co](https://appdrift.co/blog/apple-rejecting-vibe-coded-apps) (unverified)

**Base44**
- Added mobile publishing in February 2026. You choose Web or Mobile at publish time, run a store-requirements scan, then download store-ready bundles to upload with your own developer accounts — [Base44 changelog](https://base44.com/changelog/feature/base44-mobile-app-) (search extract). **The output is a WebView wrapper, not a React Native/Swift/Kotlin project** — [vp0.com](https://vp0.com/blogs/can-base44-publish-to-app-store-and-google-play) (competitor)
- GitHub export and store-file download start on the Builder plan, $40/month annual or $50 monthly. Free: 25 message credits/month (max 5/day) — [Appy Pie, prices read Oct 1 2026](https://www.appypie.com/blog/?p=2795745) (third-party). Tech.co lists Starter $20, Builder $40, Pro $80, Elite $160 (annual) — [tech.co](https://tech.co/ai/vibe-coding/base44-review)

**Lovable + wrapper (Capacitor / Median / Despia)**
- Lovable produces web apps. Store distribution uses a wrapper such as Capacitor or Median. Capacitor exposes native features like camera, storage and push. The main risk is Apple 4.2 ("website in a shell"). Wrappers pass more easily with native navigation, push, offline caching or biometrics — [vp0.com](https://vp0.com/blogs/can-lovable-publish-to-app-store-and-google-play), [catdoes.com](https://catdoes.com/blog/lovable-for-mobile-apps), [superappp.com](https://www.superappp.com/blog/can-lovable-make-mobile-apps-how-to-publish-a-lovable-app-to-the-app-store) (vendors selling native rebuilds, so not neutral). No source in this session covered Despia.

**Adalo**
- Free $0 (500 records/app, no store publishing). Starter $36/month, Professional $52/month (another source says $65), Team $160, Business $200 or $250, all annual billing. Store publishing needs a paid plan. Stripe is available, but **no source confirmed native Apple/Google IAP** — [jetadmin.io](https://www.jetadmin.io/blog/adalo-pricing-current-plans-real-costs-and-best-alternatives-in-2026/); [Adalo pricing guide](https://www.adalo.com/posts/pricing-guide-no-code-mobile-app-maker/)

**Bubble (native mobile)**
- Mobile plans started October 1, 2025. Mobile-only, annual billing: Starter $42/month, Growth $169, Team $449, metered by "workload units". Includes build infrastructure and OTA updates — [jetadmin.io Bubble pricing (Jul 2026)](https://www.jetadmin.io/blog/bubble-pricing-in-2026-plans-workload-units-and-when-it-really-makes-sense/); [Adalo on Bubble pricing](https://www.adalo.com/posts/bubble-pricing/) (competitor). IAP handling not confirmed.

**Natively**
- The name is ambiguous. A third-party post describes "Natively" as a website-to-app wrapper at $49/month (about $32/month annual), a one-time $699 lifetime option and a 14-day trial — [vp0.com Natively pricing](https://vp0.com/blogs/natively-pricing-plans-2026/). Capterra describes a native app builder with push and monetization — [Capterra](https://www.capterra.co.uk/software/1237684/AppNatively). Whether natively.dev is an AI/Expo builder or the wrapper could not be confirmed.

**Turnkey submission services (alternative)**
- RapidNative quotes a flat fee to take a Bolt/Lovable app to a store: $349.50 for one store (discounted from $699), excluding developer fees — [vp0.com citing RapidNative](https://vp0.com/blogs/can-bolt-new-publish-to-app-store-and-google-play/) (third-party)

### Inferences
- **Summary matrix** (✔ = confirmed by a source cited above, ? = unclear/unverified, ✘ = confirmed not supported):

| Tool (checked 2026-10-12) | Cheapest useful plan | Real native output | Code export / lock-in | IAP / subs | Push | Camera | Handles store submission |
|---|---|---|---|---|---|---|---|
| Rork Pro | $20/mo (100 credits) | ✔ (iPhone + Android per docs) | GitHub sync ✔; new-project export format ? | ✔ RevenueCat built-in | ? | ? | iOS ✔ build+upload; Android AAB → internal track ✔ |
| Rork Max | $200/mo | ✔ SwiftUI | ? | ✔ | ? | ? | **iOS only ✘ Google Play** |
| Expo + Claude Code/Cursor | ~$20/mo agent + EAS $0 | ✔ React Native | ✔ full ownership | ✔ via RevenueCat SDK (you wire it up) | ✔ (Expo) ? not verified this session | ? | EAS Submit (CLI; terminal needed) |
| FlutterFlow Basic | ~$39/mo (monthly) | ✔ Flutter | ✔ on Basic+ (GitHub on Growth) | ✔ RevenueCat (not web) | ✔ via Firebase (needs Blaze) | ? | Deploy buttons after API-key setup |
| a0.dev | ~$20/mo | ✔ RN/Expo (3rd-party) | ? | ? | ? | ? | "one-click" (3rd-party claim) |
| Vibecode | $20/mo Plus | ✔ RN/Expo | source download on Pro ($50) (3rd-party) | ? | ? | ? | App Store submit from web app ✔ |
| Anything | $19/mo | Expo (3rd-party) | ? | ? | ? | ? | ? (claims conflict) |
| Base44 | ~$40/mo Builder | ✘ WebView wrapper | GitHub export on Builder | ? | weak (wrapper) | ? | Downloads bundles; you upload |
| Lovable + Capacitor/Median | Lovable plan + wrapper | ✘ wrapper | ✔ web code | via plugins ? | ✔ via Capacitor | ✔ via Capacitor | You submit |
| Adalo | $36/mo | partial | ✘ lock-in (no export found) | ? (Stripe only found) | ? | ? | ✔ on paid plans |
| Bubble mobile | $42/mo | ✔ (per Bubble) | ✘ lock-in | ? | ? | ? | ✔ build infra |

- Rork Pro is the only builder with official docs confirming all three: built-in iOS build/upload with no Mac, an Android AAB pipeline, and built-in RevenueCat. That makes it the best fit for a non-developer's one-month timeline. Rork Max's native games and SwiftUI are irrelevant here because it cannot ship to Google Play.
- The credit allowance is the hidden cost. 100 credits/month on Rork Pro may not be enough to build and polish an app; the Hockey AI team produced 114 TestFlight builds. Budget for 1–2 months, or a higher Pro credit tier (third-party: up to $100/month for 500 credits).
- For an AI-wrapper or utility app, wrapped web apps (Base44, Lovable) are the highest-risk path for Apple 4.2. Avoid them unless the app already exists as a web product.

### Gaps
- The full pages of rork.com/pricing and docs.rork.com could not be loaded. Rork's support for push notifications and camera, and the exact export format for new (post-Expo) projects, were not confirmed.
- The official pricing pages for FlutterFlow, a0.dev, Vibecode, Anything, Base44, Bolt, Lovable, Adalo, Bubble and Natively were not reachable; figures come from third-party pages, often competitors. Native IAP support for a0.dev, Vibecode, Anything, Base44, Adalo and Bubble is unverified.
- Despia (a Lovable wrapper) returned no results.
- No independent (non-vendor) data was found on success or rejection rates by builder.

---

## 2. Which tools handle simple 2D casual games, and what is the simplest path to both stores?

### Takeaway
None of the AI app builders verified here is a proven route to a cross-platform casual game. Rork's "native games" feature sits on the iOS-only Max tier. The best-documented low-cost path is a **web game (Phaser, written with AI help) wrapped with Capacitor** for both stores. **Godot** is the native-engine alternative. Monetization data says games convert poorly to subscriptions, so plan on ads plus IAP (for example a "remove ads" purchase or coins).

### Cited Findings
- Rork Max (from $200/month) adds "native games", and Max apps are iOS-only and cannot be published to Google Play — [Rork docs: Subscriptions](https://docs.rork.com/introduction/subscriptions); [Rork docs: Publishing](https://docs.rork.com/faq/publishing) (search extracts)
- Phaser's official tutorial covers wrapping a finished Phaser game as an iOS and Android app with Capacitor, adding touch controls, mobile resizing and safe-area support — [Phaser: Bring your Phaser game to iOS and Android with Capacitor](https://phaser.io/tutorials/bring-your-phaser-game-to-ios-and-android-with-capacitor). A developer interviewed by Phaser (July 2026) built with Android Studio, published on Google Play, and was "caught off guard" by Google Play's testing requirements — [Phaser news, Jul 2026](https://phaser.io/news/2026/07/fuel-field-phaser-roguelite-interview)
- Godot is described as a lightweight choice for 2D, but its mobile monetization and plugin ecosystem is "less mature than Unity's" — [opper.ai roundtable](https://opper.ai/ai-roundtable/questions/which-stack-should-i-use-for-mobile-puzzle-game-def7d247) (weak source: an AI-model poll)
- Apple guideline 4.7 allows apps to offer HTML5/JavaScript mini games that are not embedded in the binary, and the developer is responsible for their compliance — [Apple App Review Guidelines 4.7](https://developer.apple.com/app-store/review/guidelines/) (fetched 2026-10-12)
- Gaming has the weakest subscription metrics in RevenueCat's 2026 report: download-to-trial 4.4%, trial-to-paid 25.0%, first-year realized LTV per payer $11.22 (lowest category) — [RevenueCat SOSA 2026 blog](https://www.revenuecat.com/blog/growth/subscription-app-trends-benchmarks-2026); [RevenueCat SOSA 2026](https://www.revenuecat.com/state-of-subscription-apps) (search extracts)
- Rewarded video is the highest-earning ad format for most app publishers, and AppLovin MAX is widely described as the default mediation for casual and hyper-casual games — [Segwise AppLovin guide](https://segwise.ai/blog/applovin-publisher-monetization-guide); [CAS.AI](https://cas.ai/blog/the-best-mobile-ad-networks/) (vendor sources)

### Inferences
- The simplest cross-platform game path for a non-coder is to have an AI agent (Claude Code or Cursor) write a Phaser game, test it in the browser, wrap it with Capacitor, and add the AdMob and IAP Capacitor plugins. A real game should face less Apple 4.2 risk than a wrapped website, because 4.2 targets apps that are just "a repackaged website".
- A game built with Rork Pro (React Native-style UI) could suit very simple puzzle or board-style games, but this was not verified.
- For games, AdMob alone is the lower-friction first step; MAX mediation adds setup work.

### Gaps
- No verified evidence was found on how well Rork Pro, a0.dev, Vibecode or FlutterFlow handle game loops or animation.
- The names and maintenance status of Capacitor AdMob/IAP plugins were not checked. Unity's 2026 pricing and runtime fees were not checked.
- No independent 2026 eCPM benchmarks for indie casual games were found.

---

## 3. Monetization stack: RevenueCat vs Superwall vs Adapty, ads (AdMob/AppLovin MAX), and store commissions

### Takeaway
All three subscription SDKs are free at launch scale. **RevenueCat** is free until $2,500 MTR (monthly tracked revenue), then 1% of all MTR. **Adapty** is free under $5,000 MTR, then 1%. **Superwall**'s Indie plan is free up to $10K of paywall-attributed revenue, then 1%. Store commission for a new small developer is effectively **15% on both stores**. Apple's Small Business Program requires enrollment. Google's new US/UK/EEA structure since June 30, 2026 is a 10% service fee plus a 5% Google Play Billing fee. Ad-network fees could not be verified from primary sources.

### Cited Findings

**RevenueCat**
- "Pay nothing for up to $2,500 in monthly tracked revenue. Then pay 1% of what you track once you hit $2,500 in MTR." The 1% applies to the **whole** MTR (docs example: $2,600 MTR gives a $26 charge). MTR is measured **before** store commission and taxes — [RevenueCat pricing](https://www.revenuecat.com/pricing); [RevenueCat billing docs](https://www.revenuecat.com/docs/welcome/set-up-revenuecat/account-management) (search extracts)
- An older free threshold of $10K MTR (TechCrunch, Series B era) is outdated — [TechCrunch](https://techcrunch.com/?p=2157127)
- RevenueCat Web supports Stripe Billing for Web Purchase Links, Web Paywalls and Funnels, and **web purchases unlock entitlements in the mobile app**. RevenueCat says it adds no fee for Web itself; processor fees apply — [RevenueCat docs: Stripe](https://www.revenuecat.com/docs/web/integrations/stripe); [RevenueCat Web feature page](https://www.revenuecat.com/feature/web) (search extracts)

**Superwall**
- Pricing page: **Indie $0/month up to $10k Monthly Attributed Revenue (MAR), then 1% of total MAR**. Startup is $49/month + 1% MAR and Scale is $199/month + 1% MAR. Entitlements, purchase APIs, webhooks and SQL access are free on all plans; only revenue attributed to Superwall paywalls is billed — [Superwall pricing](https://superwall.com/pricing) (search extract); [toolradar, checked Jun 15 2026](https://toolradar.com/tools/superwall)
- Conflict: Superwall's FAQ still describes a conversion-based model (Indie up to 250 free conversions/month, then $0.20/conversion). It appears older — [Superwall FAQ](https://superwall.com/docs/support/faq/2801653905-how-does-superwalls-pricing-work)

**Adapty**
- February 2026 announcement: the Pro plan gives "every platform feature for free" under **$5,000 MTR**, then 1% of revenue. The older $10K threshold with a $99 minimum appears superseded — [Adapty blog: new pricing 2026](https://adapty.io/blog/adapty-new-pricing-2026/) (search extract)

**Apple commission**
- Small Business Program: **15% commission on paid apps and IAP** for developers with ≤ US$1M proceeds in the prior calendar year (new developers qualify). You must enroll as Account Holder, accept the Paid Apps agreement and list Associated Developer Accounts. Proceeds are adjusted 15 days after the end of the fiscal month in which enrollment is approved. A further reduced 10% applies "for developers on the alternative terms in the EU in the App Store Small Business Program and for subscriptions after their first year". The wording is ambiguous on whether the subscription part is EU-only; Adapty's guide reads the 10% as EU-only — [Adapty SBP guide](https://adapty.io/blog/app-store-small-business-program/). Enrolled developers with fewer than 2M first-time downloads can use Apple Foundation Models on Private Cloud Compute "with no cloud API cost" — [Apple: App Store Small Business Program](https://developer.apple.com/app-store/small-business-program/) (fetched 2026-10-12; the page has no "last updated" date)
- Without the Small Business Program, the standard subscription rate is 30% in year 1 and 15% after 12 continuous months — [Adapty SBP guide](https://adapty.io/blog/app-store-small-business-program/) (third-party)

**Google Play commission (changed in 2026)**
- Official Android Developers Blog, June 2026: from **June 30, 2026 in the US, EEA and UK**, Google separates the service fee from the billing fee. The service fee starts at **10% on the first $1M** of annual earnings, whichever billing path is used, and 10% also applies to all auto-renewing subscriptions — [Android Developers Blog: Expanded billing choice and lower fees](https://android-developers.googleblog.com/2026/06/play-expanded-billing.html) (search extract)
- Secondary coverage: a **5% billing fee** applies when Google Play Billing is used in the US/UK/EEA. Rollout: Australia Sep 30, 2026; Japan and Korea Dec 31, 2026; rest of world Sep 30, 2027 — [ASO World](https://asoworld.com/en/blog/google-play-alternative-billing-lower-fees-developer-guide/); [pricepush.app "10% headline, 15% reality"](https://pricepush.app/blog/google-play-subscription-fees-2026-real-math); [wnhub.io](https://wnhub.io/news/stores-and-publishing/item-50259)
- Pre-2026 structure (still the reference outside the rollout regions): 15% on the first $1M/year for enrolled developers, and 15% for auto-renewing subscriptions regardless of earnings. Enrollment requires a payments profile and an account group — [Google Play Console Help: service fees](https://support.google.com/googleplay/android-developer/answer/10632485?hl=en) (search extract)

**Ads**
- No primary source was found for AdMob's publisher revenue share. One marketing site claims AdMob keeps 32%, which is unverified — [marketingmonk](https://www.marketingmonk.so/products/admob). A mediation vendor lists AdMob payment at Net 21 and MAX at Net 15–30 — [CAS.AI](https://cas.ai/blog/the-best-mobile-ad-networks/) (vendor; conflict of interest)
- Claims that MAX beats AdMob on rewarded and interstitial eCPMs in Tier-1 markets come only from vendors — [CAS.AI](https://cas.ai/blog/the-best-mobile-ad-networks/); [Segwise](https://segwise.ai/blog/applovin-publisher-monetization-guide)

### Inferences
- For a new app, the cheapest setup is **RevenueCat (free, with built-in Rork/FlutterFlow integrations) plus store IAP**. Its paywall builder (RevenueCat Paywalls) removes the need for Superwall at v1. Superwall's free tier is larger ($10K MAR) and worth a look later for paywall A/B testing.
- Effective commission for a US/UK/EEA indie in 2026: Apple 15% (with SBP enrollment) and Google about 15% (10% + 5% billing). **Enroll in Apple's SBP before the first sale**, because the rate change is not retroactive within the month.
- At $1,000/month gross revenue, all three subscription SDKs cost $0.

### Gaps
- The full official pricing pages for RevenueCat, Superwall and Adapty could not be loaded (search extracts only).
- AdMob's official revenue share, AppLovin MAX fees, and 2026 eCPM benchmarks were not verified.
- The exact Google Play terms outside the US/UK/EEA during the transition were not fully confirmed.

---

## 4. Subscription benchmarks (RevenueCat "State of Subscription Apps" 2026)

### Takeaway
RevenueCat's 2026 report covers 115,000+ apps, $16B+ revenue and 1B+ transactions, mostly 2025 performance. Key figures:
- **Trial-to-paid median: about 32%.**
- **Download-to-trial median: 4–9% by category.**
- **Hard paywalls convert about 5× better than freemium by Day 35:** 10.7% vs 2.1% download-to-paid.
- Median prices: weekly $5.99, monthly $10, yearly $34.80.
- The typical app earns only about $72/month one year after launch.

### Cited Findings
(All from RevenueCat's 2026 report and its summary blog: [State of Subscription Apps 2026](https://www.revenuecat.com/state-of-subscription-apps); [SOSA 2026 in 10 minutes (blog)](https://www.revenuecat.com/blog/growth/subscription-app-trends-benchmarks-2026). Search extracts; full PDF not loaded.)
- Sample: 115,000+ apps, $16B+ revenue, 1B+ transactions; 2025 is the target period.
- **Trial-to-paid, global median:** 32.0% iOS and 32.5% Google Play.
- **Trial-to-paid by trial length:** 17–32 days 42.5% (top quartile >59.4%); 5–9 days 37.4%; ≤4 days 25.5%. In the 2025 report, 17–32-day trials had a 45.7% median.
- **Trial-to-paid by region:** North America 34.2%, Asia-Pacific 31.9%, Western Europe 29.7%, India/SEA 15.2%.
- **Trial-to-paid by category:** Travel 43.5%, Health & Fitness 37.7%, Gaming 25.0%, Photo & Video 22.2%.
- **Download-to-trial (trial started within 30 days of install), median by category:** Business 9.1%, Health & Fitness 6.9%, Education 6.5%, Utilities 6.5%, Gaming 4.4%. **By price point:** high-priced 8.9%, mid 5.4%, low 4.4%.
- **Hard paywall vs freemium:** median Day-35 conversion 10.7% vs 2.1%. Hard-paywall conversion fell from 12.1% in the 2025 report while freemium stayed at 2.1%. Revenue per install at Day 60: **$3.09 hard vs $0.38 freemium**. Annual-plan retention after one year is nearly equal: freemium 28% vs hard 27%.
  - Metric-definition conflict: RevenueCat's blog wording is ambiguous ("trial-to-paid"), while [Admiral Media](https://admiral.media/app-paywall-optimization/) and [PricePush](https://pricepush.app/blog/trial-to-paid-conversion-rate-benchmarks) describe the 10.7% / 2.1% as download-to-paid. Because the overall trial-to-paid median is about 32%, the 10.7% / 2.1% figures are most consistent with **download-to-paid**.
- **AI apps:** median download-to-paid 2.4% (top quartile >4.8%) vs non-AI 2.0%. AI apps earn 41% more revenue per payer but churn 30% faster.
- **Pricing medians:** weekly $5.99 and monthly $10 (both flat). Yearly rose from $31.60 to $34.80. Plan mix varies by category: weekly is 4%–47% of sales, yearly 13%–77%.
- **Revenue reality:** cross-category median monthly revenue one year after launch is about **$72**. Photo & Video is highest at $124 and Travel lowest at $35. First-year realized LTV per payer: Health & Fitness $35.64, Business $35.48, Gaming $11.22.
- Trial cancellations: 55% of all 3-day-trial cancellations happen on Day 0 — [RevenueCat: free trial length](https://www.revenuecat.com/blog/growth/free-trial-length) (search extract)

### Inferences
- Illustrative funnel for a utility or AI scanner using medians: 1,000 installs × about 6.5% download-to-trial ≈ 65 trials × about 32% ≈ 21 paying users. With a hard paywall, Day-35 download-to-paid is about 10.7%, roughly 107 payers per 1,000 installs at the median, and $3.09 revenue per install by Day 60. A hard paywall with a trial is the evidence-backed default for AI/utility clones.
- The $72/month median one year after launch is a sobering base rate. Most apps earn little, so the ~$1,000 budget should go mostly into distribution and testing, not tooling.
- AI apps churn faster and carry per-use API costs. Weekly or annual plans, plus usage caps on free trials, protect margins (see Q5 API costs).

### Gaps
- The full 2026 PDF was not loaded, so exact median revenue by category at specific milestones (for example the share reaching $1K or $10K MRR) and refund rates were not captured.
- No AI-app-specific trial-to-paid median was found.
- The exact definition of the 10.7% / 2.1% metric should be checked in the report itself.

---

## 5. Costs: developer fees, AI API cost per call, backend free tiers, and protecting API keys

### Takeaway
Fixed store fees are **$99/year for Apple and $25 one-time for Google**. A typical AI vision call (one photo plus a short answer) costs roughly **$0.0003 to $0.006**, depending on the model; Anthropic's Claude Haiku 5.5 is the cheapest verified option. **Supabase's free tier** (500K Edge Function invocations/month) or **Cloudflare Workers' free tier** (100K requests/day) can host a secure AI proxy for $0. **Never ship AI API keys in the app**: Expo states that `EXPO_PUBLIC_` variables are readable in plain text.

### Cited Findings

**Store fees**
- Apple Developer Program: **US$99/year**, in local currency where available. Enrollment needs an Apple Account with 2FA. Organizations need a D-U-N-S number. Membership auto-renews — [Apple Developer: Membership details / Enrollment](https://developer.apple.com/programs/whats-included/); [Apple enrollment help](https://developer.apple.com/help/account/membership/program-enrollment/) (search extracts)
- Google Play: **US$25 one-time registration fee**. Organization accounts need a D-U-N-S number, which is free from Dun & Bradstreet. Personal accounts must verify access to an Android device before publishing — [Play Console Help: Get started](https://support.google.com/googleplay/android-developer/answer/6112435?hl=en); [Required info](https://support.google.com/googleplay/android-developer/answer/13628312?hl=en) (search extracts)

**AI API pricing** (per 1M tokens)
- **Anthropic:**
  - Claude Haiku 5.5: **$0.10 input / $0.50 output** for prompts ≤100K tokens.
  - Claude Haiku 4.5: $1 / $5.
  - Claude Sonnet 5.5: $2 / $10.
  - Claude Opus 5.5: $4 / $20.
  - Source: Anthropic Claude API reference model table (cached 2026-10-06, via the bundled claude-api skill); live page: [Anthropic pricing](https://platform.claude.com/docs/en/about-claude/pricing)
- **Anthropic image tokens:** an image costs ⌈width/28⌉ × ⌈height/28⌉ visual tokens. A 1000×1000 image = **1,296 tokens**. Example from the docs: at Haiku 4.5's $1/M, a 1000×1000 image costs about $1.30 per thousand images — [Anthropic Vision docs](https://platform.claude.com/docs/en/build-with-claude/vision) (fetched 2026-10-12)
- **Google Gemini:**
  - Gemini 3.8 Flash: introductory **$0.75 input / $3.75 output** through Dec 31, 2026, then $1.50 / $7.50 from Jan 1, 2027.
  - Gemini 3 Flash Preview input: $0.50 (text/image/video).
  - Gemini 2.5 Flash input: $0.30.
  - Gemini 3.1 Flash-Lite input: $0.25.
  - Source: [Gemini Developer API pricing](https://ai.google.dev/gemini-api/docs/pricing); [What's new in Gemini 3.8 Flash](https://ai.google.dev/gemini-api/docs/latest-model) (search extracts)
  - A forum reports a pricing discrepancy for Gemini 3.1 Flash Image input — [Google AI forum](https://discuss.ai.google.dev/t/gemini-3-1-flash-image-preview-inconsistent-pricing-between-ai-studio-and-api-docs/127608)
- **OpenAI:**
  - **GPT-5.4 nano: $0.20 input / $1.25 output.**
  - GPT-5.4 mini: $0.75 / $4.50.
  - GPT-5 mini ($0.25/$2.00) and GPT-5 nano ($0.05/$0.40) are marked deprecated.
  - The nano page recommends "GPT-5.6 Luna" for new cost-sensitive work (price not captured).
  - Source: [OpenAI: Introducing GPT-5.4 mini and nano](https://openai.com/index/introducing-gpt-5-4-mini-and-nano/); [GPT-5 nano model page](https://developers.openai.com/api/docs/models/gpt-5-nano) (search extracts)

**Backend free tiers**
- **Supabase Free:**
  - 500 MB database per active project; the project goes read-only above that.
  - 2 active projects.
  - **50,000 MAU** for auth.
  - 1 GB file storage and 5 GB egress.
  - Nano shared compute, no automatic backups.
  - **500,000 Edge Function invocations/month.** Pro/Team include 2M, then $2 per million.
  - **Free projects pause after 1 week of inactivity**, based on database activity. A warning email is sent first. Paused projects can be restored within 1 year per current docs; an older changelog said 90 days.
  - Sources: [Supabase pricing](https://supabase.com/pricing); [Supabase: Project pausing](https://supabase.com/docs/guides/platform/free-project-pausing); [Supabase: Database size](https://supabase.com/docs/guides/platform/database-size); [Supabase: Edge Function invocations](https://supabase.com/docs/guides/platform/manage-your-usage/edge-function-invocations) (search extracts)
- **Firebase:**
  - **Cloud Functions require the Blaze (pay-as-you-go) plan with a card.** Blaze's free Functions quota is 2M invocations, 400K GB-s, 200K CPU-s and 5 GB egress per month.
  - Spark-plan quota overruns shut the product off for the rest of the month.
  - App Check is free on both plans.
  - Spend caps for Cloud Functions are available on Blaze.
  - Sources: [Firebase pricing plans](https://firebase.google.com/docs/projects/billing/firebase-pricing-plans); [Firebase FAQ](https://firebase.google.com/support/faq) (search extracts)
- **Cloudflare Workers Free:**
  - **100,000 requests/day**, resetting at midnight UTC (error 1027 when exceeded).
  - **10 ms CPU per request**. Time waiting on `fetch()` calls does **not** count, which fits an AI proxy well.
  - 50 subrequests per invocation.
  - Static-asset requests are free and unlimited.
  - Sources: [Cloudflare Workers limits](https://developers.cloudflare.com/workers/platform/limits/); [Workers pricing](https://developers.cloudflare.com/workers/platform/pricing/) (search extracts)

**API key protection**
- Expo: "Do not store sensitive info, such as private keys, in EXPO_PUBLIC_ variables. These variables will be visible in plain-text in your compiled application." Expo inlines `process.env.EXPO_PUBLIC_*` at build time. Secrets belong in server-side code such as Expo API routes, which are not in the client bundle — [Expo: Environment variables](https://docs.expo.dev/guides/environment-variables/); [Expo Router API routes](https://docs.expo.dev/router/web/api-routes/) (search extracts)
- Google Play's July 15, 2026 policy announcement clarified that User Data requirements also apply to **third-party AI integrations** — [Play Console Help: Policy announcement Jul 15, 2026](https://support.google.com/googleplay/android-developer/answer/17134731) (search extract)

### Inferences
- **Worked per-call estimate** for one AI scan: a 1000×1000 photo (1,296 tokens) plus about 200 prompt tokens is about 1,500 input tokens, with about 300 output tokens. The Gemini and OpenAI image-token counts are assumed equal to Anthropic's for comparison only; their tokenizers differ.

| Model | Cost per scan | Cost per 1,000 scans | Cost per 10,000 scans |
|---|---|---|---|
| Claude Haiku 5.5 | ≈ $0.0003 | ≈ $0.30 | ≈ $3 |
| GPT-5.4 nano | ≈ $0.0007 | ≈ $0.68 | ≈ $7 |
| Gemini 3.8 Flash (intro rate) | ≈ $0.0023 | ≈ $2.25 | ≈ $23 |
| GPT-5.4 mini | ≈ $0.0025 | ≈ $2.50 | ≈ $25 |
| Claude Haiku 4.5 | ≈ $0.003 | ≈ $3.00 | ≈ $30 |
| Claude Sonnet 5.5 | ≈ $0.006 | ≈ $6.00 | ≈ $60 |

  Even the priciest option is small next to a $5.99/week subscription, but free trials and abuse can multiply calls. Add per-user rate limits in the proxy.
- **Recommended key-protection pattern:**
  1. The app calls your own endpoint: a Supabase Edge Function or a Cloudflare Worker.
  2. The endpoint holds the AI key as a server secret and enforces limits, for example free users get N scans per day.
  3. Optionally, it checks the RevenueCat entitlement before allowing premium calls.
  4. It forwards the request to the AI provider.
- Supabase's Edge Function quota (500K/month) and Cloudflare's (about 3M/month at 100K/day) both cover a launch month for $0.
- **Firebase is less attractive** for a $0 proxy because Functions need Blaze billing. That is cheap in practice but requires a card and spend caps.

### Gaps
- The live Anthropic pricing page was not loaded (the cached reference table is from 2026-10-06). Haiku 5.5's unusually low price should be re-checked before budgeting.
- Gemini image-token counting for Gemini 3.x and output prices for Gemini 3.1 Flash-Lite were not captured, nor was the price of OpenAI's "GPT-5.6 Luna".
- Supabase Pro's monthly price was not verified this session (search budget exhausted).
- How long Apple's individual developer enrollment approval takes was not verified.

---

## 6. Store review risks for AI-built clone apps (Apple 4.1, 4.2, 4.3, 5.1, 3.1, AI rules; Google Play AI-content and Families policies)

### Takeaway
The big Apple risks for a cloned AI or utility app:
- **4.3(b) spam**: "indistinguishable from what's already widely available", plus a named list of saturated categories.
- **4.1 copycats**: no copying another app's name, UI, icon or brand.
- **4.2 minimum functionality**: thin wrappers.
- **2.1 completeness**: crashes, broken links, an unreachable paywall. This is the largest rejection category by volume.
- **5.1.2(i)**: explicit consent before sending personal data to third-party AI.
- **3.1.x**: IAP rules and required subscription disclosures.

Google Play requires in-app reporting or flagging in generative-AI apps. It applies strict Families rules (certified ad SDKs only, no ad ID) if the app targets children.

### Cited Findings

**Apple App Review Guidelines** (all fetched 2026-10-12 from [developer.apple.com/app-store/review/guidelines](https://developer.apple.com/app-store/review/guidelines/); the page shows no "last updated" date)
- **4.1 Copycats:** "(a) Come up with your own ideas… Don't simply copy the latest popular app on the App Store, or make some minor changes to another app's name or UI and pass it off as your own." (b) Impersonation "may result in removal from the Apple Developer Program." "(c) You cannot use another developer's icon, brand, or product name in your app's icon or name, without approval."
- **4.2 Minimum Functionality:** "Your app should include features, content, and UI that elevate it beyond a repackaged website. If your app is not particularly useful, unique, or 'app-like,' it doesn't belong on the App Store." 4.2.2: apps shouldn't primarily be "marketing materials, advertisements, web clippings, content aggregators, or a collection of links."
- **4.2.6:** "Apps created from a commercialized template or app generation service will be rejected unless they are submitted directly by the provider of the app's content."
- **4.3(a):** "Don't create multiple Bundle IDs of the same app…"
- **4.3(b) (current wording):** "Don't submit apps that are indistinguishable from what's already widely available. Opportunistically creating variants of existing app categories or popular apps degrades App Store discovery… Certain kinds of apps, such as dating, flashlight, sound effects, wallpaper, simple timers, and fortune telling, are well established on the App Store and we will not accept new submissions unless they offer a meaningfully different or improved experience… Repeated submissions of this kind may lead to removal from the Apple Developer Program." A blog claims this rewording dates from a June 9, 2026 update — [appdrift.co](https://appdrift.co/blog/apple-rejecting-vibe-coded-apps) (date unverified)
- **2.5.2:** apps may not "download, install, or execute code which introduces or changes features or functionality of the app." This is the basis for Apple blocking or removing on-device vibe-coding apps (Replit, Vibecode, Anything) in 2026; Apple says it is enforcing violations, not banning vibe coding — [MacRumors](https://macrumors.com/2026/03/30/apple-pulls-vibe-coding-app/); [storyboard18](https://storyboard18.com/digital/apple-removes-anything-from-app-store-says-violations-not-vibe-coding-behind-crackdown-93790.htm)
- **5.1.2(i):** "You must clearly disclose where personal data will be shared with third parties, including with third-party AI, and obtain explicit permission before doing so." Apps also may not require users to enable push, location or tracking to access functionality.
- **5.1.1(i):** third parties that receive user data (analytics, ad networks, SDKs) must provide equal protection to your privacy policy.
- **5.1.1(v):** "If your app doesn't include significant account-based features, let people use it without a login. If your app supports account creation, you must also offer account deletion within the app."
- **1.2 User-generated content:** must include filtering, a reporting mechanism with timely responses, user blocking, and published contact information.
- **3.1.1:** features or content must be unlocked with in-app purchase. 3.1.2(a): an auto-renewing subscription must last **at least seven days**. 3.1.2(c): "Before asking a customer to subscribe, you should clearly describe what the user will get for the price."
- **4.7:** HTML5/JS mini games, chatbots and plug-ins are allowed, but the developer is responsible for their compliance.

**Other Apple findings**
- Age ratings: Apple's new questionnaire (new 13+/16+/18+ tiers) had to be answered by **January 31, 2026**, or app updates could be blocked. It asks about capabilities including AI assistants or chatbots — [9to5Mac](https://9to5mac.com/?p=1011484); [iGeeksBlog](https://www.igeeksblog.com/apple-app-store-age-ratings/) (secondary)
- Rejection volumes (secondary write-up of Apple transparency data): in 2025, 9,100,620 submissions were reviewed and 2,093,244 rejected. The "Performance" category, which covers 2.1 app completeness, had 1,354,418 rejections, more than all other categories combined. Apple states that over 40% of unresolved issues relate to App Completeness — [trysonar.app](https://trysonar.app/blog/app-store-rejection-common-reasons-and-fixes) (secondary; Apple's report not loaded)
- Common 2.1 triggers per practitioners: missing demo login in review notes, crashes, paywalled features the reviewer cannot reach, placeholder text, dead privacy/support/terms URLs — [trysonar.app](https://trysonar.app/blog/app-store-rejection-common-reasons-and-fixes); [drobinin.com](https://drobinin.com/consulting/app-store-review/why-apple-keeps-rejecting-your-app/) (practitioner)
- Builder-specific warning: Rork says apps will be rejected without a privacy policy, terms and a visible EULA — [Rork docs](https://docs.rork.com/payment-guides/revenuecat-copied-1) (search extract)
- Wrapper rejections (4.2): mirroring the mobile site, needing a constant connection, no native navigation, blank screen offline — [superappp.com](https://www.superappp.com/blog/can-lovable-make-mobile-apps-how-to-publish-a-lovable-app-to-the-app-store) (vendor)

**Google Play**
- **AI-Generated Content policy:** covers generative AI apps (text chatbots, text-to-image, voice/video of real people). Apps must include **in-app reporting or flagging of offensive content without exiting the app** and must prevent generation of restricted content. Limited-scope AI apps (hosting only, or summarizing non-AI content) are currently excluded — [Play Console Help: AI-Generated Content](https://support.google.com/googleplay/android-developer/answer/13985936?hl=en); [Understanding the AI-Generated Content policy](https://support.google.com/googleplay/android-developer/answer/14094294?hl=en) (search extracts)
- An August 2026 Android Developers Blog post describes enhanced requirements for genAI apps to prevent non-consensual intimate content and "nudify" media — [Android Developers Blog, Aug 2026](https://android-developers.googleblog.com/2026/08/ensuring-safety-genai-preventing-non-consensual-intimate-content.html)
- The July 15, 2026 announcement says User Data requirements apply to third-party AI integrations. The target API level deadline was **August 31, 2026** — [Policy announcement Jul 15, 2026](https://support.google.com/googleplay/android-developer/answer/17134731) (search extract)
- **Families policy:**
  - Child-only apps must use only **Families Self-Certified Ads SDK** versions; mixed-audience apps need a neutral age screen.
  - No interest-based ads or remarketing to children.
  - No transmission of the advertising ID and similar identifiers from children or users of unknown age.
  - Child-only apps may not request precise location.
  - The self-certified SDK program is **not accepting new applicants**.
  - A July 2026 preview bars anonymous chat apps from targeting children.
  - Sources: [Families Self-Certified Ads SDK Program](https://support.google.com/googleplay/android-developer/answer/9900633?hl=en); [Preview: Families Policies](https://support.google.com/googleplay/android-developer/answer/17122218); [AdMob Families compliance](https://support.google.com/admob/answer/6223431?hl=en) (search extracts)

### Inferences
**Pre-submission checklist** (no AI-built-app rejection statistics exist; these items follow from the guideline text and practitioner reports above):
- Avoid the six named saturated categories unless the app clearly differs.
- Never reuse a competitor's name or icon, or near-copies of either.
- Add at least one distinct feature or angle to answer 4.3(b).
- Give the reviewer a working path to the paywall and a sandbox account.
- Host live privacy, terms and EULA URLs.
- Show a consent screen naming the AI provider before the first upload of photos or personal data (5.1.2(i)).
- Add a "report this result" button in AI output screens. This satisfies Google Play's AI-content rule and helps with Apple 1.2 if the app has UGC.
- Do not target children. Families rules sharply limit ads and AI features.
- The 2.5.2 crackdown hit the builder companies' own iOS apps, not apps built with them. It does mean the user should not build an "AI app generator" app.
- 4.2.6 is satisfied when the user submits under their own developer account, which Rork and Vibecode require anyway.

### Gaps
- Apple's 2025 App Store Transparency Report was not loaded directly, so the rejection counts are secondary.
- The text after section 5.3 of the guidelines was not read; the fetch truncated at about 100K characters.
- No quantitative data exists on rejection rates specific to AI-built apps.
- Whether EAS Update / OTA JavaScript updates are treated as compliant with 2.5.2 was not verified this session.

---

## 7. Google Play closed-testing requirement for new personal accounts and its effect on a 1-month timeline

### Takeaway
A **new personal developer account must run a closed test with at least 12 testers who stay opted in for at least the last 14 continuous days** before it can apply for production access. Until then, Production and Pre-registration are disabled. Production access is then reviewed. On a 30-day plan, the Android closed test must start by about **day 7–10**, and Android production launch realistically lands in **week 4 or later**. iOS can ship earlier.

### Cited Findings
- Official rule: newly created personal developer accounts must run a closed test with **a minimum of 12 testers opted in for at least the last 14 days continuously**, then apply for production access from the Dashboard in Play Console. Production and Pre-registration are disabled until then — [Play Console Help: App testing requirements for new personal developer accounts](https://support.google.com/googleplay/android-developer/answer/14151465) (search extract; page not loadable in full)
- Scope: applies to personal accounts created after November 2023; sources disagree on Nov 1 vs Nov 13, 2023. Google's page does not name organization accounts, and sites calling them exempt are inferring this — [extendsclass](https://extendsclass.com/blog/google-plays-closed-testing-requirement-what-developers-need-to-know-in-2026); [choicely](https://www.choicely.com/blog/google-play-12-tester-rule) (third-party)
- Unverified third-party claims: the 14-day clock resets if active testers drop below 12. Google's text only requires testers to be "opted in" and does not require them to install or use the app; claims about session-length tracking come mainly from companies selling testers — [extendsclass](https://extendsclass.com/blog/google-plays-closed-testing-requirement-what-developers-need-to-know-in-2026); [levelup.gitconnected "12-tester tax"](https://levelup.gitconnected.com/the-12-tester-tax-google-plays-closed-testing-rule-is-quietly-killing-solo-devs-2cea83c2e338)
- Rork can push signed Android AABs to the internal testing track, but you create the app and manage releases in Play Console — [Rork docs: Publishing](https://docs.rork.com/faq/publishing) (search extract)
- Organization accounts need a D-U-N-S number, which is free — [Play Console Help](https://support.google.com/googleplay/android-developer/answer/13628312?hl=en) (search extract)

### Inferences
**Suggested 30-day timeline:**
- **Day 1:** pay for both developer accounts. Enroll in Apple's Small Business Program. Start recruiting 15+ Android testers (friends, a Discord or Reddit community, or tester-exchange groups), buffering above 12.
- **Days 2–7:** build the MVP. Upload the **first working Android build to a closed track by about day 7**, even if unfinished, to start the 14-day clock. Later builds can update the same track.
- **Days 7–21:** keep at least 12 testers opted in while iterating. Submit iOS around days 14–20.
- **About day 21:** apply for Android production access.
- **About days 22–30:** Android production review, then launch.

**Other implications:**
- If the clock slips, Android launches in month 2. Plan iOS-first marketing.
- Registering as an organization (D-U-N-S) may avoid the requirement, but D-U-N-S issuance time is unverified and may itself take weeks. Not recommended for a 1-month plan without checking first.

### Gaps
- The full Google help page could not be loaded. The production-access review duration (third parties often cite up to 7 days) was not verified.
- The exact account-creation cutoff date was not resolved (Nov 1 vs Nov 13, 2023).
- Whether organization accounts are officially exempt was not confirmed from Google's own text.

---

## 8. User's proposed stack: keep / swap / skip (smallest stack that fully works for a 1-month v1)

### Takeaway
**Keep:**
- **GitHub**: free, and needed for code ownership.
- **Supabase**: only for an AI-proxy Edge Function and, optionally, storage.
- **PostHog**: optional; free tier with React Native/Flutter SDKs.

**Swap:**
- **Stripe → Apple/Google IAP via RevenueCat.** IAP is still mandatory for in-app digital unlocks. US link-outs to Stripe are an optional add-on with unsettled fees.
- **Cloudflare hosting → just a free static page** for privacy/terms/landing. Use a Cloudflare Worker *or* a Supabase Edge Function as the AI-key proxy, not both.

**Skip for v1:**
- **MongoDB**: Supabase covers it with built-in auth and functions.
- **Supabase Auth**: an anonymous, no-account app avoids login, account-deletion and Sign in with Apple obligations.
- **Resend**: no accounts means no email.

**Frontend:** **React Native via Expo** (what Rork, a0.dev, Vibecode and Bolt output), or Flutter if using FlutterFlow. Not Swift-only (Rork Max), because it cannot ship to Google Play.

### Cited Findings

**(1) Stripe vs Apple IAP / Google Play Billing**
- **Apple 3.1.1:** features and content must be unlocked with IAP.
- **Apple 3.1.1(a) (current):** external-purchase entitlements "are not required for developers to include buttons, external links, or other calls to action in their **United States storefront** apps". In all other storefronts, apps may not include such calls to action, except through regional entitlements.
- **Apple 3.1.3:** apps "cannot, within the app, encourage users to use a purchasing method other than in-app purchase, except for apps on the United States storefront…"
- **Apple 3.1.3(b) Multiplatform:** web-bought access can be honored in-app "provided those items are also available as in-app purchases within the app."
- Source for the four items above: [Apple App Review Guidelines](https://developer.apple.com/app-store/review/guidelines/) (fetched 2026-10-12)
- Apple's FY2026 10-Q:
  - The Ninth Circuit upheld the 2025 injunction in part but lets Apple **require parity in size, form and placement between IAP and links**, and held that Apple **can charge some commission** on link-out purchases. The case was remanded to the district court.
  - Apple petitioned the Supreme Court on May 21, 2026, and **cert was granted June 30, 2026** (on the civil-contempt standard).
  - Source: [Apple Form 10-Q (quarter ended Jun 27, 2026)](https://www.sec.gov/Archives/edgar/data/0000320193/000032019326000020/aapl-20260627.htm) (search extract)
  - Reported grant dates differ: June 30 per the 10-Q and [iClarified](https://www.iclarified.com/101339/supreme-court-to-hear-apples-appeal-of-app-store-contempt-ruling), July 2 per [beancount.io](https://beancount.io/blog/2026/07/11/apple-app-store-external-purchase-links-accounting-guide).
  - Commission rate: reported as 0% currently. Apple has proposed 15% standard / 10% renewals / **5% for Small Business Program apps**, pending court approval — [beancount.io](https://beancount.io/blog/2026/07/11/apple-app-store-external-purchase-links-accounting-guide); [Subscription Insider](https://www.subscriptioninsider.com/blog/apple-proposes-15-year-one-link-out-fee-10-on-subscription-renewals)
  - RevenueCat: "most apps are still required to also offer In-App Purchases", and it treats the US link-out rate as 0% pending litigation — [RevenueCat: Can you use Stripe for IAP?](https://www.revenuecat.com/blog/engineering/can-you-use-stripe-for-in-app-purchases); [RevenueCat: App Store fees](https://www.revenuecat.com/blog/engineering/app-store-fees) (search extracts)
- **Google Play (US):**
  - Google's help page says a new Epic settlement was entered March 4, 2026. US developers enrolled in external content links / alternative billing "will need to report transactions… and pay the relevant service fees starting on **October 1, 2026**" — [Play Console Help 15582165](https://support.google.com/googleplay/android-developer/answer/15582165?hl=en) (search extract)
  - Reported fee levels: external payments 10% for auto-renewing subscriptions and 20% for other digital content (10% within the first $1M for eligible developers). External content links add a per-install fee within 24h of the click: **$2.85 for apps, $3.65 for games** — [Notebookcheck](https://www.notebookcheck.net/Google-cuts-Play-Store-fees-as-Epic-settlement-reshapes-Android-app-payments.1243278.0.html) (secondary)
  - Conflicting report: Appcharge says the settlement was withdrawn and US links remain at 0% — [Appcharge](https://appcharge.com/blog/epic-v-google-the-settlement-is-off-the-table) (date unclear)
- **RevenueCat can combine IAP with Stripe web checkout:**
  - Stripe Billing powers RevenueCat Web Purchase Links, Web Paywalls and Funnels, and entitlements unlock in the app.
  - A paywall "web purchase button" can send US iOS users to Stripe checkout. In the US storefront the SDK does not request an Apple token, so these purchases are not reported to Apple.
  - Source: [RevenueCat docs: App-to-web purchases](https://www.revenuecat.com/docs/tools/paywalls/creating-paywalls/web-purchase-button); [RevenueCat docs: Stripe](https://www.revenuecat.com/docs/web/integrations/stripe) (search extracts)
  - RevenueCat's marketing FAQ says US app-to-web requires enrollment in an approved program such as Apple's External Purchase Links. That partly conflicts with 3.1.1(a)'s "not required … in their United States storefront apps" — [RevenueCat Web](https://www.revenuecat.com/feature/web)

**(2) Supabase vs MongoDB Atlas**
- **Supabase Free:** 500 MB database per project, 2 active projects, 50K auth MAU, 1 GB storage, 5 GB egress, 500K Edge Function invocations, no backups. **Pauses after 1 week of inactivity**, judged by database activity ("a few user requests to the database each day" prevents it). Paid projects never pause — [Supabase pricing](https://supabase.com/pricing); [Supabase project pausing](https://supabase.com/docs/guides/platform/free-project-pausing) (search extracts)
- **MongoDB Atlas Free (M0):** 512 MB storage, shared RAM/vCPU, "free forever", up to 100 operations/second, **no backups**, one free cluster per project. Flex clusters are capped at **$30/month** with 5 GB. M2/M5 and Serverless are no longer supported (Jan 2026 docs note) — [MongoDB pricing](https://www.mongodb.com/pricing); [Atlas Flex costs](https://www.mongodb.com/docs/atlas/billing/atlas-flex-costs/); [Atlas limits](https://www.mongodb.com/docs/atlas/reference/atlas-limits/) (search extracts)

**(3) Supabase Auth vs no-account app; Sign in with Apple**
- Apple 5.1.1(v): let people use the app without login if there are no significant account-based features. If accounts exist, in-app account deletion is required — [Apple guidelines](https://developer.apple.com/app-store/review/guidelines/) (fetched)
- **Apple 4.8 Login Services:** apps using a third-party or social login (Google Sign-In, Facebook, etc.) for the primary account "must also offer as an equivalent option another login service" that:
  - limits data to name and email,
  - lets users keep their email private, and
  - does not collect interactions for ads without consent.

  This is not required if the app "exclusively uses your company's own account setup and sign-in systems" (for example email/password or OTP) — [Apple guidelines 4.8](https://developer.apple.com/app-store/review/guidelines/) (fetched)
- Supabase Auth free tier: 50,000 MAU — [Supabase pricing](https://supabase.com/pricing) (search extract)

**(4) Cloudflare's role**
- Cloudflare Workers Free: 100K requests/day, 10 ms CPU/request (I/O wait excluded), 50 subrequests. Static-asset requests are free and unlimited, and Pages Functions are billed as Workers — [Cloudflare Workers limits](https://developers.cloudflare.com/workers/platform/limits/); [Workers pricing](https://developers.cloudflare.com/workers/platform/pricing/) (search extracts)
- Supabase Edge Functions: 500K invocations/month free — [Supabase docs](https://supabase.com/docs/guides/platform/manage-your-usage/edge-function-invocations) (search extract)

**(5) Resend**
- Free plan: **3,000 emails/month, 100/day** (UTC day), **3 verified domains** (changelog Aug 25, 2026), 1,000 marketing contacts. Pro: $20/month for 50K emails — [Resend pricing](https://resend.com/pricing); [Resend quotas](https://resend.com/docs/knowledge-base/account-quotas-and-limits); [Resend changelog: three domains](https://resend.com/changelog/three-domains-on-the-free-tier) (search extracts)

**(6) PostHog**
- Free monthly allowance: **1M analytics events**, 5K session replays (PostHog's comparison page says 2,500 mobile), 1M feature-flag requests. It resets monthly. Events beyond the free plan are dropped. Replays are kept 1 month — [PostHog pricing](https://posthog.com/pricing); [PostHog: best mobile session replay tools](https://posthog.com/compare/best-mobile-app-session-replay-tools) (search extracts)
- SDKs: **React Native** (session replay needs SDK ≥3.2.0; **Expo Go is not supported**, use a development build) and **Flutter** (replay needs SDK ≥4.7.0 with manual init). Both record in screenshot mode — [PostHog: Mobile session replay](https://posthog.com/docs/session-replay/mobile); [React Native replay install](https://posthog.com/docs/session-replay/installation/react-native); [Flutter docs](https://posthog.com/docs/libraries/flutter) (search extracts)

**(7) GitHub**
- Rork supports GitHub sync and export for Expo projects — [Rork docs](https://docs.rork.com/expo). FlutterFlow's GitHub integration starts on Growth ($80/month first seat) — [nocode.mba](https://nocode.mba/articles/flutterflow-pricing) (third-party). Base44 GitHub export starts on Builder — [Appy Pie](https://www.appypie.com/blog/?p=2795745) (third-party)

### Inferences

| Proposed component | Verdict for v1 | Why |
|---|---|---|
| Frontend framework (user lets us choose) | **React Native (Expo), via Rork Pro or Expo + AI agent** | Both stores from one codebase. Rork, a0.dev, Vibecode and Bolt all output it. RevenueCat and PostHog have RN SDKs. Rork Max (SwiftUI) can't publish to Google Play. FlutterFlow (Flutter) is an acceptable alternative. |
| Backend/DB: Supabase or MongoDB | **Keep Supabase (minimal use); skip MongoDB** | Supabase bundles DB, auth, storage and Edge Functions; MongoDB Atlas M0 is only a database. A simple scanner, habit app or game can keep history on-device, so Supabase may be needed only for the AI proxy. Pre-launch inactivity pausing is a nuisance, not a blocker: a live app with daily DB traffic doesn't pause, and the warning email arrives first. |
| Auth: Supabase Auth | **Skip for v1** | No-account apps avoid 5.1.1(v) account deletion, 4.8 Sign in with Apple, password reset emails (and thus Resend), and extra privacy disclosures. RevenueCat purchases work with store restore. If cross-device sync is needed later, add Sign in with Apple + email OTP. |
| Hosting: Cloudflare | **Swap to a minimal role** | A mobile app needs no web hosting except a public privacy policy, terms/EULA and support/landing URL (Cloudflare Pages static: free). Pick **one** proxy platform: a Supabase Edge Function if already using Supabase, otherwise a Cloudflare Worker (100K/day free; fetch wait doesn't count toward CPU). |
| Payments: Stripe | **Swap to Apple IAP + Google Play Billing via RevenueCat** | 3.1.1 still requires IAP for digital unlocks, and US link-outs must be in addition to IAP (parity rules). Apple's link-out commission is unsettled in court. Google's US external-link fees start Oct 1, 2026 with a per-install fee. RevenueCat is free under $2.5K MTR and can add Stripe web checkout later without a rewrite. |
| Email: Resend | **Skip for v1** | Without accounts there are no transactional emails. The free tier (3K/month, 100/day) is there if needed later. |
| Analytics: PostHog | **Keep (optional)** or defer | Free 1M events/month with an RN SDK. Store consoles plus RevenueCat charts cover the minimum. Replay needs an Expo development build, which Rork and EAS already produce. Disclose it in privacy labels. |
| Code: GitHub | **Keep** | Free. Protects against builder lock-in (Rork GitHub sync). |

**Smallest stack that fully works:**
- **Builder:** Rork Pro, or Expo + Claude Code / Cursor.
- **RevenueCat:** IAP and subscriptions.
- **One serverless proxy** holding the AI key and enforcing rate limits: Supabase Edge Function or Cloudflare Worker.
- **Static legal/support page:** Cloudflare Pages.
- **GitHub.**
- **Optional:** PostHog.

### Gaps
Not verified this session (search budget exhausted):
- Supabase Pro's monthly price.
- Supabase Auth's anonymous sign-in feature.
- RevenueCat's anonymous App User ID behavior (believed to support no-login apps).
- Cloudflare Workers paid-plan price.

Unresolved conflicts:
- The Google Play US external-link fee status (Google's help page says fees from Oct 1, 2026; Appcharge says 0%). Check in Play Console before using external links.
- Whether US app-to-web on iOS requires an Apple entitlement. Apple's 3.1.1(a) text says no for the US storefront; RevenueCat's FAQ implies enrollment.

Not checked:
- Whether MongoDB Atlas still offers built-in auth or functions (Atlas App Services).

---

## 9. Recommended lowest-cost stack and month-1 cost table

### Takeaway
**Recommended stack for a non-developer:**
- **Builder:** Rork Pro (or Expo + Claude Code if comfortable in a terminal).
- **Monetization:** RevenueCat with IAP/subscriptions, hard paywall with trial. For a casual game: AdMob plus a "remove ads"/coins IAP.
- **AI:** a cheap vision model (Claude Haiku 5.5, GPT-5.4 nano or Gemini Flash) behind a free Supabase Edge Function or Cloudflare Worker proxy.
- **Web:** Cloudflare Pages for the legal pages.
- **Code:** GitHub.

**Month-1 fixed cost: about $165–$300.** That leaves roughly $700–$835 of the $1,000 for marketing and testers.

### Cited Findings
- Apple $99/year; Google $25 one-time — [Apple Developer Program](https://developer.apple.com/programs/whats-included/); [Play Console Help](https://support.google.com/googleplay/android-developer/answer/6112435?hl=en) (search extracts)
- Rork Pro $20/month (100 credits); Rork Max (iOS-only) from $200 — [Rork docs](https://docs.rork.com/introduction/subscriptions) (search extract)
- Expo EAS Free: $0 with 15 iOS + 15 Android builds; Starter $19 — [Expo pricing](https://expo.dev/pricing) (search extract)
- Claude Pro (includes Claude Code) about $20/month; Cursor Pro about $20/month — [morphllm](https://www.morphllm.com/comparisons/cursor-vs-copilot) (third-party)
- FlutterFlow Basic about $39/month (monthly billing) — [nocode.mba](https://nocode.mba/articles/flutterflow-pricing) (third-party)
- RevenueCat $0 up to $2,500 MTR — [RevenueCat pricing](https://www.revenuecat.com/pricing) (search extract)
- Supabase Free $0 (500K Edge Function invocations); Cloudflare Workers Free $0 (100K requests/day); Cloudflare static assets free — [Supabase pricing](https://supabase.com/pricing); [Cloudflare Workers pricing](https://developers.cloudflare.com/workers/platform/pricing/) (search extracts)
- AI vision call about $0.0003 (Haiku 5.5) to $0.0025 (GPT-5.4 mini) per scan — computed from [Anthropic vision docs](https://platform.claude.com/docs/en/build-with-claude/vision), [OpenAI GPT-5.4 mini/nano](https://openai.com/index/introducing-gpt-5-4-mini-and-nano/), [Gemini pricing](https://ai.google.dev/gemini-api/docs/pricing) (see Q5)
- Hockey AI (Rork case study) spent about $1,000 on influencer marketing to reach about $2,000 revenue and $1K/month — [Rork blog](https://rork.com/blog/eli-hockey-ai-case-study) (vendor-reported)
- Store commission about 15% on each store for small developers (Apple SBP enrollment; Google 10% service + 5% billing in the US/UK/EEA since June 30, 2026) — [Apple SBP](https://developer.apple.com/app-store/small-business-program/); [Android Developers Blog](https://android-developers.googleblog.com/2026/06/play-expanded-billing.html)

### Inferences

**Month-1 cost table** (USD, checked 2026-10-12)

| Item | Option chosen | Month-1 cost | Notes |
|---|---|---|---|
| Apple Developer Program | Individual | $99 | Annual; enroll in Small Business Program (free) before first sale |
| Google Play developer account | Personal | $25 | One-time; triggers 12-tester/14-day closed test |
| AI builder | Rork Pro | $20–$100 | $20 = 100 credits; heavier iteration may need a higher Pro credit tier (third-party: up to $100/500 credits) or a 2nd month |
| *Alt. builder* | Expo + Claude Pro (Claude Code) | $20 (+ EAS $0 or $19) | Full code ownership; needs terminal comfort |
| *Alt. builder* | FlutterFlow Basic | ~$39 | Visual; push needs Firebase Blaze |
| Build service | EAS Free (if Expo path) | $0 | 15 iOS + 15 Android builds/month; Rork builds on its own servers |
| Subscriptions/paywall | RevenueCat | $0 | Free < $2,500 MTR, then 1% of MTR |
| AI API | Claude Haiku 5.5 / GPT-5.4 nano / Gemini Flash | $5–$30 | ≈ $0.30–$2.50 per 1,000 photo scans; budget a buffer for testing and abuse |
| AI-key proxy | Supabase Edge Function or Cloudflare Worker | $0 | Free tiers; add per-user rate limits |
| Database | None (on-device) or Supabase Free | $0 | Watch the 7-day inactivity pause before launch |
| Legal/landing pages | Cloudflare Pages (static) | $0 | Privacy policy, terms/EULA, support URL |
| Custom domain (optional) | Any registrar | ~$10–$15/yr (unverified estimate) | Not required; a free *.pages.dev URL works |
| Analytics | PostHog Free (optional) | $0 | 1M events/month |
| Ads (games) | AdMob | $0 | Revenue share not verified |
| Closed-test testers | Friends/community | $0–$50 (unverified) | Paid tester services exist; prices not verified |
| **Total fixed (build + publish)** | | **≈ $165–$300** | Leaves ≈ $700–$835 of $1,000 for marketing (UGC/influencers, ASA/TikTok tests) |

**Recommended path by app type:**
- **AI scanner/utility or habit app:** Rork Pro + RevenueCat hard paywall with a 3- or 7-day trial on an annual plan and a weekly option. Benchmarks: weekly $5.99 and yearly $34.80 medians. Use a cheap vision model behind an Edge Function proxy, with consent before sending photos to third-party AI.
- **Casual puzzle game:** Phaser web game written with Claude Code/Cursor, wrapped with Capacitor, plus AdMob rewarded and interstitial ads and a "remove ads" IAP. Or Rork Pro for very simple grid puzzles (unverified). Avoid subscriptions as the main revenue source for games.

**Timeline-critical actions:**
- Day 1: register both developer accounts.
- Upload the Android closed-test build by about day 7.
- Recruit 15+ testers.
- Expect iOS launch around days 15–21 and Android around days 25–35.

### Gaps
- Domain registration cost and paid tester-recruitment service prices were not verified.
- Rork's credit consumption for a typical full app build is not documented beyond vendor case studies.
- Apple review turnaround times and Google production-access review times for 2026 were not verified.
- These cost figures exclude taxes, VAT and currency differences on developer fees in non-US regions.
