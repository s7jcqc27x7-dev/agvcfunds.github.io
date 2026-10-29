# Ag Ventures — site update (v5)

Supersedes every earlier folder. Deploy this one only.

## 1. Logo — now embedded, no upload required
You saw text instead of the logo because the browser was falling back to alt
text: /images/agventures-wordmark.png was not present on the deploy. That is
the second time the mark has vanished for the same reason, so I removed the
dependency instead of renaming the file again.

The wordmark is now a base64 data URI inside each page's stylesheet, applied as
a background on .av-mark (one copy per page, shared by the nav, hero and footer
sizes). The favicon is embedded the same way. Nothing in /images/ is needed for
either to appear.

Verified by blocking every /images/ request in a headless browser: the wordmark
still renders in the nav, hero and footer.

Source: AgVentures_SilverBlue_horizontal_transparent (the light variant, which
is the one that reads on the dark bar), trimmed to its ink box and resampled to
832x120 — about 3x the largest on-screen size, so it stays crisp on retina.
Cost: roughly +35KB per page. Markup is now
  <span class="av-mark nav" role="img" aria-label="Ag Ventures"></span>
so it stays accessible to screen readers.

TRADE-OFF: changing the logo later means regenerating the pages rather than
swapping one file. Say the word if you would rather go back to a linked file
once /images/ is reliably populated.

The full-resolution agventures-wordmark.png and a 512px agventures-mark.png are
still in images/ for decks, email signatures and social cards.

## 2. Team page
Removed: Doug Nissinoff, Dr. Rima Patel, Elena Liapounova, Sergei Petukhov.
(Donny Siu went in the previous round.) Justin and Aaisha remain.

Their photo files are no longer referenced and can be deleted from /images/:
  doug-nissinoff.jpg, rima-patel.jpg, elena-liapounova.jpeg, sergei-petukhov.jpeg,
  donny-siu.jpg

The grid was a fixed 3 columns, which would have left two cards stranded beside
an empty third. It is now auto-fit with a 360px max track, so two cards sit
correctly and it returns to three across by itself if you add people back.

## Images to upload to /images/
  event-longevity-tech-summit-2026.jpg
  partner-investhk.png / partner-hkstp.png / partner-ayari.png
  (agventures-*.png are optional now — the site no longer reads them)

## STILL PENDING from earlier rounds
  git mv services.html longevitysprint.html
Without the rename the leftover file shadows the /services -> /longevitysprint
301 in netlify.toml.

## Open items — unchanged, your call
1. The Longevity Tech Summit CTA points at /#contact; no registration URL yet.
2. The Science Pulse card could not be verified — science.org blocks automated
   requests. Labelled "2026 · Science", blurb written from the title.
3. AYARI is your own affiliate, shown beside InvestHK and HKSTP with no
   related-party disclosure.
4. about.html and longevity-asia.html still carry a different nav from the other
   five pages, and still have --serif/--sans inverted.
