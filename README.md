# ¶ Lorem Ipsum Generator

Private placeholder text, exactly how you need it. A **single-file, zero-dependency** Lorem Ipsum generator by **TekiDeki**.

**[Open the app](https://tekideki.github.io/Generator-Lorem-Ipsum/)** · [Apache-2.0](LICENSE) · [Support with a coffee](https://paypal.me/TekiDeki)

## Features

- Generate **paragraphs**, **sentences**, or an **exact word count**.
- Short, medium and long length presets, plus an optional “Lorem ipsum…” opening.
- Copy text, download a plain UTF-8 `.txt` file, or clear the output.
- Live word, character, sentence and paragraph counters.
- **10 interface languages:** English, Română, Srpski Latin, Српски Cyrillic, Deutsch, Français, Italiano, Español, Português and Nederlands.
- Light/dark themes, responsive layout, keyboard controls and reduced-motion support.
- Local preferences, no account, no tracking, no backend or external runtime resources.
- Installable PWA with offline support after a successful online visit.
- Translated donation button and source/license footer.

**The interface is translated; the generated text remains traditional pseudo-Latin Lorem Ipsum**, not a translation or natural-language prose generator.

## Generation rules

| Mode | Maximum | Behavior |
|---|---:|---|
| Paragraphs | 100 | Exactly the requested number of paragraphs, separated by blank lines. |
| Sentences | 500 | Exactly the requested number of sentences, in one text block. |
| Words | 10,000 | Exactly the requested number of space-separated words. No sentence punctuation is added. |

| Length preset | Sentences per paragraph | Words per sentence |
|---|---:|---:|
| Short | 3 | 9–14 |
| Medium | 5 | 14–20 |
| Long | 7 | 20–28 |

The length preset is disabled in word mode because it does not change an exact word count. Each mode remembers its own last valid count.

When enabled, the first sentence begins with **“Lorem ipsum dolor sit amet”**, followed by randomly selected words and punctuation. In word mode the opening is truncated when necessary: requesting three words returns **“Lorem ipsum dolor”**, not five words.

Word selection uses a local, deduplicated bank of common Lorem Ipsum-style tokens and `Math.random()`. Consecutive identical tokens are avoided, but repeats elsewhere are possible. Output is intentionally meaningless placeholder text; do not treat it as correct Latin, factual prose, or a cryptographic generator.

Counters use whitespace-separated words and Unicode code points for characters, including spaces and newlines. Sentence count follows generated periods. Paragraph count follows blank-line-separated text blocks, so sentence/word mode reports one paragraph and unpunctuated word mode reports zero sentences.

## Use and keyboard

1. Choose a mode, quantity and length preset.
2. Choose whether to start with “Lorem ipsum…”.
3. Press **Generate text** or **Ctrl/Cmd + Enter**.
4. Copy the output or download `lorem-ipsum.txt`.

Changing the interface language does not regenerate or translate the current output. The copy action reports success only after the clipboard API succeeds; otherwise the text is selected and a manual-copy instruction is shown. The TXT download contains exactly the displayed text, without HTML markup.

## Language links

[EN](https://tekideki.github.io/Generator-Lorem-Ipsum/) · [RO](https://tekideki.github.io/Generator-Lorem-Ipsum/?lang=ro) · [SR Latin](https://tekideki.github.io/Generator-Lorem-Ipsum/?lang=sr-Latn) · [СР Cyrillic](https://tekideki.github.io/Generator-Lorem-Ipsum/?lang=sr-Cyrl) · [DE](https://tekideki.github.io/Generator-Lorem-Ipsum/?lang=de) · [FR](https://tekideki.github.io/Generator-Lorem-Ipsum/?lang=fr) · [IT](https://tekideki.github.io/Generator-Lorem-Ipsum/?lang=it) · [ES](https://tekideki.github.io/Generator-Lorem-Ipsum/?lang=es) · [PT](https://tekideki.github.io/Generator-Lorem-Ipsum/?lang=pt) · [NL](https://tekideki.github.io/Generator-Lorem-Ipsum/?lang=nl)

A valid URL language overrides the saved preference, which overrides the browser language. English is the fallback. Switching language updates the URL, HTML language and SEO metadata, but never puts the generated text into the URL.

## PWA, offline and local use

Visit the [HTTPS app](https://tekideki.github.io/Generator-Lorem-Ipsum/) online once and let the service worker finish caching. Generation, copy where supported, TXT export and LICENSE then work offline. GitHub and PayPal links still require an Internet connection.

Supporting browsers may offer installation. The in-app **Install app** button only appears after a browser `beforeinstallprompt` event. On iPhone/iPad, use Safari → **Share → Add to Home Screen**. Browser support and policy determine availability; an automated Chromium check is not a physical-phone installation test.

For direct local use, download and open `index.html`. The app CSS/JS and word bank are embedded; no package manager, framework, CDN or build step is required. The accompanying manifest, service worker, icons and metadata support hosting and installation. `file:` URLs cannot use service workers and storage/clipboard behavior differs by browser.

For local PWA testing:

```sh
python3 -m http.server 8000
```

Open `http://localhost:8000`. Production PWA hosting needs HTTPS. The service-worker cache is scoped to this app and only deletes its own outdated caches; increment its version when updating the offline shell.

## Privacy and preferences

The `tekideki_lorem_preferences_v1` localStorage key stores only language, theme, mode, preset, the start option and per-mode counts. **Generated text is not uploaded or automatically persisted.** Copy or download anything you want to keep before reloading; a fresh output is generated when the app opens.

When storage is blocked/full, generation still works but preferences may be session-only. Site data is not encrypted, and clearing it or changing browser/device/origin can reset preferences. The hosting provider receives ordinary page/asset requests; clicking GitHub or PayPal opens those services. The application itself makes no third-party asset or analytics requests.

## SEO and verification

Includes localized titles/descriptions, canonical and hreflang links, Open Graph/Twitter image, WebApplication JSON-LD, robots and sitemap. Translations are client-rendered; indexing, preview refresh and search rankings are not guaranteed.

Tested in Chromium using Playwright on 2026-10-14:

- 270 language/mode/count/length combinations, plus maximum limits and invalid inputs;
- exact word counts, sentence lengths/counts, paragraph counts and accurate counters;
- keyboard generation, preferences, copy permission success/denial and byte-exact TXT export;
- ten languages × both themes, responsive widths from 320 to 1280 px;
- automated axe-core A/AA checks with no tested violations;
- manifest/installability checks, scoped cache, new-language-query offline navigation and offline LICENSE;
- no third-party requests, safe invalid preferences, unavailable storage and direct-file mode.

Automated checks are not exhaustive cross-browser testing or accessibility certification. The install-button interaction is also checked with a simulated browser event, not a claim of installation on a physical device.

## License

Copyright © 2026 Kristian Mario Mišković (**TekiDeki**).

Licensed under **Apache License, Version 2.0**. See [LICENSE](LICENSE) and [NOTICE](NOTICE).
