# Engineering case studies

I design, build and maintain these products as my employer's sole software engineer. I work directly with the people who use them and stay involved through release, monitoring, and field support.

[Kadans](#kadans-tellal) · [Tellal](#tellal) · [Turnstile](#turnstile) · [SepetArası](#sepetarasi) · [VeliGeldi](#veligeldi) · [AnnounceFlow](#announceflow) · [Price Checker](#retail-price-checker) · [Havale Bildirim](#bank-transfer-notifications)

<a name="kadans-tellal"></a>

## Kadans

**A production system for a regional, multi-city grocery chain with 20+ branches.**

One HQ server on the customer's network manages promotions, music, hours and prayer silence for every branch, with in-store Raspberry Pi players rolled out in stages. I designed, built and run it end to end, integrated with the customer's SQL Server ERP, network and VPN, and Windows server. The server publishes a versioned plan for each branch instead of play commands, so players keep going through network outages, and announcements play at most once, so a promotion is never replayed. The customer's server checks each night for a signed, canary-approved release and installs it unattended, rolling back from any failed step.

Copy and speech come from Tellal, below.

*Python, FastAPI, PostgreSQL, Go, MQTT 5, React, TypeScript, Raspberry Pi, PowerShell, Prometheus, Grafana.* [Full case study](https://github.com/berkaybakac/kadans-case-study)

<a name="tellal"></a>

## Tellal

**An AI announcement platform, built for several clients; Kadans is the first.**

Claude (Anthropic) writes the copy and ElevenLabs speaks it. The model writes only words around placeholders and code inserts prices and dates, so it can never state a wrong price; rejected copy falls back to a verified sentence in the same voice. Idempotent operations make every paid call safe to retry, and prepaid balances with spending caps checked inside the same transaction prevent overspending. Projects, scoped keys and versioned prompt and voice profiles serve several clients; an admin panel, fleet view and Prometheus/Grafana monitoring run it.

*Python, FastAPI, SQLite, Claude API, ElevenLabs, nginx, Prometheus, Grafana, Playwright.* [Full case study](https://github.com/berkaybakac/tellal-case-study)

<a name="turnstile"></a>

## Turnstile Device Agent

**QR access control for more than 20 turnstiles at gyms, studios and a swimming facility in seven cities, in production since June 2026.**

I built the device agent and its telemetry collector. The partner platform authorizes individual access; my agent shows its QR codes, decides the gate output for each grant, and switches to free passage after a sustained platform disconnect. The fleet handled more than 90,000 access approvals in its first six months; from 28 October to 27 November 2026 alone, 13 turnstiles handled 29,158, each new pulse a median of 3 ms after the device logged the approval. I prepare new devices on the bench, deploy tagged releases remotely and monitor the fleet with Prometheus device alerts that start only within each venue's opening hours; a company technician mounts each unit and checks passage on site.

*Python, asyncio, WebSockets, Raspberry Pi, Linux, systemd, GPIO, RS-485, FastAPI, Prometheus, Grafana, Tailscale.* [Full case study](https://github.com/berkaybakac/turnstile-case-study)

<a name="sepetarasi"></a>

## SepetArası

**One restaurant completed more than 12,400 orders with the system over seven months.**

I built a React kitchen and pickup interface, an Electron cashier app, and a TypeScript backend. The restaurant's existing LED display could not run the modern browser interface, so I added a lightweight HTML view it could use.

When a display loses its connection, it can miss an order becoming ready. I made it fetch the server's current order state after reconnecting. A regression test takes the display from preparing to ready even when it misses the original WebSocket update.

*TypeScript, Fastify, React, Electron, SQLite, WebSocket.*

<a name="veligeldi"></a>

## VeliGeldi

**The system sends about 2,500 classroom pickup notifications a month.**

I built the .NET backend, classroom notification client, licensing service, and name-audio integration. I made balances derive from a ledger and placed the check and spend in one PostgreSQL transaction protected by an advisory lock.

The integration test makes a second request wait while the first holds the lock. When it resumes, it sees the updated balance and declines the spend. I also built versioned Windows updates and rollback and made service updates work on the school's Windows PowerShell 5.1.

*C#, ASP.NET Core, PostgreSQL, SignalR, Avalonia.* [Public product website](https://veligeldi.com)

## AnnounceFlow

**Live audio and scheduled announcements in use at four locations.**

I built the Flask control panel, Windows audio sender, and playback software on Raspberry Pi. I used logs from both ends to locate packet fragmentation during live audio. Smaller audio blocks addressed that failure mode. Receiver recovery uses cooldowns, and its tests cover stopping playback while a recovery is in progress.

*Python, Flask, SQLite, UDP, Windows audio, Raspberry Pi.* [Source and setup](https://github.com/berkaybakac/announceflow)

## Retail Price Checker

**Android price terminals used across multiple retail branches.**

I connected the terminals to the retailer's SQL Server through a central .NET API. A delayed response from one scan could overwrite a newer price. I made the latest scan authoritative, cancelled superseded requests, and checked the scan identity before applying responses or timers. The regression covers the case where a previous lookup returns last.

*Kotlin, Android, ASP.NET Core, SQL Server.*

<a name="bank-transfer-notifications"></a>

## Havale Bildirim

**Installed at its first customer.**

I built a Windows app that lets cashiers see incoming bank transfers and print informational receipts. I designed the sync so the same transaction is recorded only once and queued receipts can resume after the printer reconnects. The first field release was v1.0.0.

*C#, Windows, SQLite, bank integrations, receipt printing.*

[Back to profile](README.md)
