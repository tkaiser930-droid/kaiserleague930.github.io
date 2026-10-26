KAISER FAMILY FANTASY SMX — LOCAL PROJECT
Open in Visual Studio Code, then use Live Server to open index.html. Use the same Live Server origin/browser profile for all pages.

Files: index.html, teams.html, team-manage.html, available-athletes.html, all-athletes.html, commissioner.html, trades.html, draft.html, schedule.html, styles.css, app.js.

Commissioner password is set in app.js. The sign-in screen does not display a default-password hint. This is only a client-side convenience gate, not secure authentication; do not use this for real credentials or production security.

Claim a team from Teams; enter owner name and password. Team passwords are hashed with Web Crypto. Team roster quotas: 5 x 250, 5 x 450, 3 x MXGP, 3 x MX2, 3 x MotoGP, 3 x F1 (22 total). Team add/drop, draft picks and accepted trades check roster quotas. Roster lock is enforced for any scheduled event date: Team Management and Trade Center are unavailable on event days. Events can be single-day (leave End Date blank) or multi-day (set an End Date); lock dates are inclusive from start through end date, using the browser local calendar date.

RACE SCORING: The Commissioner page has a 22-place race-results table. The same SMX base-points model is used for every series: places 1–22 score 25, 22, 20, 18, 17, 16, 15, 14, 13, 12, 11, 10, 9, 8, 7, 6, 5, 4, 3, 2, 1, 0 points. SMX divides into 450/250; MXGP divides into MXGP/MX2. The Commissioner can select any listed athlete, whether rostered or a free agent. Selected rostered athletes award fantasy-team points to the team that owns them at submission; a free-agent result is saved to athlete scoring history but is not added to a fantasy team total. Bonuses can be checked independently for multiple athletes or left unused. Moto 1 winner and Moto 2 winner bonuses are each worth 5 points for SMX/MXGP. Sprint winner is worth 5 points for MotoGP/F1. All other bonuses are worth 2 points: SMX fastest qualifier and heat winner; MXGP qualifying race winner; MotoGP/F1 fastest qualifier and sprint fastest qualifier. Each score stores the rider and team-at-scoring as a historical snapshot. Later trades or drops do not transfer past points.

All data is stored in this browser's localStorage, not a server or shared database. It does not sync between computers/browsers. Starter athletes are sample data. Schedule starts empty. Each schedule event requires a round number and start date. End Date is optional for single-day events and can be set for multi-day events. Public and Commissioner schedules display date ranges, and scheduled dates drive the roster lock. Draft is a manual pick flow, not a timed snake draft. Trades are local browser proposals; both teams must use the same browser profile to share state. Do not use for real credentials or production league security.

DISPLAY UPDATE: Racing numbers are stored as text so values are not accidentally rounded or converted (including numbers with leading zeroes). Existing numbers are trimmed and a malformed starter value for Jorge Prado is corrected to 61 on load. Manufacturer badges use brand-specific colors and attempt to load logo marks from Simple Icons CDN; a network connection is needed for those logo images, while the colored brand labels remain visible if a logo cannot load.


Racing-number color fix: number plates now use manufacturer-specific background and foreground color combinations for better contrast. If you still see the old style, hard-refresh the page (Ctrl+F5) after replacing the project files.

COMMISSIONER EDIT RIDER: Sign in to the Commissioner page and use Edit Rider in the All Athletes table. The form can change name, racing number, series, race team, manufacturer, and championship/points-leader flags. Changes sync to any current roster copies. Previously recorded score history is retained as it was recorded. The save is blocked if changing series would push a team above the series roster limit.


MANUFACTURER LOGO/STYLING UPDATE: Manufacturer sidebars use each manufacturer’s assigned color, including purple for Aprilia, teal for Kove, white for Fantic, blue for ZXMoto, red for JHL, and maroon for Ducati. MotoGP/F1 racing-number plates retain team/manufacturer-colored numbers on black, and 250/MX2, 450/MXGP, champion, and points-leader priorities are unchanged. Honda uses the motorcycle Wing logo; Yamaha uses the tuning-fork emblem; Triumph uses the inverted-triangle mark; Aprilia uses a lion-head mark. Logo images loaded from external hosts require an internet connection. All manufacturer names remain visible if an image fails to load.
Manufacturer logos
------------------
The Haas circular H/A emblem, Beta vector-B emblem, Kawasaki K mark, Mercedes three-pointed star, and Williams W mark are connected to image URLs used in the branding update. The Alpine pink A logo is included locally at assets/logos/alpine-pink-a.png. Internet access is required for the five externally hosted logos; if an external host blocks an image, the manufacturer name will still appear as a fallback.

NATIONALITY FLAGS: Commissioner Add Athlete and Edit Rider forms have a nationality dropdown. Nationality flags appear beside rider names in athlete listings, team rosters, commissioner tables, scoring history, draft picks, and trade displays. Known sample riders are prefilled with their established nationality when the project first loads; add nationality to custom/previously blank riders through Commissioner > Edit Rider. Flags use Unicode country symbols and may depend on the operating system font.

MANUFACTURERS ADDED: Kove (teal), Fantic (white), ZXMoto (blue), JHL (red). Ducati is maroon. The four new logo marks are loaded from the image source URLs in app.js; text labels stay visible if a remote logo fails to load.


NUMERIC RIDER ORDER: Athlete-facing tables (All Athletes, Available Athletes, Commissioner athlete list, team rosters, scoring history, and draft pick list) sort by racing number ascending. Numeric sorting uses the number value while the displayed racing-number string is preserved; leading zeroes are not stripped. Free-agent, scoring, draft, and trade athlete choices use the same numeric order. Schedule, standings, and trade-history rows retain their natural date/transaction ordering.
JHL WORDMARK: Added a local red JHL letter-only wordmark at assets/logos/jhl-wordmark.svg, based on the JHL/JHLMOTO wordmark reference at https://jhlmoto.ru/image/catalog/logo.png. It shows the requested letters without an added pictorial icon and falls back to a JHL text label if the image is unavailable.
Scoring updates:
- SMX bonus options: Fastest qualifier, Heat winner, Moto 1 winner, Moto 2 winner.
- MXGP bonus options: Moto 1 winner, Moto 2 winner, Qualifying race winner.
- MotoGP and F1 bonus options: Sprint winner (5), Fastest qualifier (2), and Sprint fastest qualifier (2).
- Moto 1 winner and Moto 2 winner are worth 5 points each; Sprint winner is worth 5 points. Fastest lap is worth 1 point for all series. All other non-winner bonuses are worth 2 points. Bonuses can be left unused or awarded to multiple riders.
- Commissioner dashboard includes a Previously Scored Events table with Edit Scoring. Saving an edit replaces the prior results for that event/series/division instead of duplicating them. Previous team attribution is preserved for riders already in that result group.
- When editing older SMX/MXGP results that used the former generic “Moto winner” bonus, select the correct Moto 1 or Moto 2 replacement bonus; the old record does not identify which moto was won.

LATEST SCORING / UI UPDATE
- Added a +1 Fastest lap checkbox for every scoring series (SMX, MXGP, MotoGP, and F1).
- Commissioner password updated in app.js; the local password hint has been removed from the login screen. As this is client-side JavaScript, the password is not secure against inspection by someone with access to the project files.
- Racing number plates are slightly larger and use the more aggressive Teko display font, with Impact / Arial Black fallbacks. Google Fonts requires an internet connection; fallback fonts are used if it cannot load.
