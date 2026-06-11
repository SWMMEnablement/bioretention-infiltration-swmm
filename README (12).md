# Bioretention Infiltration, Over Time

An interactive reading of Skorobogatov et al. (2026) on bioretention infiltration, mapped onto the parameters you actually edit in SWMM5, InfoWorks ICM, and a hypothetical SWMM6.

Four years of field data from 24 lined mesocosms in Okotoks, Alberta found something most of us design against: surface infiltration rose from 286 to 875 mm/h across 72 runoff events. It went up, not down. SWMM5 has exactly one parameter that changes LID performance over a run, the storage-layer clogging factor, and it only points one way (down). This app sits in that gap. It explains what the paper measured, then shows field by field where SWMM5, ICM, and a future SWMM6 can and cannot represent it.

## Live demo

- GitHub Pages: https://dickinsonre.github.io/bioretention-infiltration-swmm/ (live once Pages is enabled, see "Running it" below)
- Netlify: add your Netlify URL here after you deploy it

## What it does

Six tabs.

- **The Finding.** The 286 to 875 mm/h trajectory, the effect-size ranking (media dominates at η² = 0.89, then vegetation at 0.59), and the four hypotheses the authors scored. Charts are hand-drawn SVG, no chart library.
- **Soil Column to Params.** A clickable four-layer bioretention column. Click any layer to see the paper's reality next to the exact SWMM5 Bio-Retention Cell fields and the matching ICM SuDS fields. One column, three models.
- **SWMM5 Mapping.** The clogging-versus-maturation chart (down only against the measured up), a live `[LID_CONTROLS]` generator (pick media, vegetation, Ksat source, SI or US units, and a clogging factor, then copy or download the four layer lines), a two-column media diff, and a reverse reader. Paste any Bio-Retention Cell block and it translates every field, finds the nearest study media by Ksat, and flags whether the cell is set up to decline.
- **ICM InfoWorks.** The SWMM5-to-SuDS layer correspondence, a scenario-staging workflow (a `Mature_Yr4` scenario that overrides only soil conductivity), and a Ruby / ICM Exchange conductivity-sweep pattern you can copy.
- **SWMM6 Ideas.** Six process-module proposals written as a brief for the SWMM5+ TAC and the EWRI Stormwater committee, including a maturation term that would let Ksat climb the +6.814 mm/h-per-event slope the study measured.
- **Practice.** Eight takeaways and a clogging-factor decision helper (sediment, vegetation, IP ratio, and pretreatment in; a recommendation out).

It also carries a how-to-use modal, a guided tour, a one-click GIF walkthrough recorder, shareable deep links (the tab and every generator selection live in the URL query string), and a print layout that expands all six tabs into one report.

## How it works

One HTML file. No build step, no framework, no server. Double-click it, or host it anywhere static.

Every number in the app is the authors' measured value. Nothing is re-simulated. The generated `[LID_CONTROLS]` block and the Ruby sweep are calibrated starting points, not drop-ins. Size and validate them against your own site.

Two things worth knowing.

- The GIF button loads gif.js and html2canvas from a CDN. If your network blocks them, the button runs the guided tour instead.
- The paste-and-map reader can't know your file's units, so it gives you an mm/in toggle. Porosity, field capacity, and wilting point are ratios and don't convert. Depths and rates do.

## Running it

- **Locally.** Double-click `index.html`. It runs in any modern browser, offline (minus the web fonts and the optional GIF libraries).
- **GitHub Pages.** Settings, Pages, Source: Deploy from a branch, Branch: main, Folder: / (root), Save. Live in about a minute at the Pages URL above.
- **Any static host.** Netlify, S3, a Google Sites embed, a shared drive. It's a single file.

## The paper

Skorobogatov A, He J, Chu A, Valeo C, van Duin B. (2026). "Bioretention system infiltration: Insights into temporal evolution and impacts of design parameters." *Ecological Engineering* 230, 108020. https://doi.org/10.1016/j.ecoleng.2026.108020

Shared by Kerr Wood Leidal Associates on LinkedIn, which is where this one started.

## Credits

Built by Robert Dickinson. The science belongs to the authors above. Read their paper for the method, the statistics, and the caveats this app summarizes.

This is an independent teaching tool. It is not an official Autodesk, Innovyze, or EPA product, and it does not ship with any of them.

## License

MIT. See [LICENSE](LICENSE).
