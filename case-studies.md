# Engineering case studies

I build and maintain these products as the sole software developer at Statek Stabil Teknoloji. I work directly with the people who use them and stay involved through release, monitoring, and field support.

[Turnstile](#turnstile) · [SepetArası](#sepetarasi) · [VeliGeldi](#veligeldi) · [AnnounceFlow](#announceflow) · [Price Checker](#retail-price-checker) · [Havale Bildirim](#bank-transfer-notifications)

<a name="turnstile"></a>

## Turnstile Device Agent

**Built software for 18 turnstiles across six cities as of 21 November 2026.**

I wrote the Python agent that connects a vendor access platform to Raspberry Pi kiosks and GPIO-controlled turnstiles. I validated incoming WebSocket events before they could trigger hardware. During a documented 10-hour upstream outage, the affected gates stayed usable through their configured offline mode.

I built a FastAPI collector for heartbeats and logs. If a response is lost after the collector stores a batch, the device can retry without counting the same records twice. Tests exercise retry deduplication per device. I also wrote the setup and verification checklist used by the technician who handles physical installation.

*Python, Raspberry Pi, Linux, systemd, WebSocket, GPIO, FastAPI, Prometheus, Grafana.*

<a name="sepetarasi"></a>

## SepetArası

**One restaurant completed more than 12,400 orders with the system from April through October 2026.**

I built a React kitchen and pickup interface, an Electron cashier app, and a TypeScript backend. The restaurant’s existing LED display could not run the modern browser interface, so I added a lightweight HTML view it could use.

When a display loses its connection, it can miss an order becoming ready. I made it fetch the server’s current order state after reconnecting. A regression test takes the display from preparing to ready even when it misses the original WebSocket update.

*TypeScript, Fastify, React, Electron, SQLite, WebSocket.*

<a name="veligeldi"></a>

## VeliGeldi

**The system sent about 2,500 classroom pickup notifications a month as of October 2026.**

I built the .NET backend, classroom notification client, licensing service, and name-audio integration. I made balances derive from a ledger and placed the check and spend in one PostgreSQL transaction protected by an advisory lock.

The integration test makes a second request wait while the first holds the lock. When it resumes, it sees the updated balance and declines the spend. I also built versioned Windows updates and rollback and fixed a service-update issue found on the school’s PowerShell version.

*C#, ASP.NET Core, PostgreSQL, SignalR, Avalonia.* [Public product website](https://veligeldi.com)

## AnnounceFlow

**Live audio and scheduled announcements in use at four locations as of 6 October 2026.**

I built the Flask control panel, Windows audio sender, and playback software on Raspberry Pi. I used logs from both ends to locate packet fragmentation during live audio. Smaller audio blocks addressed that failure mode. Receiver recovery uses cooldowns, and its tests cover stopping playback while a recovery is in progress.

*Python, Flask, SQLite, UDP, Windows audio, Raspberry Pi.* [Source and setup](https://github.com/berkaybakac/announceflow)

## Retail Price Checker

**Android price terminals used across multiple retail branches.**

I connected the terminals to the retailer’s SQL Server through a central .NET API. A delayed response from one scan could overwrite a newer price. I made the latest scan authoritative, cancelled superseded requests, and checked the scan identity before applying responses or timers. The regression covers the case where a previous lookup returns last.

*Kotlin, Android, ASP.NET Core, SQL Server.*

<a name="bank-transfer-notifications"></a>

## Havale Bildirim

**First customer installation documented in November 2026.**

I built a Windows app that lets cashiers see incoming bank transfers and print informational receipts. I designed the sync so the same transaction is recorded only once and queued receipts can resume after the printer reconnects. The first field release was v1.0.0. Subsequent release artifacts have their own installation and verification records.

*C#, Windows, SQLite, bank integrations, receipt printing.*

<a name="kadans-tellal"></a>

## Kadans & Tellal

**Customer pilot. The server was installed at the customer site and playback was exercised on a Raspberry Pi in the office.**

I built the workflow that turns campaign data into an in-store announcement. Claude drafts wording, code inserts prices and dates, and ElevenLabs generates the audio. If validation fails or the text budget is reached, the system uses a standard script. The FastAPI backend serves playback plans over HTTPS. A Go broker uses MQTT for plan changes and device presence.

*Python, FastAPI, PostgreSQL, Go, MQTT, HTTPS, Raspberry Pi.*

## Career Portal

**Personal development project.**

I built a local application-workflow tool in which one agent drafts from selected evidence and another reviews independently. The system checks structured output and saves each completed stage, so I can resume an interrupted run and approve the final text myself.

*Python, FastAPI, React, SQLite, Claude Code, Codex.*

[Back to profile](README.md)
