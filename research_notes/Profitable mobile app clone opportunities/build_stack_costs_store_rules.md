# Build Stack, Costs and App-Store Rules for a Solo Non-Coding Australian Founder (AI app builder, iOS + Android, ~1 month, ~A$1,000)

Research date: 2026-10-12. Method notes for the report writer:
- **Primary pages fetched directly on 2026-10-12:** Apple developer pages (enrollment, programs, Small Business Program, App Review Guidelines "Last Updated: June 8, 2026", subscriptions guidance, App Store Connect tax/DSA/payments help, developer news), Anthropic/Claude pricing and vision docs, Google Cloud Vertex AI Gemini pricing, and the official Expo and Supabase docs. I read the Expo and Supabase docs from their GitHub source files.
- **Search-only sources:** Network policy blocked direct fetches of most other vendor sites: rork.com, vibecodeapp.com, a0.dev, flutterflow.io, revenuecat.com, superwall.com, adapty.io, supabase.com, openai.com, ai.google.dev, support.google.com and ato.gov.au. Facts about those come from web-search result summaries, often from third-party blogs, and are labelled as such.
- **Search budget ran out:** The session's web-search budget ran out before Google Play policy pages (spam, impersonation, subscriptions), ATO pages and some user-report searches could be run. Those gaps are listed explicitly.
- **Exchange rate assumption:** 1 AUD ≈ 0.69 USD, so 1 USD ≈ A$1.45 (rounded up slightly for safety). exchange-rates.org lists AUD/USD at about 0.6928 on 1 Oct 2026 ([exchange-rates.org](https://www.exchange-rates.org/exchange-rate-history/aud-usd-2026-10-01)). currency-converter.org.uk lists about 0.69 on 2 Oct 2026 ([currency-converter.org.uk](https://www.currency-converter.org.uk/converter/AUD/USD/1)). The 2026 range was 0.6676 to 0.7260 ([exchange-rates.org](https://www.exchange-rates.org/exchange-rate-history/aud-usd-2026-10-01)).
- **Not legal or tax advice:** Nothing here is legal or tax advice. The Australia section in particular must be confirmed with a registered tax agent or accountant.

## Q1. Which AI app builders can actually produce and publish native/cross-platform iOS + Android apps (2026), what do they cost, and what are their limits?

### Takeaway
Most "AI mobile app builders" that genuinely target both stores generate **Expo / React Native** code: Rork, Vibecode, a0.dev, Anything, Bolt (Expo mode), Replit (Expo Launch) and Claude Code/Cursor + Expo. FlutterFlow generates **Flutter**. Base44 and Lovable are **web-app builders**: they reach the stores only by wrapping the web app in a WebView shell (Base44's built-in shell, or Median/Capacitor), which carries more risk under Apple 4.2. Paid tiers for the AI-native builders cluster around **US$20–50/month** for a usable plan, with top tiers around US$200. Official pricing pages could not be fetched, and third-party sources disagree on tier names and credits, so every price below must be re-checked on the vendor site before purchase.

### Cited Findings

**Rork (Expo/React Native; a higher "Max" tier is reported to do native Swift)**
- Third-party guides agree that Rork has a free tier and paid plans topping out around US$200/month, metered by AI messages/credits rather than seats ([vp0.com](https://vp0.com/blogs/rork-pricing-plans-2026/); [nocode.mba](https://nocode.mba/articles/rork-pricing); [bilt.me](https://bilt.me/blog/rork-pricing); [aitoolsatlas.ai](https://aitoolsatlas.ai/tools/rork/pricing)).
- **Conflict on plan names and prices:**
  - One guide lists Junior US$25/mo (100 messages), Middle US$50 (250) and Senior US$100 (500) ([vp0.com](https://vp0.com/blogs/rork-pricing-plans-2026/)).
  - Another lists Pro US$20 (100 credits) and Max US$200 (1K credits) ([banani.co TR review](https://www.banani.co/tr/blog/rork-ai-review)).
  - A UK guide lists Free (50 credits), Plus and Pro at about £16/mo ([marcandrews.com](https://marcandrews.com/rork-pricing-uk-2026-ai-app-builder-cost-breakdown/)).
  - The free tier is variously reported as 5 or 50 credits/month.
- "Rork Max" at US$200/mo is reported as the tier for **native Swift** builds. The same sources list Apple Developer (US$99/yr) and Expo EAS as costs outside the Rork subscription ([search summary of vp0/aitoolsatlas/b12](https://vp0.com/blogs/rork-pricing-plans-2026/); [b12.io](https://www.b12.io/ai-directory/rork/)). Unverified against rork.com.

**Vibecode (React Native + web)**
- **Reported tiers:** Free, Plus US$20/mo, Pro US$50/mo, Max US$200/mo. Credits are pass-through ("$1 in Vibecode credits equals $1 of AI usage") and roll over. **Plus is reported as the lowest tier including App Store submission**. Pro adds downloadable source code and SSH (for example, editing in Cursor) ([superappp.com review](https://www.superappp.com/blog/vibecode-app-review-2026-pricing-real-reviews); [b12.io](https://www.b12.io/ai-directory/vibecode/)).
- An App Store pricing tracker (March 2026 snapshot) shows Vibecode's in-app purchases at US$19.99, US$49.99 and US$199.99 per month ([apppricinglab.com](https://apppricinglab.com/app/apple/6751900853)).
- One review says prompt-based costs "burn quickly, often on fixing the AI's own mistakes". Another says the current App Store listing repositions Vibecode as "the easiest way to learn how to code by building websites" ([superappp.com](https://www.superappp.com/blog/vibecode-app-review-2026-pricing-real-reviews)). Positioning may have shifted, so verify.

**a0.dev (YC W25; Expo/React Native)**
- Generates a complete React Native project on Expo. Third-party listings describe one-click publishing to the App Store and Google Play ([vp0.com a0 pricing](https://vp0.com/blogs/a0-dev-pricing-2026-explained); [techjockey](https://www.techjockey.com/detail/a0-dev); [dealroom](https://app.dealroom.co/companies/a0_dev_yc_w25_)).
- **Free:** one project, limited messages, **no store publishing**.
- **Pro:** from about US$20/mo with 100 credits.
- **Max:** reported as US$200 (1,250 credits). A separate guide says higher tiers reach US$800, which conflicts ([vp0.com](https://vp0.com/blogs/a0-dev-pricing-2026-explained); [techjockey](https://www.techjockey.com/detail/a0-dev)).
- Described as not suited to web apps or complex backends (third-party).

**Anything (formerly Create.xyz; Expo/React Native)**
- **Conflict on pricing:**
  - Anything's own blog estimate gives Starter US$19/mo and Pro US$49/mo ([anything.com blog](https://www.anything.com/blog/how-to-build-an-app-without-coding)).
  - A review lists Free, Pro US$19 and Max US$199 ([superappp.com](https://www.superappp.com/blog/anything-ai-app-builder-review-2026-pricing-verdic.md)).
  - An older page mentions US$16/mo with App Store submission support ([create.xyz blog](https://www.create.xyz/blog/how-to-build-an-app-without-coding)).
- Mobile output is Expo (React Native), not native Swift ([superappp.com](https://www.superappp.com/blog/anything-ai-app-builder-review-2026-pricing-verdic.md)).
- A 2026 review reports that **Apple pulled Anything's own iOS app under guideline 2.5.2** (apps that download or execute code). Other reporting says this happened around March 2026 and that Anything later returned ([superappp.com](https://www.superappp.com/blog/anything-ai-app-builder-review-2026-pricing-verdic.md); [axonbuild.com](https://axonbuild.com/blog/vibe-coded-app-rejected-app-store/); [appdrift.co](https://appdrift.co/blog/apple-rejecting-vibe-coded-apps)). This concerned the builder's own on-phone app, not apps built with it. Single or secondary sources.

**Bolt.new (StackBlitz; Expo integration for mobile)**
- Putting "mobile app" in the first prompt makes Bolt scaffold an Expo project, which you test in Expo Go ([support.bolt.new FAQ](https://support.bolt.new/concepts/faq)).
- Publishing needs an Expo account plus the Apple and Google accounts. You cannot share a public link: the app must be published to a store first (Spanish-language review, unverified) ([banani.co ES](https://www.banani.co/es/blog/bolt-new-pricing)).
- **Pricing (2026 summaries):**
  - Free: 300K tokens/day and 1M tokens/month.
  - Pro: US$25/mo, starting at 10M tokens/month with no daily limit.
  - Teams: US$30/member/mo.
  - One review puts Pro at US$20 ([vp0.com](https://vp0.com/blogs/bolt-new-pricing-2026-explained); [coddy.tech](https://coddy.tech/build/vs/bolt); [livemy.app](https://livemy.app/blog/bolt-new-pricing)).
- Tokens get more expensive as the app grows, because more code is read each turn ([livemy.app](https://livemy.app/blog/bolt-new-pricing)).
- No official Bolt step-by-step for store submission was found.

**FlutterFlow (Flutter; visual builder with AI features)**
- **Free:** no code export and no store publishing.
- **Basic:** **US$39/mo monthly (about US$29.25/mo billed annually)**. Unlocks code download, APK download, custom domain, local device testing and **one-click deployment to the App Store, Google Play and web**.
- **Growth:** US$80/mo for the first seat (US$55 for a second); adds GitHub integration, branching and collaboration.
- **Business:** US$150/mo for the first seat.
- An August 2025 restructure retired the old Standard/Pro/Teams plans ([lowcode.agency](https://www.lowcode.agency/blog/flutterflow-pricing-plans); [bilt.me](https://bilt.me/blog/flutterflow-pricing); [toolradar](https://toolradar.com/tools/flutterflow/pricing); [scand.com](https://scand.com/company/blog/flutterflow-vs-flutter-pricing-features/)). Third-party sources; verify on flutterflow.io.

**Replit (Agent builds Expo mobile apps; "Expo Launch" wizard)**
- Replit launched mobile app building with a direct App Store path in **January 2026** (dates vary between sources) ([vktr.com](https://www.vktr.com/ai-news/replit-launches-mobile-app-builder-with-direct-app-store-path/)).
- Per Replit docs, a "Start publishing to the App Store" button appears under Publishing. You sign in with the Apple account enrolled in the Developer Program, and **the bundle identifier cannot be changed later** ([docs.replit.com](https://docs.replit.com/build/mobile-upload-ios)).
- Launch signs the iOS build and pushes it to App Store Connect **without needing a Mac**. **Android stops at a file you upload yourself** ([axonbuild.com](https://axonbuild.com/blog/can-replit-make-mobile-apps/); [rapidnative.com](https://www.rapidnative.com/replit-agent-for-mobile-apps)).
- Plan gating for Launch is not stated in the docs. Previews are on the Core, Pro and Enterprise plans (third-party).

**Base44 (web builder → WebView shell)**
- Secondary sources say Base44 added store publishing in **early 2026** by wrapping the web app in a native WebView container, similar to Capacitor. They note that wrapped apps handle background push, Bluetooth and Face ID poorly and rank weakly in store search ([vp0.com](https://vp0.com/blogs/can-base44-publish-to-app-store-and-google-play)).
- Third-party wrappers (Median, webtoapp.design, RapidNative) and Fiverr freelancers also offer Base44 store packaging ([median.co](https://median.co/blog/how-to-convert-your-base44-web-app-into-a-native-app); [webtoapp.design](https://webtoapp.design/blog/convert-base44-website-to-app); [rapidnative.com](https://www.rapidnative.com/deploy/base44-to-app-store)).
- No official Base44 documentation was found to confirm this.

**Lovable (web builder; no native output)**
- Lovable launched its own **companion** iOS/Android app around 27 April 2026 for managing projects. That app does not publish your apps ([docs.lovable.dev](https://docs.lovable.dev/integrations/lovable-mobile-app); [communityone.io](https://communityone.io/servers/1119885301872070706/lovable/news/lovable-mobile-app-ios-android-release-2026-04-27/)).
- Lovable does not produce IPA or AAB files. Store publishing needs a WebView wrapper (Median) or Capacitor ([median.co](https://median.co/blog/how-to-convert-your-lovable-app-to-a-mobile-app-and-publish)).

**Claude Code / Cursor + Expo (most control; steeper learning curve)**
- **Claude:** Pro is **US$20/mo billed monthly** (US$17/mo on annual billing, US$200 up front) and **includes Claude Code**. Max starts at US$100/mo ([claude.com/pricing](https://claude.com/pricing), fetched 2026-10-12).
- **Expo EAS Free plan:** a limited, low-priority quota of builds that resets monthly. Free accounts cannot incur overage, and new builds stop until the quota resets on the 1st of the next month ([Expo docs: plans](https://raw.githubusercontent.com/expo/expo/main/docs/pages/billing/plans.mdx); [Expo docs: billing FAQ](https://raw.githubusercontent.com/expo/expo/main/docs/pages/billing/faq.mdx)). The pricing page lists **15 Android + 15 iOS builds/month** on Free ([expo.dev/pricing](https://expo.dev/pricing.md); [docs.expo.dev](https://docs.expo.dev/billing/plans/)).
- **EAS Starter:** **US$19/mo with US$45 of build credit** and 3,000 EAS Update MAU, versus 1,000 on Free ([Expo billing FAQ](https://raw.githubusercontent.com/expo/expo/main/docs/pages/billing/faq.mdx)). Example usage prices are US$1 per medium Android build, US$2 per large Android or medium iOS build, and US$4 per large iOS build ([Expo usage-based pricing](https://raw.githubusercontent.com/expo/expo/main/docs/pages/billing/usage-based-pricing.mdx)).
- Free-tier queues can wait 90+ minutes at peak (third-party) ([newly.app](https://newly.app/guides/eas-build)).
- **EAS Submit:** can submit to Google Play using a Google Service Account key. A first `eas submit` creates the app's first release on the **internal testing track**, but the app must already exist in Play Console ([Expo docs: submit/android](https://raw.githubusercontent.com/expo/expo/main/docs/pages/submit/android.mdx)).
- **In-app purchases** need native code, which **does not work in Expo Go**: you need a development build. Expo recommends RevenueCat's `react-native-purchases` (or `expo-iap`) ([Expo docs: in-app purchases](https://raw.githubusercontent.com/expo/expo/main/docs/pages/guides/in-app-purchases.mdx)). This applies to every Expo-based AI builder above.

**Cross-builder observation**
- Third-party commentary notes that AI builders often ship near-identical onboarding, tab bars and paywalls from the same template. App Review can then see clusters of look-alike apps as spam under 4.3 ([vp0.com](https://vp0.com/blogs/app-store-rejection-4-3-spam-design-ai-fix); [newly.app](https://newly.app/guides/does-apple-accept-ai-generated-apps)). Note that vp0 sells a template product.

### Inferences
- **Best fits for a non-coder targeting both stores in a month:**
  - An Expo-based AI builder that includes store submission on a ~US$20–50 plan: Rork, Vibecode Plus/Pro, a0 Pro or Anything.
  - FlutterFlow Basic (US$39), if the founder prefers a visual editor.
  - Replit only partially fits: iOS is automated, but the Android upload is manual.
- **Ensure code export:** Choose a plan that allows source-code export (for example, Vibecode Pro, or FlutterFlow Basic and up). Claude Code/Cursor + Expo can then rescue the project if the builder hits a wall.
- **Avoid WebView wrappers for a subscription app:** Base44 and Lovable wrappers raise the 4.2 "repackaged website" risk and give weaker native features (camera, IAP, push).
- **Budget for more than one month:** "Credits burn on fixing the AI's mistakes" is a recurring complaint. A second month or a higher tier is plausible.

### Gaps
- I could not fetch any builder's official pricing page (rork.com, vibecodeapp.com, a0.dev, anything.com, bolt.new, flutterflow.io, base44.com). All tier prices, credit counts and which tier includes store publishing are **unverified third-party claims with conflicts**.
- I found no reliable first-hand reports (Reddit/X/Indie Hackers) with numbers on shipping to both stores with each builder. The search budget ran out before targeted searches for first-hand reports.
- Cursor pricing was not verified.
- Whether each builder handles the Google Play 12-tester closed test, and RevenueCat wiring, end-to-end is not documented in the sources found.

## Q2. Monetization and infrastructure: RevenueCat / Superwall / Adapty, paywall A/B testing, analytics, backend, ads

### Takeaway
At launch scale the whole monetization and analytics stack can be **free**:
- **RevenueCat:** free under US$2.5k monthly tracked revenue.
- **Superwall Indie:** free under US$10k monthly app revenue.
- **Adapty:** free under US$5k.
- **PostHog:** about 1M events/month free.
- **Supabase Free:** 50k MAU and 500k Edge Function invocations.
- **Expo EAS Free:** see Q1.

The main traps are Supabase pausing free projects after 1 week of inactivity, and fees being charged on gross rather than net revenue.

### Cited Findings
- **RevenueCat:** free until **US$2.5k MTR (monthly tracked revenue)**. Above that, Pro charges **1% of total MTR**. The docs' example is US$26 on US$2,600 MTR, so the fee applies to the full amount, not just the excess. Accounts that drop back below the threshold return to free, and a 30-day grace period applies if the threshold is exceeded in the first month ([RevenueCat docs: account management](https://www.revenuecat.com/docs/welcome/set-up-revenuecat/account-management)).
  - Third parties say MTR is **gross** revenue, before Apple's or Google's cut ([apppricinglab.com](https://apppricinglab.com/playbook/revenuecat-review); [costbench.com](https://costbench.com/software/subscription-billing/revenuecat/)).
  - One comparison incorrectly describes the fee as 1% above the threshold only ([getpulsesignal.com](https://getpulsesignal.com/compare/revenuecat-vs-withorb)).
- **Superwall (paywall builder and A/B testing):**
  - **Indie: US$0/mo, free up to US$10k MAR (monthly app revenue), then 1% of total MAR.** Includes charts, webhooks, integrations, IAP SDK, paywalls, campaigns, audiences and templates.
  - **Startup:** US$49/mo + 1%. **Scale:** US$199/mo + 1% ([superwall.com/pricing](https://superwall.com/pricing.md); [apppricinglab.com](https://apppricinglab.com/playbook/superwall-review)).
  - Subscription infrastructure (entitlements, purchase APIs, webhooks) is described as free at any scale (third-party) ([apppricinglab.com](https://apppricinglab.com/playbook/superwall-review)).
  - Not confirmed whether **experiments/A-B tests are included on Indie**.
- **Adapty:** a February 2026 announcement made the Pro plan **free while MTR is under US$5,000**, then 1% of revenue above that. It previously cost US$99/mo minimum ([adapty.io blog](https://adapty.io/blog/adapty-new-pricing-2026/)). Some third-party pages still show the old US$99 minimum or a US$10k threshold ([toolradar](https://toolradar.com/tools/adapty/pricing); [g2.com](https://g2.com/products/adapty-io/pricing)).
- **PostHog:** free tier of **1M events/month**, 5K session replays and 1M feature-flag requests. Overage is about US$0.00005/event ([toolradar](https://toolradar.com/tools/posthog/pricing); [agentdeals.dev](https://agentdeals.dev/analytics-free-tier-comparison-2026)).
- **Mixpanel:** sources conflict. 2026 comparisons list a 1M events/month free plan with 10K replays ([costbench.com](https://costbench.com/compare/posthog-vs-mixpanel/); [solodevstack.com](https://solodevstack.com/blog/mixpanel-vs-posthog-solo-developers)), while others cite an older 100K MTU free tier ([amplitude.com](https://amplitude.com/compare/posthog-vs-mixpanel)).
- **Supabase Free** (official plans data):
  - Unlimited API requests, **50,000 MAU, 500 MB database**, 5 GB egress, 1 GB file storage.
  - **"Free projects are paused after 1 week of inactivity. Limit of 2 active projects."**
  - **Pro starts at US$25/mo:** 100k MAU, 8 GB disk, 250 GB egress, daily backups ([Supabase plans source](https://raw.githubusercontent.com/supabase/supabase/master/packages/shared-data/plans.ts)).
- **Supabase Edge Functions:**
  - Quota is **500,000 invocations/month on Free** and 2M on Pro/Team, then US$2 per extra 1M ([Supabase docs partial](https://raw.githubusercontent.com/supabase/supabase/master/apps/docs/content/_partials/billing/pricing/pricing_edge_functions.mdx)).
  - Limits: 256 MB memory, **2 s CPU time per request (async I/O excluded)**, 150 s request idle timeout, and 100 secrets per project ([Supabase docs: function limits](https://raw.githubusercontent.com/supabase/supabase/master/apps/docs/content/guides/functions/limits.mdx)).
- **AppLovin MAX (ads):** US$100 minimum before AppLovin pays. Payments are monthly at about NET 15. AppLovin pays for AppLovin Bidding and ALX revenue, while other networks in MAX pay separately ([AppLovin docs: payments](https://developers.applovin.com/en/max-dashboard/account/payments); [support.applovin.com](https://support.applovin.com/en/max/max-dashboard/account/payments)).
- **AdMob mediation:** AdMob docs describe adding AppLovin as a mediation source per ad unit and implementing **app-ads.txt** to avoid losing revenue ([Google AdMob mediation: AppLovin](https://developers.google.com/admob/android/mediation/applovin?hl=fa)).
- **Paywall disclosure (Apple):** the purchase flow must show the subscription name and duration, the **full renewal price clearly and prominently**, and a way to restore purchases. **The amount that will be billed must be the most prominent pricing element** (for example, the annual total rather than the "per week" equivalent). For free trials, show the trial length and the price billed afterwards. App and metadata must link Terms of Use and Privacy Policy ([Apple: Auto-renewable subscriptions](https://developer.apple.com/app-store/subscriptions/)).
- **Apple metered paywalls:** Apple encourages metered or freemium paywalls and testing prompt variants ([Apple: Auto-renewable subscriptions](https://developer.apple.com/app-store/subscriptions/)).
- **Apple revenue split on subscriptions:**
  - Standard: 70% of price in the first year of paid service, 85% after.
  - Small Business Program members receive **85% from the start** ([Apple: Auto-renewable subscriptions](https://developer.apple.com/app-store/subscriptions/)).

### Inferences
- **Recommended free stack:**
  - RevenueCat (free under US$2.5k MTR) for cross-store entitlements.
  - Optionally Superwall Indie (free under US$10k) on top for no-code paywall iteration.
  - Supabase Free for auth/DB/Edge Functions.
  - PostHog Free for funnels.
  - Expo EAS Free for builds.
  - Monthly cost: **US$0** until revenue arrives.
- **Two paywall vendors add complexity.** For a non-coder, pick the one the AI builder already integrates with. Expo's docs point to RevenueCat.
- **Supabase inactivity pause:** a live app with real users won't sit idle for 7 days, but a project paused during a slow review period could break the app for reviewers. Ping it or keep it active during review.
- **Ads vs subscriptions:** ad revenue for a new app is unlikely to reach AppLovin's US$100 payout threshold quickly. Subscriptions or IAP are the more realistic primary model, with ads optional for free tiers.

### Gaps
- **Firebase:** Analytics and Crashlytics free-tier terms and Firestore/Auth Spark-plan limits were not verified (firebase.google.com was unreachable and search budget was exhausted).
- **AdMob:** payment threshold and schedule not verified (one unverified third-party claim says Net 21).
- **Superwall:** experiments on the free Indie tier are not confirmed.
- **Mixpanel:** free-tier terms conflict.

## Q3. AI API costs (vision/LLM) and keeping keys server-side

### Takeaway
Vision calls are now cheap at the "small model" tier. Assuming one ~1 MP image + 500 prompt tokens + 300 output tokens per analysis:
- **Claude Haiku 5.5:** about **US$0.35 per 1,000 analyses**.
- **Gemini 3.1 Flash-Lite / 2.5 Flash:** about **US$0.9–1.3**.
- **Claude Sonnet 5.5:** about **US$6.60**.
- **Gemini 3.8 Flash:** about **US$2.30** at introductory pricing.

The biggest cost lever is resizing photos client-side before upload. API keys must never be shipped in the app. Expo explicitly warns that `EXPO_PUBLIC_` variables are plain text in the compiled app. Proxy calls through a Supabase Edge Function that holds the key as a secret.

### Cited Findings
- **Claude API pricing** (official, fetched 2026-10-12), input / output per million tokens:
  - Claude Fable 5.1: US$10 / US$50.
  - **Claude Opus 5.5: US$4 / US$20.**
  - **Claude Sonnet 5.5: US$2 / US$10.**
  - **Claude Haiku 5.5: US$0.10 / US$0.50 for prompts up to 100,000 tokens**, and US$0.50 / US$2.50 above 100k.
  - Legacy: Haiku 4.5 at US$1 / US$5; Sonnet 4.6 at US$3 / US$15.
  - Prompt-cache hits cost a fraction of input (for example, US$0.01/MTok on Haiku 5.5).
  - Source: [Claude pricing docs](https://platform.claude.com/docs/en/about-claude/pricing).
- **Claude image tokens:** cost = ⌈width/28⌉ × ⌈height/28⌉ visual tokens.
  - Claude 4.7+ models use a high-resolution tier: max long edge 2,576 px and **max 4,784 tokens per image**.
  - 1000×1000 px = **1,296 tokens**; 1920×1080 = 2,691 tokens on the high-res tier.
  - Larger images are downscaled ([Claude vision docs](https://platform.claude.com/docs/en/build-with-claude/vision)).
- **Gemini on Vertex AI** (Google Cloud, official, fetched 2026-10-12), USD per 1M tokens input / output (global endpoint):
  - **Gemini 3.8 / 3.7 / 3.6 Flash:** introductory **US$0.75 / US$3.75 through 31 Dec 2026**. Gemini 3.8 Flash rises to **US$1.50 / US$7.50 from 1 Jan 2027**.
  - **Gemini 3.5 Flash:** US$1.50 / US$9.00.
  - **Gemini 3.5 Flash-Lite:** US$0.30 / US$2.50.
  - **Gemini 3.1 Flash-Lite:** US$0.25 / US$1.50.
  - **Gemini 2.5 Flash:** US$0.30 / US$2.50.
  - Gemini 3 Flash Preview input is US$0.50.
  - Output price includes reasoning ("thinking") tokens.
  - Source: [Vertex AI generative AI pricing](https://cloud.google.com/vertex-ai/generative-ai/pricing).
- **Gemini image tokens:**
  - The Vertex page states "Image Input: 258 tokens per image" in its Live API conversion notes.
  - It states that Gemini 3.1 Flash Image and Flash-Lite Image charge 1,120 tokens per input image ([Vertex AI pricing](https://cloud.google.com/vertex-ai/generative-ai/pricing)).
  - Token counts for a standard image input to Gemini 3.x text models were not confirmed. I used 258–1,120 as a range.
- **OpenAI (third-party only, conflicting):**
  - Aggregators say GPT-5 and GPT-5-mini are no longer on OpenAI's pricing page. Reported prices for the current models are GPT-5.4-nano US$0.20 / US$1.25 and GPT-5.4-mini US$0.75 / US$4.50 per 1M tokens.
  - Older GPT-5 nano was US$0.05 / US$0.40, and GPT-5 mini US$0.125 / US$1.00 ([morphllm.com](https://morphllm.com/openai-api-pricing); [pricepertoken.com](https://pricepertoken.com/pricing-page/model/openai-gpt-5-nano); [trevorfox.com](https://trevorfox.com/tools/calculators/llm-cost/openai/gpt-5.4-mini/)).
  - One source describes a "GPT-5.6" family, which is unconfirmed.
  - **Not verified against openai.com.**
- **Expo key exposure:** "Do not store sensitive info, such as private keys, in `EXPO_PUBLIC_` variables. These variables will be visible in plain-text in your compiled application." EAS Build inlines these variables into the JS bundle ([Expo docs: environment variables](https://raw.githubusercontent.com/expo/expo/main/docs/pages/guides/environment-variables.mdx)).
- **Supabase secrets:** set with `supabase secrets set --env-file .env` or `supabase secrets set KEY=value`, or in the dashboard's Edge Function Secrets page. The docs warn that committing `.env` to Git exposes every secret ([Supabase docs: function secrets](https://raw.githubusercontent.com/supabase/supabase/master/apps/docs/content/guides/functions/secrets.mdx)).
- **Apple rule on third-party AI (5.1.2(i)):** "You must clearly disclose where personal data will be shared with third parties, **including with third-party AI**, and obtain explicit permission before doing so" ([App Review Guidelines 5.1.2](https://developer.apple.com/app-store/review/guidelines/)).

### Inferences: cost per 1,000 calls (my arithmetic from the official prices above; estimates only)
Assumptions:
- **Image analysis:** one photo resized to about 1000×1000 px. Claude counts it as about 1,296 tokens; for Gemini I conservatively assumed about 1,120. Plus about 500 tokens of text prompt, giving about 1.8M input tokens per 1,000 calls (about 1.62M for Gemini). Output is about 300 tokens, so 0.3M per 1,000.
- **Chat session:** about 10 turns totalling about 20k cumulative input tokens and 3k output tokens per session, with no caching.

| Model (price source) | ~Cost / 1,000 image analyses (USD) | ~AUD @1.45 | ~Cost / 1,000 chat sessions (USD) |
|---|---|---|---|
| Claude Haiku 5.5 ($0.10/$0.50) | ≈ $0.18 + $0.15 = **$0.33** | ≈ A$0.48 | ≈ $2 + $1.5 = **$3.50** |
| Claude Sonnet 5.5 ($2/$10) | ≈ $3.60 + $3.00 = **$6.60** | ≈ A$9.60 | ≈ $40 + $30 = **$70** |
| Claude Opus 5.5 ($4/$20) | ≈ **$13.20** | ≈ A$19 | ≈ **$140** |
| Gemini 3.1 Flash-Lite ($0.25/$1.50) | ≈ $0.41 + $0.45 = **$0.86** | ≈ A$1.25 | ≈ $5 + $4.5 = **$9.50** |
| Gemini 2.5 Flash ($0.30/$2.50) | ≈ $0.49 + $0.75 = **$1.24** (+ thinking tokens) | ≈ A$1.80 | ≈ $6 + $7.5 = **$13.50** |
| Gemini 3.8 Flash intro ($0.75/$3.75, to 31 Dec 2026) | ≈ $1.22 + $1.13 = **$2.35**; doubles from 1 Jan 2027 | ≈ A$3.40 | ≈ $15 + $11 = **$26** |
| GPT-5.4-mini ($0.75/$4.50, unverified) | ≈ **$2.85** (assumes ~2k input tokens/image) | ≈ A$4.10 | ≈ **$28.50** |

- **Resize photos before upload.** Sending a full 12 MP phone photo to a Claude 4.7+ model can cost up to 4,784 image tokens instead of about 1,300, roughly 3.7× the image-input cost. Client-side resizing to ~1,000 px is the main cost lever.
- **Per-user cost is small.** A heavy subscriber doing 100 scans/month costs about US$0.03 on Haiku 5.5 or about US$0.66 on Sonnet 5.5, small next to a ~US$5–10/month subscription. The real risk is **abuse**: someone extracting the key, or unauthenticated free users. Keep the key server-side, require auth or anonymous sessions, and rate-limit free users in the Edge Function.
- **Supabase CPU limit is not a problem here.** The 2 s CPU limit excludes async I/O, so an Edge Function that awaits an LLM call is fine. The 150 s idle timeout is ample for single vision calls.
- **Disclosure and consent:** add an in-app consent screen and privacy-policy text naming the AI provider before the first upload, to satisfy Apple 5.1.2(i).

### Gaps
- OpenAI official pricing and image-token accounting were not verified.
- The Gemini Developer API (ai.google.dev) free tier and its prices may differ from the Vertex prices above; that page was not reachable.
- Image-token counts for Gemini 3.x standard models are unconfirmed.
- Batch, flex and caching discounts were not modelled.

## Q4. Store accounts and fees (Apple, Google), small-business tiers, closed testing, D-U-N-S, EU DSA trader status

### Takeaway
- **Accounts:** Apple costs **US$99/year**, charged in local currency where available. Google Play costs a widely reported **US$25 one-time** fee.
- **Commission:** Both stores charge 15% for small developers. Apple's 15% requires enrolling in the Small Business Program. Google's 15% applies to subscriptions automatically, and to other sales on the first US$1M with enrollment.
- **Google closed test:** a new **personal** Google Play account must run a closed test with **≥12 testers opted in for ≥14 continuous days** before production. This is the single biggest timeline risk for a one-month plan.
- **Organization accounts** need a **D-U-N-S** number at both stores, which can take up to 30 days. A sole trader should enrol as an individual.

### Cited Findings
- **Apple fee:** "The Apple Developer Program annual fee is **99 USD** … in local currency where available. Prices may vary by region and are listed in local currency during the enrollment process" ([Apple: enrollment](https://developer.apple.com/support/enrollment/); [Apple: programs](https://developer.apple.com/programs/)).
  - The Australian price was reported as **A$149** in 2020 ([ozbargain.com.au](https://ozbargain.com.au/node/535826)). No current Apple page confirming the A$ price was found.
  - Fee waivers are not available to individuals or sole proprietors, or to apps with IAP ([adalo.com guide](https://studio.adalo.com/blog/apple-developer-program-guide)).
- **Apple individual vs organization:**
  - **Individuals and sole proprietors/single-person businesses enrol as individuals, and their legal name is shown as the seller.**
  - Organizations must be legal entities (no DBAs or trade names) and need a **D-U-N-S Number** ("free in most jurisdictions").
  - Individuals can buy the membership at enrolment. Organizations buy after Apple verifies them.
  - Individuals paying by card must use their own card.
  - Source: [Apple: enrollment](https://developer.apple.com/support/enrollment/).
- **TestFlight:** up to **10,000 external testers** by email or public link ([Apple: programs](https://developer.apple.com/programs/)).
- **Apple Small Business Program:**
  - **15% commission** for developers with ≤US$1M proceeds in the prior calendar year, and for new developers.
  - You must list Associated Developer Accounts.
  - The reduced rate starts 15 days after the end of the fiscal month in which enrolment is approved.
  - Source: [Apple: Small Business Program](https://developer.apple.com/app-store/small-business-program/).
- **Apple payouts:** paid within **45 days of the end of the fiscal month** once the per-region minimum payment threshold is met, to a single bank account, with currency conversion by Apple's bank ([Apple: overview of receiving payments](https://developer.apple.com/help/app-store-connect/getting-paid/overview-of-receiving-payments/)).
- **Google Play service fee:**
  - **15% on the first US$1M** of earnings each year (requires enrolling in the tier via a payments profile and account group), 30% above that.
  - **15% for auto-renewing subscriptions regardless of revenue** ([Google Play Console Help 112622](https://support.google.com/googleplay/android-developer/answer/112622?hl=en); [Google Play Console Help 10632485](https://support.google.com/googleplay/android-developer/answer/10632485?hl=en-AU)).
  - Google notes the rates may change as "updated service fees are rolled out globally".
- **Google registration fee:** the US$25 one-time fee is reported by [SplitMetrics](https://splitmetrics.com/blog/google-play-apple-app-store-fees/) and other guides. The official page was not fetched.
- **Google closed testing for new personal accounts:**
  - Developers with personal accounts **created after 13 November 2023** must run a closed test with **at least 12 testers opted in continuously for at least 14 days**, then apply for production access in Play Console ([Google Play Console Help 14151465](https://support.google.com/googleplay/android-developer/answer/14151465?hl=en-EN)).
  - The requirement was previously **20 testers**; one source dates the reduction to December 2024 ([androidauthority.com](https://androidauthority.com/google-play-app-testing-requirement-3510580)).
  - Third-party guides say testers must actually install and stay opted in, and the clock effectively resets if you drop below the threshold. **Organization accounts are reported as exempt** ([RevenueCat blog](https://www-docs.revenuecat.com/blog/engineering/google-play-14-day); [levelup.gitconnected.com](https://levelup.gitconnected.com/the-12-tester-tax-google-plays-closed-testing-rule-is-quietly-killing-solo-devs-2cea83c2e338); [extendsclass.com](https://extendsclass.com/blog/google-plays-closed-testing-requirement-what-developers-need-to-know-in-2026)). The org exemption and tester-eligibility details come from secondary sources.
- **Google D-U-N-S:**
  - New **organization** Play Console accounts must provide a **D-U-N-S number**, unless they are government or already have a verified payments profile. It is free from Dun & Bradstreet but can take **up to 30 days**.
  - Personal accounts don't need one.
  - Sources: [Google Play Console Help 10841920](https://support.google.com/googleplay/android-developer/answer/10841920); [goo.gle/developer-verification](https://goo.gle/developer-verification).
- **EU DSA trader status (Apple):**
  - Apple must verify and display trader contact info for apps on the EU App Store. You self-assess trader status, and having a "legal status associated with a business activity" suggests you are one.
  - **Individual traders must display an address or PO Box, phone and email** on the EU product page. All traders must provide payment details and certify EU-law compliance.
  - If you don't distribute on the EU App Store, you're not a trader there.
  - Source: [Apple: DSA trader requirements](https://developer.apple.com/help/app-store-connect/manage-compliance-information/manage-european-union-digital-services-act-trader-requirements/).
- **Apple EU terms:** new EU business terms took effect on **1 October 2026**. The Core Technology Fee is replaced by a 5% Core Technology Commission for apps distributed outside the App Store, alongside other commission changes ([Apple developer news, 18 Aug 2026](https://developer.apple.com/news/)).
- **Apple submission requirements:**
  - From **April 2027**, iOS uploads must be built with the iOS 27 SDK.
  - Age-rating questionnaire responses, including new social-media questions, are required for submissions from **September 2026**.
  - Source: [Apple developer news](https://developer.apple.com/news/).

### Inferences
- **Timeline risk:** on a personal Google account, the Android launch cannot happen sooner than about 14 days after 12 real testers are opted in, plus Google's production-access review. Start the closed test in **week 1–2** with the earliest working build, or ship iOS first.
- **Free testers:** friends and family, local communities, or tester-swap groups can supply them. Paid tester services exist but weren't priced here.
- **Sole trader vs company:** a sole trader with an ABN enrols as an Apple individual, under their legal name, with no D-U-N-S needed. An Australian Pty Ltd would need a D-U-N-S at both stores (up to ~30 days). It would show the company name and, on Google, avoid the 12-tester rule, but it adds time and cost that likely don't fit a 1-month / A$1,000 plan.
- **Apple Small Business Program:** enrol immediately after joining, because the 15% rate only starts the fiscal month after approval.
- **EU distribution:** an individual distributing in the EU must publish contact details (a PO Box is allowed). Alternatively, exclude EU storefronts at launch to avoid publishing a home address.

### Gaps
- Current Apple membership price in AUD is not confirmed (A$149 figure is from 2020).
- Google's US$25 fee was not read on an official page.
- Google Play's own DSA trader-status requirements and its 2026 Android developer-verification changes were not researched (search budget).
- Google Play production-access review time after the 14 days is not quantified.

## Q5. App review risks: Apple 4.3 / 4.1 / 4.2 / 3.1.1 / 3.1.2 / 5.1, Google Play equivalents, and how clone-style apps get approved

### Takeaway
Apple's guidelines (last updated 8 June 2026) directly target the "clone" playbook:
- **4.1** bans copying a popular app or its name/UI/icon.
- **4.3(b)** rejects apps "indistinguishable from what's already widely available". It names saturated categories (dating, flashlight, sound effects, wallpaper, simple timers, fortune telling) that need a "meaningfully different or improved experience".
- **4.2** rejects thin or web-wrapper apps.
- **4.2.6** rejects apps from template/app-generation services unless the content provider submits them.

Clone-style apps that pass generally copy the *proven job-to-be-done and monetization pattern*, not the brand, UI or assets. They add a real differentiator, ship a complete native experience, and follow paywall and privacy rules exactly. Health, finance and other regulated categories should come from a legal entity, not an individual.

### Cited Findings
All quotes in this group are from the [App Review Guidelines](https://developer.apple.com/app-store/review/guidelines/), fetched 2026-10-12 and marked "Last Updated: June 8, 2026".
- **4.1 Copycats:**
  - "Don't simply copy the latest popular app on the App Store, or make some minor changes to another app's name or UI and pass it off as your own."
  - Impersonation "may result in removal from the Apple Developer Program".
  - "You cannot use another developer's icon, brand, or product name in your app's icon or name, without approval."
- **4.2 Minimum Functionality:**
  - Apps should "elevate it beyond a repackaged website". If not "particularly useful, unique, or 'app-like,' it doesn't belong on the App Store."
  - 4.2.2: not primarily marketing, web clippings or a collection of links.
  - **4.2.6:** "Apps created from a commercialized template or app generation service will be rejected unless they are submitted directly by the provider of the app's content."
- **4.3 Spam:**
  - (a) Don't create multiple Bundle IDs of the same app.
  - (b) "Don't submit apps that are indistinguishable from what's already widely available. Opportunistically creating variants of existing app categories or popular apps degrades App Store discovery…"
  - "Certain kinds of apps, such as **dating, flashlight, sound effects, wallpaper, simple timers, and fortune telling**, are well established … and we will not accept new submissions unless they offer a meaningfully different or improved experience."
  - Drinking games, Kama Sutra, fart and burp apps are deemed low-quality. "Repeated submissions of this kind may lead to removal from the Apple Developer Program."
- **2.5.2:** apps may not "download, install, or execute code which introduces or changes features or functionality of the app".
- **3.1.1 In-App Purchase:**
  - Unlocking features or functionality requires IAP.
  - Purchased credits may not expire, and you must provide a **restore mechanism**.
  - Non-subscription free trials use a Price Tier 0 non-consumable named "XX-day Trial", with clear disclosure.
- **3.1.2 Subscriptions:**
  - Must provide **ongoing value** and last **at least seven days**.
  - Must work across the user's devices.
  - Users must not be required to do extra tasks such as posting on social or rating the app.
  - "Apps that attempt to trick users into purchasing a subscription under false pretenses or engage in bait-and-switch … will be removed … and you may be removed from the Apple Developer Program."
  - 3.1.2(c): "Before asking a customer to subscribe, you should clearly describe what the user will get for the price."
- **5.1.1 Privacy:**
  - A privacy-policy link is required in App Store Connect and in-app.
  - Collecting user data requires consent, and paid functionality must not depend on granting data access.
  - Use out-of-process pickers instead of full Photos access where possible.
  - **Apps with account creation must offer in-app account deletion.**
  - Apps without significant account features must work without login.
- **5.1.1(ix) regulated fields:** apps "in highly regulated fields (such as banking and financial services, **healthcare**, gambling…) or that require sensitive user information should be submitted by a legal entity that provides the services, and **not by an individual developer**."
- **5.1.2:**
  - (i) Disclose and get explicit permission before sharing personal data with **third-party AI**. Tracking requires App Tracking Transparency.
  - (vi) Data from camera/photo APIs, face mapping or HealthKit may not be used for marketing, advertising or data mining.
- **5.1.3 Health:** health and fitness data may not be used for advertising, and personal health information may not be stored in iCloud.
- **5.2.1:** don't use third-party trademarks or copyrighted works, or "copycat representations, names, or metadata".
- **Third-party commentary on AI-built apps:**
  - Apple doesn't reject apps for being AI-built; rejections come from quality and duplication.
  - **4.2 is described as the most common rejection for AI-built apps.**
  - 4.3 is triggered by look-alike template UIs.
  - Apple blocked updates for some apps that generate and run code in-app (2.5.2) around March 2026, while web-based builders like Lovable and Bolt were reported unaffected.
  - Sources: [vp0.com](https://vp0.com/blogs/does-apple-reject-ai-generated-apps); [axonbuild.com](https://axonbuild.com/blog/vibe-coded-app-rejected-app-store/); [appdrift.co](https://appdrift.co/blog/apple-rejecting-vibe-coded-apps); [newly.app](https://newly.app/guides/does-apple-accept-ai-generated-apps). These are blogs, and several are vendors with a stake in the framing.
- **4.2.6 interpretation:** one source argues 4.2.6 is about *who submits*, so a founder submitting their own builder-made app under their own account is not the issue the rule targets ([vp0.com](https://vp0.com/blogs/does-apple-reject-ai-generated-apps)).

### Inferences
**How clone-style apps get approved** (synthesis of the guideline text, not a guarantee):
1. Copy the **category/job and monetization model**, never the competitor's name, icon, screenshots, copy or UI layout (4.1, 5.2.1).
2. Add at least one clearly visible differentiator to avoid 4.3(b), such as:
   - a niche audience, for example "for Australian tradies";
   - a better UX;
   - an extra AI feature;
   - localisation;
   - an offline mode.
   Say what it is in the App Review notes.
3. Customise the AI-builder template: unique onboarding, design system and icon, so it doesn't look like other builds from the same template.
4. Make it fully native and complete. Avoid WebView-only experiences (4.2), placeholder content and broken flows (2.1).
5. Apply the paywall rules:
   - billed amount most prominent;
   - trial length and post-trial price shown;
   - restore button;
   - Terms and Privacy links in app and metadata;
   - no dark patterns (3.1.2).
6. Apply the privacy rules:
   - in-app account deletion if accounts exist;
   - login not forced;
   - AI-sharing consent;
   - minimal permissions;
   - accurate privacy nutrition labels (5.1).
7. Avoid the named saturated categories and anything health, finance or medical-diagnosis as an individual developer (5.1.1(ix)).
8. Never let the app download or execute new code (2.5.2). Avoid "AI generates mini-apps inside the app" concepts.

### Gaps
- **Google Play policy pages were not fetched or searched** (support.google.com was blocked and the search budget was exhausted). This includes the Spam and Minimum Functionality policy (repetitive content, webview spam), Impersonation and Intellectual Property, and Subscriptions/Payments disclosure rules. From prior knowledge, Google has comparable rules, but specifics and current wording must be verified before the report states them.
- No quantified data was found on rejection rates for AI-built or clone apps, and no first-hand case studies with outcomes.

## Q6. Australia-specific setup: ABN / sole trader / company, GST on store sales, income tax, W-8BEN, bank/payout

### Takeaway
**Critical finding:** Apple's App Store Connect tax help states that **Apple requires Australia-based developers to have an ABN *and* GST registration to sell apps**, "although you may not be required to register for GST with the Australian government". For a paid or subscription app, the founder therefore needs an ABN and voluntary GST registration before paid agreements can be completed. GST handling then differs between stores:
- **Apple:** reportedly an agency/RCTI arrangement, where you report GST from Apple's recipient-created tax invoices.
- **Google:** Google's help page says Australian-based developers are responsible for charging and remitting GST on Play sales to Australian customers.

Both stores require US tax forms (W-8BEN for non-US individuals at Apple). An accountant must confirm the structure, BAS obligations and income tax treatment.

### Cited Findings
- **Apple tax requirements for Australian developers** ([Apple: provide tax information](https://developer.apple.com/help/app-store-connect/manage-tax-information/provide-tax-information/)):
  - "Although you may not be required to register for Goods and Services Tax (GST) with the Australian government, **Apple requires that Australia-based developers have a GST registration to sell apps.** Required tax information: **Australian Business Number (ABN) and proof of GST Registration.**"
  - Evidence can be screenshots or PDFs of the ABN registration showing the GST history.
  - The page links to "recipient-created tax invoices".
- **US tax forms:**
  - "All developers must complete a US tax form to comply with the Paid Apps Agreement."
  - Non-US developers are directed to **W-8BEN** (individuals), W-8BEN-E or W-8ECI.
  - Once submitted, the forms can't be changed in App Store Connect without contacting Apple.
  - Source: [Apple: provide tax information](https://developer.apple.com/help/app-store-connect/manage-tax-information/provide-tax-information/).
- **Google Play GST** ([Google Play Console Help 138000](https://support.google.com/googleplay/android-developer/answer/138000?hl=en)):
  - Per Google's tax help page, **Australian developers are responsible for determining, charging and remitting GST** on Google Play paid-app and in-app purchases by customers in Australia.
  - Google may charge 10% GST on its service fee to non-GST-registered developers.
  - For developers **outside** Australia, Google itself remits 10% GST on Play-billing purchases by Australian customers.
- **Conflicting views on who handles GST:**
  - A consultancy blog says Apple uses an **agency arrangement**, so you report GST from Apple's RCTIs, while Google Play leaves you to charge and remit GST. Direct website sales are always your obligation ([42 Advisory](https://42advisory.com.au/42-advisory-blog/gst-app-store-sales-australia)).
  - Lawpath says the stores are generally treated as the supplier, which contradicts the split above ([Lawpath](https://lawpath.com.au/blog/launching-an-app)).
  - Old forum posts describe Apple's Australian sales including GST that the developer reports on the BAS ([Whirlpool](https://forums.whirlpool.net.au/archive/2132696); [Apple forums thread 132812](https://developer.apple.com/forums/thread/132812)).
- **ATO rules for electronic distribution platform (EDP) operators:**
  - The operator is generally responsible for GST on sales of digital products to Australian consumers by **offshore** merchants.
  - For **Australian** merchants, the operator can take on GST responsibility only if there is a written agreement before the sale and the operator is GST-registered ([ATO: if you are an EDP operator](https://www.ato.gov.au/businesses-and-organisations/international-tax-for-business/gst-for-non-resident-businesses/how-to-charge-gst/if-you-are-an-edp-operator)). Content came via search summary, not a direct fetch.
- **Sub-threshold sole trader:** an Apple developer forum thread is titled "Australian GST with revenue < AUD$75k". It concerns a sole trader being asked for GST registration despite low turnover ([Apple forums thread 85437](https://developer.apple.com/forums/thread/85437)). It is anecdotal, and the page content could not be rendered.
- **Payouts:**
  - Apple pays into one bank account in your bank's currency (Apple's bank converts), within 45 days of fiscal month-end, above a minimum threshold ([Apple: receiving payments](https://developer.apple.com/help/app-store-connect/getting-paid/overview-of-receiving-payments/)).
  - AppLovin pays monthly at NET 15 once over US$100 ([AppLovin docs](https://developers.applovin.com/en/max-dashboard/account/payments)).
- **Google's disclaimer:** Google states it "cannot provide you with tax advice. Please consult your tax advisor" ([Google Play Console Help 138000](https://support.google.com/googleplay/android-developer/answer/138000?hl=en)).

### Inferences
- **Practical setup sequence for a sole trader** (confirm with an accountant):
  1. Apply for an ABN.
  2. Register for GST voluntarily, as Apple requires it to sell.
  3. Enrol in the Apple Developer Program as an individual and the Google Play Console as a personal account.
  4. Complete Apple's Paid Apps Agreement with ABN + GST proof + W-8BEN, plus bank details.
  5. Set up the Google Payments profile, including tax info.
  6. Lodge BASs: quarterly is typical for small businesses (verify).
- **Benefit of GST registration:** being registered may let the founder claim GST credits on Australian-GST-inclusive business purchases. Whether foreign SaaS tools charge Australian GST depends on the vendor (verify).
- **Price setting:** set store prices knowing that, for Australian customers, the GST component may be your liability (Google) or reported via RCTIs (Apple).
- **Company vs sole trader:** a company (Pty Ltd) adds ASIC registration costs, a D-U-N-S, separate tax returns and slower store verification. For a ~A$1,000 test it is probably not worth it initially. Revisit if revenue grows, or if building in regulated categories (Apple 5.1.1(ix)).
- **Income tax:** store proceeds are business income for the sole trader, net of deductible expenses. The specifics need an accountant.

### Gaps
- No ATO page was fetched directly (ato.gov.au was blocked, and the search budget ran out before ABN/GST-threshold searches). Unverified this session:
  - the A$75,000 GST registration threshold;
  - ABN application cost (believed free);
  - BAS frequency;
  - sole trader vs company tax rates.
- Apple's Australia RCTI mechanics were not read in full: the RCTI help page URL tried returned "Page Not Found".
- Google Play's payments-profile tax form requirements for Australians (W-8BEN equivalent) were not verified.
- A **conflict remains on GST responsibility for Google Play sales by Australian-based developers** (Google help page and 42 Advisory vs Lawpath). Flag for accountant review.

## Q7. A realistic line-item budget (~A$1,000) and what to skip

### Takeaway
A full two-store launch fits within about **A$1,000 (≈US$690)**. Store accounts take about A$185, an AI builder about A$75–145, AI API credits about A$45, and nearly all infrastructure is free tiers. That leaves about A$300–400 for a small paid acquisition test plus a contingency for rejections or an extra builder month. Skip company registration, paid infra tiers, paid tester services, agencies and multiple builder subscriptions.

### Cited Findings (unit costs used)
- **Apple Developer Program:** US$99/yr in local currency ([Apple](https://developer.apple.com/support/enrollment/)). About A$149 per a 2020 source ([ozbargain](https://ozbargain.com.au/node/535826)); at current FX it would be about A$144.
- **Google Play:** US$25 one-time ([SplitMetrics](https://splitmetrics.com/blog/google-play-apple-app-store-fees/)).
- **AI builders:**
  - Rork about US$20–50 for entry/mid tiers ([vp0](https://vp0.com/blogs/rork-pricing-plans-2026/)).
  - Vibecode Plus US$20 / Pro US$50 ([superappp](https://www.superappp.com/blog/vibecode-app-review-2026-pricing-real-reviews)).
  - a0 Pro about US$20 ([vp0](https://vp0.com/blogs/a0-dev-pricing-2026-explained)).
  - Anything US$19–49 ([anything.com](https://www.anything.com/blog/how-to-build-an-app-without-coding)).
  - Bolt Pro US$25 ([vp0](https://vp0.com/blogs/bolt-new-pricing-2026-explained)).
  - FlutterFlow Basic US$39 ([lowcode.agency](https://www.lowcode.agency/blog/flutterflow-pricing-plans)).
  - Claude Pro US$20 ([claude.com/pricing](https://claude.com/pricing)).
- **Expo EAS:** Free plan, or Starter US$19 with US$45 build credit ([Expo FAQ](https://raw.githubusercontent.com/expo/expo/main/docs/pages/billing/faq.mdx)).
- **RevenueCat:** US$0 under US$2.5k MTR ([RevenueCat docs](https://www.revenuecat.com/docs/welcome/set-up-revenuecat/account-management)).
- **Superwall:** US$0 under US$10k MAR ([superwall.com](https://superwall.com/pricing.md)).
- **Adapty:** US$0 under US$5k ([adapty.io](https://adapty.io/blog/adapty-new-pricing-2026/)).
- **Supabase:** Free US$0 ([Supabase plans](https://raw.githubusercontent.com/supabase/supabase/master/packages/shared-data/plans.ts)).
- **PostHog:** Free US$0 up to 1M events ([toolradar](https://toolradar.com/tools/posthog/pricing)).
- **AI API:** see Q3; about US$0.33–6.60 per 1,000 image analyses.

### Inferences: suggested line-item budget (USD → AUD at 1 USD = A$1.45; excludes any GST charged by vendors)

| # | Item | USD | AUD | Notes |
|---|---|---|---|---|
| 1 | Apple Developer Program (1 yr) | 99 | ~149 | Mandatory for iOS. A$ price unconfirmed; it may show differently at checkout |
| 2 | Google Play Console (one-time) | 25 | ~36 | Mandatory for Android |
| 3 | AI app builder, ~2 months of a mid tier (for example US$50/mo) | 100 | ~145 | Pick ONE builder. Ensure the plan includes store submission and code export |
| 4 | Expo EAS Starter, 1 month (optional) | 19 | ~28 | Only if free-queue waits or build quota block you; otherwise US$0 |
| 5 | AI API prepaid credits (Claude / Gemini) | 30 | ~44 | Covers tens of thousands of Haiku/Flash-class calls in testing and launch |
| 6 | RevenueCat / Superwall / Adapty, Supabase, PostHog | 0 | 0 | Free tiers |
| 7 | ABN + GST registration | 0 | 0 | Believed free; verify. Accountant consult not included |
| 8 | Domain for landing page, privacy policy and support URL | ~10–20 | ~15–30 | **Unverified estimate**. Hosting on a free tier (unverified) |
| 9 | Design assets: AI icon and screenshot generation | ~20 | ~29 | Placeholder; covered by the marketing/AI-video researcher |
| 10 | AI video tool, 1 month, for TikTok/Reels creatives | ~30 | ~44 | Placeholder; covered by the marketing researcher |
| 11 | Small paid UA test (Apple Search Ads / TikTok / Meta) | ~250 | ~363 | Validate CPI and trial conversion; stop if the paywall doesn't convert |
| 12 | Contingency (extra builder month, resubmissions, FX/GST, tester incentives) | ~100 | ~145 | Keep in reserve |
| | **Total** | **~690** | **~1,000** | |

- **Skip or defer:**
  - Pty Ltd company and D-U-N-S.
  - Supabase Pro (US$25/mo), Superwall Startup (US$49/mo), Mixpanel paid, FlutterFlow Growth.
  - Paid "12 testers" services (use friends and communities).
  - Fiverr/agency store-submission services.
  - Multiple simultaneous AI-builder subscriptions.
  - Claude Max.
  - Paid templates.
  - Trademark filing (revisit if traction).
  - Large ad spend before paywall conversion is proven.
- **If the user is in USD, not AUD:** the same plan costs about US$690, leaving about US$310 more headroom for the UA test.
- **Ongoing monthly run-rate after launch:** about US$20–50 for the builder (or cancel it once code is exported), plus API usage, plus US$0 infra until revenue thresholds.

### Gaps
- Domain, landing-page hosting, AI image/video tool and ad-platform minimums were not verified in this research scope. The marketing researcher should supply them.
- Whether foreign vendors add 10% Australian GST to these prices was not verified.
- Accountant fees were not included.

## Q8. Which app types are realistic in ~1 month with these tools, and which are not?

### Takeaway
Realistic types are **single-purpose, mostly client-side apps with one AI call and a subscription paywall**:
- camera/photo → AI analysis "scanner/identifier" apps (non-medical);
- AI text, chat or coach utilities;
- trackers, journals and habit apps;
- quiz, flashcard and learning apps;
- simple productivity utilities.

Not realistic in a month (or risky for an individual developer):
- anything with user-generated social feeds, marketplaces, real-time multiplayer, payments between users, deep hardware or background integrations, or health, finance or medical claims;
- categories Apple explicitly flags as saturated;
- apps that generate or run code.

### Cited Findings
- The Expo-based builders target React Native/Expo apps. a0.dev is described as not suited to complex backends ([vp0.com](https://vp0.com/blogs/a0-dev-pricing-2026-explained)).
- WebView-wrapped apps (Base44/Lovable) handle background push, Bluetooth and Face ID poorly ([vp0.com](https://vp0.com/blogs/can-base44-publish-to-app-store-and-google-play)).
- IAP requires a development build, not Expo Go, and RevenueCat integration ([Expo docs](https://raw.githubusercontent.com/expo/expo/main/docs/pages/guides/in-app-purchases.mdx)).
- Apple 4.3(b) lists dating, flashlight, sound effects, wallpaper, simple timers and fortune telling as saturated; drinking games and fart/burp apps are low-quality ([App Review Guidelines](https://developer.apple.com/app-store/review/guidelines/)).
- Apple 5.1.1(ix): banking/financial, healthcare, gambling, cannabis, air travel and crypto apps should come from a legal entity, not an individual developer ([App Review Guidelines](https://developer.apple.com/app-store/review/guidelines/)).
- Apple 5.1.3 and 5.1.2(vi): health data and camera/face-mapping data restrictions ([App Review Guidelines](https://developer.apple.com/app-store/review/guidelines/)).
- Apple 2.5.2 forbids downloading or executing code that changes functionality ([App Review Guidelines](https://developer.apple.com/app-store/review/guidelines/)).
- From September 2026, Apple's age-rating questionnaire requires declaring **social media capabilities** (feeds or UGC discovery), which add a "Social Media" content descriptor and Time Allowances category ([Apple developer news, 9 Jul 2026](https://developer.apple.com/news/)).
- Supabase Edge Functions have a 2 s CPU and 150 s idle limit per request ([Supabase limits](https://raw.githubusercontent.com/supabase/supabase/master/apps/docs/content/guides/functions/limits.mdx)). This suits single API-proxy calls, not heavy server processing.

### Inferences
**Realistic in ~1 month** (one core loop, 3–6 screens, onboarding + paywall + settings):
- **AI camera "identify/scan/estimate" apps:** plants, objects, food labels or receipts, with a "for information only" framing. Avoid medical or diagnostic claims (5.1.1(ix), 5.1.3).
- **AI writing/rewriting, caption, translation or "coach" utilities** with a narrow niche persona.
- **Trackers, journals and habit/streak apps** with local storage or Supabase, plus an AI summary feature.
- **Learning:** quiz, flashcard and exam-prep apps, with AI-generated practice for a niche.
- **Simple calculators or converters** for a specific profession or region (for example, Australian trades), differentiated enough to avoid 4.3.

**Not realistic, or high-risk, for this founder/timeline:**
- Social networks, UGC feeds and chat between users: moderation, reporting and blocking, plus the new social-media age-rating declarations.
- Marketplaces, bookings, delivery and payments between users.
- Real-time multiplayer games and complex games.
- Health, medical, fitness-with-HealthKit, finance, budgeting with bank links, gambling and crypto (5.1.1(ix) legal-entity expectation; 5.1.3).
- Dating, wallpaper, flashlight, sound effects, simple timers and fortune telling (4.3(b) saturated).
- Apps that need background processing, Bluetooth, widgets, watch apps or heavy native modules beyond what the builder supports.
- "AI builds apps inside your app" concepts (2.5.2).
- Anything copying a competitor's brand, name, icon or UI (4.1, 5.2.1).

**Timeline realism:** about 1–2 weeks to build with the AI builder, then iOS TestFlight and review (days). Android needs the 14-day, 12-tester closed test on a personal account, so the plan should start Android closed testing by around day 10 at the latest to have any chance of a Play production launch within the month.

### Gaps
- No quantified success-rate data was found for one-month AI-builder launches by non-coders. First-hand Reddit, X and Indie Hackers reports were not gathered because the search budget was exhausted.
- Apple review turnaround times for 2026 were not verified.
