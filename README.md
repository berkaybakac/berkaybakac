# Berkay Bakaç

**Production systems end to end: backend platforms, device fleets and AI integrations**

I design, build and run production systems, from architecture to the customer's own servers and networks. I work directly with the people who use them, integrate with the systems they already run, and own releases, monitoring and field support.

**Software Engineer**, Statek Stabil Teknoloji · December 2025 – present

[Engineering case studies](case-studies.md) · [Portfolio](https://berkaybakac.vercel.app/en/) · [LinkedIn](https://www.linkedin.com/in/berkay-bakac/) · [Email](mailto:berkaybakacwork@gmail.com)

## Production work

- **[Kadans](https://github.com/berkaybakac/kadans-case-study)** · I built and run in-store audio and AI announcements for a regional grocery chain with more than 20 branches, live in its first branches and rolling out branch by branch. Its SQL Server ERP feeds Raspberry Pi players announcing eligible discounts; after the office canary, the customer's server updated itself overnight and reported success. [Case study](https://github.com/berkaybakac/kadans-case-study)
- **[Tellal](https://github.com/berkaybakac/tellal-case-study)** · I built the AI gateway for paid LLM and speech calls behind Kadans: Claude writes the words, code every price, spend limits guard each call. Copy and speech settle separately, so a speech retry never charges for the copy again. [Case study](https://github.com/berkaybakac/tellal-case-study)
- **[Turnstile Device Agent](https://github.com/berkaybakac/turnstile-case-study)** · I built and operate the Raspberry Pi access software for more than 20 turnstiles at gyms, studios and a swimming facility in seven cities: **90,000+ access approvals in its first six months**, every field update delivered remotely, and automatic free passage after a sustained platform disconnect. [Case study](https://github.com/berkaybakac/turnstile-case-study)
- **[Guardian Pickup (VeliGeldi)](https://github.com/berkaybakac/guardian-pickup-case-study)** · Authorized pickup for a private kindergarten in Türkiye, in production since August 2026: a guardian identifies at the entrance kiosk and the child's classroom gets a real-time alert with the arrival photo. On-premises .NET on the school's Windows PCs, a PostgreSQL credit ledger with a tested last-credit lock, and remote upgrades through the school's filtered network using signed maintenance jobs. [Case study](https://github.com/berkaybakac/guardian-pickup-case-study)
- **[Restaurant Order Pickup](https://github.com/berkaybakac/restaurant-pickup-case-study)** · I built and run offline-first ordering and pickup for a restaurant in Türkiye: an Electron till, real-time React screens and spoken pickup calls, served by an on-site Raspberry Pi. **More than 15,700 orders from April to November 2026**, with October's volume about 2.5 times May's. [Case study](https://github.com/berkaybakac/restaurant-pickup-case-study)
- **[AnnounceFlow](case-studies.md#announceflow)** · The per-store predecessor of Kadans, in use at four locations: scheduled announcements and live Windows-to-Raspberry Pi audio; traced dropouts to UDP fragmentation. [Source code](https://github.com/berkaybakac/announceflow)
- **[Retail Price Checker](case-studies.md#retail-price-checker)** · Connected Android price terminals to SQL Server through a .NET API, in use across multiple branches. Fixed a race that let late replies overwrite the latest scan.
- **[Havale Bildirim](case-studies.md#bank-transfer-notifications)** · A Windows app that alerts cashiers to incoming bank transfers, filters duplicate transactions, and resumes pending receipt printing.

## Open-source & personal

- **[rag-supportbot](https://github.com/berkaybakac/rag-supportbot)** · Offline, document-grounded AI assistant for technical support teams: a full retrieval-augmented generation pipeline with LLaMA and FAISS.
- **[android-page-to-pdf](https://github.com/berkaybakac/android-page-to-pdf)** · Offline Android app that captures pages in order with automatic page turns and hands the PDF to Samsung Notes.
- **[rpi-location-audio-scheduler](https://github.com/berkaybakac/rpi-location-audio-scheduler)** · Location-aware audio scheduler for Raspberry Pi with systemd automation, offline caching and direct ALSA control.

**Stack:** Python · Go · C#/.NET · TypeScript/React · FastAPI · PostgreSQL · SQL Server · MQTT · Docker · Linux · Raspberry Pi · Prometheus/Grafana · LLM and speech APIs

## How I work

I own the architecture, every decision and every release. I write decisions down with their trade-offs, prove each guarantee with a test that fails without it, and verify on the target system. I use Claude Code and Codex daily as coding agents under my approval gates and test-enforced repository rules, and I own the correctness of every change.

Based in Türkiye. Open to international remote work, contracting, and relocation.
