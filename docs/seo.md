# SayType site SEO

Standard: `~/.claude/skills/frusoft-playbook/reference/seo.md`. Site: https://saytype.frusoft.dev (GitHub Pages, static).

## Scores (`seo-audit.mjs`)
- Baseline (2026-11-09, live): **9/21**
- After (live, 2026-11-09): **18/21**. Remaining 3 fails are N/A: no iOS app (apple-itunes-app, App Store link) and no `/es/` (hreflang).

## Decisions
- **No `/es/`**: the site is English only today and the demand found is English. Revisit if Search Console shows Spanish queries ("dictado por voz mac", "dictar en mac sin internet").
- Mac app: `SoftwareApplication` JSON-LD with `operatingSystem`, free offer, DMG `downloadUrl`; CTAs are DMG + Homebrew.
- Guides are static HTML in `guides/<slug>/` (Article + FAQ + Breadcrumb JSON-LD). No build script yet; two pages, hand-edited.

## Keyword research (WebSearch, qualitative; no volume data. Verify in Search Console after ~4 weeks)
Head terms ("voice typing mac", "dictation app mac", "speech to text mac") are dominated by Apple, Willow, Wispr, Superwhisper and many vendor blogs. Winnable angles are specific problems:

| # | Candidate guide | Fit with SayType | Status |
|---|---|---|---|
| 1 | Mac dictation stops by itself / after 30 seconds | Strong: SayType has no session timeout | **Drafted** |
| 2 | Dictate on Mac offline / no internet, keep voice private | Strong: local Whisper, MIT, privacy | **Drafted** |
| 3 | Dictate into Terminal / VS Code / Cursor (coding by voice, "cube cuttle" -> kubectl via Teach, per-app profiles) | Strong, real expertise, competitors are thin | Next |
| 4 | Voice commands on Mac: new line, scratch that, spoken punctuation (Apple's list vs SayType's) | Good | Candidate |
| 5 | Transcribe an audio/video file to SRT/VTT on Mac locally | Good (`saytype transcribe`, export formats) | Candidate |
| 6 | Dictate to AI coding agents (Claude Code, Codex CLI) by voice | Good, rising demand | Candidate |
| 7 | Push-to-talk vs hands-free dictation: which to use | Medium | Candidate |
| 8 | Whisper vs Parakeet on Mac: which engine, which language | Medium, niche | Candidate |
| 9 | Dictate in Spanish / other languages on Mac | Needs `/es/` decision | Later |
| 10 | Record and summarize a meeting locally on Mac | Medium, crowded | Skip for now |

## Claims to verify before publishing (Nico review)
- Guide 1: the "~30 seconds without speech" timeout is user-reported (Apple Community, vendor blogs), worded as such. Confirm on your Mac if you can.
- Guide 2: Apple's offline Dictation behavior on current macOS is deliberately hedged ("test with Wi-Fi off in Notes"). Check Settings → Keyboard → Dictation on macOS 26 and tighten the wording.
- SayType statements (0.8 s default pause, ~630 MB model, hands-free stops when focus leaves a field, 25 Parakeet languages) come from the app README/CHANGELOG.
- Guides have no screenshots yet. Add real SayType screenshots (badge, per-app profile pause setting) where readers stop.

## Your part
1. Review/approve both guides, then merge to `main` (a push to `main` publishes).
2. Search Console (`sc-domain:frusoft.dev`): submit `https://saytype.frusoft.dev/sitemap.xml`; request indexing for the two guides.
3. Import the property into Bing Webmaster Tools.
4. After ~4 weeks: `gsc-report.mjs opps` for saytype, then pick guide #3 and onward.
5. Optional: link the guides from the app's README/GitHub description.
