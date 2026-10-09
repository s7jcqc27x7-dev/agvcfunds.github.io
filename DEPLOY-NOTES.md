# Deploy notes

## Rename (in git, not by uploading)
    git mv services.html longevitysprint.html

Then overwrite with the file here. `services.html` must not remain in the repo —
the /services 301 below would be shadowed by a leftover file.

## What changed this round
longevitysprint.html   Centred Longevity Sprint wordmark + intro paragraph added
                       above the page header. Now uses
                       /images/Longevity-Sprint_transparent.png.
                       The onerror="hide" handler was REMOVED — that is what made
                       the logo disappear silently last time. If the filename is
                       ever wrong you will now see a broken image instead of
                       nothing, which is the failure you want.

longevity-asia.html    The whole "Deep Dive — China" block had NO CSS at all
                       (.china-stats, .china-stat, .china-stat-val, .china-stat-label,
                       .china-stat-src, .china-opp-grid, .china-opp, .china-opp-icon,
                       .china-opp-title, .china-opp-body were all undefined).
                       It was rendering as 14px unstyled text. Rules added,
                       mirroring .geo-stat* / .geo-opp* on the same page.

all pages              Stat-unit accent unified on var(--gold). Some pages used
                       var(--teal) for the same component. Both are #c4a46b today,
                       so nothing changes visually — but they could drift apart on
                       any future palette edit.

## Images
No new uploads needed. Uses files already in /images/:
  Longevity-Sprint_transparent.png             hero wordmark (CSS-cropped)
  Longevity-Sprint_black.png                   og:image
  Longevity Global.jpeg / InvestHK.png / BIOHK.png   partner chips

## Open item — NOT changed, needs your call
about.html and longevity-asia.html define --serif and --sans INVERTED
relative to index / intelligence / team / partnering / longevitysprint:

  those two pages   --serif:'Satoshi'...(a sans)   --sans:'Noto Serif'...(a serif)
  every other page  --serif:'Noto Serif'...        --sans:'Inter'...

So headings render in Satoshi and body copy in Noto Serif on those two pages,
and the reverse everywhere else. Swapping the two values in those two files is a
two-line fix, but it restyles both pages, so it is left alone.
