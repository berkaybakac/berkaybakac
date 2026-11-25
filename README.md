# Berkay Bakaç

**Production systems end to end: backend platforms, device fleets and AI integrations**

I design, build and run production systems, from architecture to the customer's own servers and networks. I work directly with the people who use them, integrate with the systems they already run, and own releases, monitoring and field support.

**Software Engineer**, Statek Stabil Teknoloji · December 2025 – present

[Engineering case studies](case-studies.md) · [Portfolio](https://berkaybakac.vercel.app/en/) · [LinkedIn](https://www.linkedin.com/in/berkay-bakac/) · [Email](mailto:berkaybakacwork@gmail.com)

## Production work

- **[Kadans & Tellal](https://github.com/berkaybakac/kadans-case-study)** · In-store audio and AI announcements for a regional, multi-city grocery chain with 20+ branches. One HQ server on the customer's network turns ERP price changes into spoken announcements for every branch, with music, opening hours and prayer silence, played by a fleet of in-store Raspberry Pi players. Tellal, the AI announcement platform behind it, integrates Claude (Anthropic) and ElevenLabs. Designed, built and run end to end as sole engineer. [Case study](https://github.com/berkaybakac/kadans-case-study)
- **[Turnstile Device Agent](case-studies.md#turnstile)** · Built Python software for **18 turnstiles across six cities**. Offline mode kept gates usable during a documented 10-hour outage. A FastAPI collector receives device telemetry and deduplicates retried logs.
- **[SepetArası](case-studies.md#sepetarasi)** · Built the cashier, kitchen, and pickup screens for a restaurant that completed **12,400+ orders over seven months**. A display that reconnects reloads current orders so it can recover from missed updates.
- **[VeliGeldi](case-studies.md#veligeldi)** · Built the .NET backend and classroom notification software that sends **about 2,500 notifications a month**. A PostgreSQL test confirms that two requests cannot spend the same credit.
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
