# Selected engineering work

I build and maintain these products as the sole software developer at Statek Stabil Teknoloji. Deployment figures below are snapshots confirmed on 2026-09-08.

<a id="turnstile"></a>
## Turnstile Device Agent

**In use at 7 locations across 3 cities.**

The agent connects a vendor access service to a Raspberry Pi kiosk and physical turnstile outputs. It handles device communication, the local display, GPIO control, deployment and diagnostics. Membership decisions belong to the vendor service.

One integration issue was incomplete access-direction information in vendor messages. I added explicit validation and regression coverage so unrecognized directions do not trigger a hardware pulse. Connectivity loss is a separate operating-policy decision; it should not be confused with accepting an invalid command.

Another field investigation showed why a single CPU measurement was misleading: it landed between animation cycles. I added continuous sampling and changed animation timing after comparing sustained behavior on the device. That experience changed how I validate performance fixes.

**Stack:** Python, Linux, Raspberry Pi, WebSocket, GPIO, systemd, pytest. Source is private.

<a id="veligeldi"></a>
## VeliGeldi

**Live at 1 school.**

A guardian uses the entrance kiosk to find the linked student. The system sends a notification to the relevant classroom and plays name audio. It coordinates pickup communication; it does not record a teacher's custody approval.

I built the .NET backend, PostgreSQL data layer and classroom application, along with the companion licensing and TTS service. A key backend problem was preventing concurrent requests from spending the same remaining credit. The implementation derives balances from a ledger, combines the check and spend inside a database transaction, and uses uniqueness constraints to make repeated operations safe. A PostgreSQL-specific test observes lock contention instead of hoping two tasks happen to overlap.

For field maintenance, I added versioned Windows updates and rollback. A real upgrade exposed a PowerShell-version incompatibility; I corrected service retargeting for the deployed environment.

**Stack:** C#, ASP.NET Core, EF Core, PostgreSQL, SignalR, Avalonia. Source is private.

<a id="announceflow"></a>
## AnnounceFlow

**Used by 3 customers in 3 locations.**

AnnounceFlow combines scheduled announcements, playlists, live audio and automatic playback policies on a Raspberry Pi, controlled through a web panel and Windows application.

Audio interruptions required looking at the sender, network and receiver together. I added diagnostic context, reduced UDP audio block size to address fragmentation, and implemented bounded recovery with cooldowns and stop/start race protection. Those changes address different failure modes; I do not treat one successful session as proof that every audio issue is solved.

**Public implementation:** [UDP block sizing](https://github.com/berkaybakac/announceflow/commit/648bec4b5db6ff57215597c63ecdffee04e65822) · [Recovery cooldown](https://github.com/berkaybakac/announceflow/commit/45edd2dc4e7ca79f2e4988d8b20c94c9c554a0c7).

**Stack:** Python, Flask, SQLite, Raspberry Pi/Linux, Windows audio capture. [Source and setup](https://github.com/berkaybakac/announceflow).

<a id="sepetarasi"></a>
## SepetArası Order Tracking

**Live in one restaurant.**

The product connects the cashier application, administration and customer order display over a local network. It includes real-time order updates, audio announcements and receipt-printing integration.

The customer's display hardware could not be treated like a modern desktop browser. I implemented a dedicated HTML compatibility renderer and display presets. I also added reconnect/snapshot recovery coverage and changed item loading from per-order queries to a batched database query.

**Public implementation:** [Display compatibility](https://github.com/berkaybakac/sepetarasi-order-tracking/commit/82da7140a523c691f7a42130c51810db5aa70477) · [Reconnect coverage](https://github.com/berkaybakac/sepetarasi-order-tracking/commit/367b58d48d6a627f20f7ed458abe79137e9cd5fa) · [Batched queries](https://github.com/berkaybakac/sepetarasi-order-tracking/commit/d3c8bce0881ee5f0b73bfe2038a84d138eacf7d7).

**Stack:** TypeScript, Fastify, React, Electron, SQLite/Drizzle, WebSocket. [Source and setup](https://github.com/berkaybakac/sepetarasi-order-tracking).
