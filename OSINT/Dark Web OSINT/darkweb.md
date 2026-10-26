**Dark Web OSINT**

Dark Web OSINT is the collection of publicly available information from the dark web—the part of the internet that needs special software, usually Tor, to access. Forums, markets, and paste sites there can reveal early threat signals, credential dumps, malware chatter, or how criminal groups organize. Security teams and researchers use it for that reason. It is also noisy, full of lies, and carries real legal and operational risk.

Stay passive and stay legal. Collect only what is openly posted. Do not create accounts to dig deeper, message people, download “tools,” or push any access that could look unauthorized. Laws and company policies differ; know yours. Never seek or keep prohibited material such as child sexual abuse content. If you run into it, note the bare minimum, disconnect, and report through proper channels.

**Setup and basic hygiene**
- Work from an isolated environment with no personal or work accounts—Tails or Whonix on external media or a throwaway VM is ideal.
- Use Tor Browser; keep JavaScript off for higher-security work. A VPN in front of Tor is optional and sometimes adds more trust issues than it solves.
- Treat every download as hostile. Open files only in a disposable sandbox, if at all. Prefer screenshots and notes.
- Use strong unique passwords, keep everything patched, and never mix identities.

**Collection and analysis**
- Browse methodically. Dark-web search engines can help locate starting points, but verification is everything—cross-check claims, look at poster history, and treat single-source tips as unproven.
- Record exact URLs, timestamps, and hashes of anything you save. Store it securely and wipe temporary copies when finished.
- Be ready to disconnect the moment something feels off. Scams, phishing, and honeypots are common.

Dark Web OSINT is quiet observation, not infiltration. The same anonymity that makes it useful also makes it a place of traps and malware. Hardened setup, skepticism, clean records, and clear legal lines keep the work both useful and defensible.

Here’s a practical expansion on the tools you already have. I focused on ones that still show up regularly in current OSINT discussions and GitHub lists (as of late 2025–2026). Many of these are open-source; a few are clearnet services that index onion content. Always run them from an isolated setup and stick to passive collection.

### Additional search & discovery tools
- **Ahmia** — One of the cleaner, more research-friendly onion search engines (clearnet + onion access). Filters a lot of the worst material.
- **Darkus** — Command-line onion searcher, similar spirit to OnionSearch/Darkdump.
- **Torch** — Long-running, large-index search engine. Broader (and noisier) than Ahmia.
- **Haystak** — Larger index with some structured/filter options; free tier is limited.
- **Tor66 / TorNode** — Useful for fresh onion link lists rather than full-text search.
- **OnionEngine / Onion Search Engine** — Another multi-source search option that sometimes surfaces different results.
- **Robin** — Newer AI-assisted helper that can generate better queries and help process results (from the same maintainer as one of the popular tool lists).

### Scanners & link checkers
- **Onioff** — Lightweight onion URL inspector/status checker.
- **Onion-nmap** (Docker version) — Lets you run nmap-style scans against onion services through Tor.
- **nao1215/onionscan** — Modern Go rewrite of the classic OnionScan; better support for current v3 addresses and concurrent work.

### Extra crawlers & collectors
- **Darc** — Distributed archival-style crawler.
- **Prying Deep** — Focused on gathering and analyzing dark-web data for threat intel.
- **Midnight Sea** — Research-oriented crawler, sometimes used for market-related mapping.
- **Fresh Onions** (and related torscraper projects) — Classic approach for discovering and tracking live onions.
- **AIL Framework** — Broader than a pure crawler; good for ingesting, correlating, and monitoring leaks/pastes/onion content in a pipeline.

### Broader OSINT platforms & resources worth knowing
- **SpiderFoot** — Automates a lot of pivoting (including some dark-web modules) and is useful once you have seeds.
- **Intelligence X** — Strong for historical/leak searches that often overlap with dark-web material; clearnet interface.
- **Hunchly** (you already listed it) remains one of the best for clean, timestamped capture of what you actually visit.
- **DeepDarkCTI** (you have it) is still the go-to community list of forums, markets, ransomware blogs, Telegram channels, etc.
- Curated GitHub lists such as `apurvsinghgautam/dark-web-osint-tools` are handy living indexes—check them periodically because tools appear and die quickly.

A few practical notes:  
Many of the pure crawlers (TorBot, TorCrawl, etc.) need a working Tor SOCKS proxy and can be brittle. Prefer tools that stay read-only. Commercial platforms (DarkOwl, Recorded Future, etc.) exist for continuous monitoring if you need scale, but the open-source options above cover most manual or small-team work.  

Test anything new in a disposable VM first, keep JavaScript disabled when possible, and document exactly what you collect. The landscape changes fast, so verify a repo’s last update before relying on it.