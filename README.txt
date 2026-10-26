KAISER FAMILY FANTASY SMX — LOCAL PROJECT WITH PROJECT-FILE STORAGE

RECOMMENDED STARTUP (saves data into this project folder)
1. Install Node.js 18 or newer if it is not already installed.
2. Open this project folder in Visual Studio Code.
3. Stop Live Server first if it is using port 5500.
4. Open Terminal > New Terminal in VS Code.
5. Run: npm start
6. Open http://127.0.0.1:5500/ in your browser.
7. Keep the terminal running while you use the website. Press Ctrl+C in the terminal to stop the local server.

League data is stored in data/league-data.json in this project folder. The file is maintained by server.js and is not exposed through ordinary website file requests. The Data & Backup page allows you to download and restore JSON backups. Back up league data before replacing files or resetting the league.

IMPORTANT MIGRATION NOTE
The first time the project server starts, bootstrap.js migrates saved localStorage data from the same browser origin into the project database if that data is newer or the project database is empty. To retain existing data, start the local server using the same exact hostname and port you used before (for example, http://127.0.0.1:5500 rather than http://localhost:5500). Browser data is separated by hostname and port. If prior data lives under a different address, open that old address and use Data & Backup to download a backup, then open the new server address and restore the backup there.

FALLBACK MODE
The pages still work under VS Code Live Server, but they will show a Browser-only storage banner. In that mode data is saved to browser localStorage, not to data/league-data.json. To save inside this project folder, stop Live Server and use npm start. If port 5500 is already in use, close Live Server and retry npm start.

DATA CATEGORIES
- kaiserFantasyAthletes: riders, nationality, number, class, manufacturer and championship flags.
- kaiserFantasyTeams: teams, ownership/password hashes and rosters.
- kaiserFantasyScores: scored results and historical team attribution.
- kaiserFantasyTrades: proposed, accepted and rejected trades.
- kaiserFantasyDraftState: manual draft picks.
- kaiserFantasyDraftSettings: draft statuses and start times.
- kaiserFantasySchedule: event dates, round numbers and event details.

HOW SAVING WORKS
The website keeps a same-origin browser cache for fast rendering and mirrors every write to the local project database. Changes appear in the status banner. A browser cache edit that is newer than a saved database value is reconciled on the next load; exports are available from Data & Backup.

PROJECT FEATURES
- Five fantasy teams and roster quotas: 5 x 250, 5 x 450, 3 x MXGP, 3 x MX2, 3 x MotoGP, 3 x F1 (22 roster spots total).
- Commissioner athlete creation/editing, nationality dropdown and flags in athlete displays.
- Manufacturer colors and logos, including Aprilia purple, Kove teal, Fantic white, ZXMoto blue, JHL red and Ducati maroon.
- Athlete tables and selectors sorted numerically by rider number.
- Race-day roster lock for team management and trade centre; schedule supports single-day and multi-day events.
- Commissioner scoring table with positions 1-22, series-specific optional bonuses, fastest lap, and Edit Scoring for previously submitted events.
- Score points stay with the team that owned the rider at scoring time. Free-agent results remain in rider history but do not score for a fantasy team unless rostered at submission.

SECURITY AND SCOPE
This is a local single-computer project, not a cloud database. Other computers/browsers do not automatically share league data. The commissioner password and frontend authorization are convenience features, not secure production authentication. Do not use real private credentials or expose the server to the public internet.
