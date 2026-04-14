# 🏏 Cricket Live Score Widget — Tasker + KWGT

A Tasker automation project that scrapes live cricket scores from **Cricbuzz** and pushes real-time match data to a **KWGT** home screen widget. Supports IPL, Test matches, ODIs, T20Is, and any match available on Cricbuzz.

---

## 📱 Features

- **Live score updates** refreshed every 5 minutes automatically
- **Match state detection** — In Progress, Innings Break, Lunch, Tea, Stumps, and other interruptions
- **Batsman details** — current batsmen, runs, balls, partnerships
- **Bowling figures** — current bowler stats
- **Recent balls** — last 10 deliveries shown on widget
- **Run rates** — Current RR, Required RR, Projected Score
- **Last wicket** info displayed on widget
- **Match format** detection (Test / ODI / T20)
- **Streaming link** support
- **IPL Schedule** from Google Calendar integration
- **Share a Cricbuzz link** directly from browser to trigger a new match
- **Auto-refresh toggle** — enable or disable periodic refresh
- **Visual loading indicator** — colour-coded dot shows fetch status (red = loading, transparent = done)
- **Team name abbreviation** — full names auto-shortened (e.g., Royal Challengers Bangalore → RCB)

---

## 🗂️ Project Structure

### Profiles (Triggers)

| Profile | Trigger | Linked Task |
|---|---|---|
| **Refresh Cricket** | Time — every 5 minutes | Parse Cricbuzz |
| **IPL Calendar** | Google Calendar event: `IPL_2025` | Match Links |
| **Receive Link** | Share Received event | Receive Link |

### Tasks

| Task | Purpose |
|---|---|
| **Parse Cricbuzz** | Core task — fetches and parses the Cricbuzz match page |
| **CricBuzz LATEST** | Clears old score variables before a fresh fetch |
| **Display Cricbuzz Score** | Pushes parsed data to KWGT via Kustom Tasker plugin |
| **Progress** | Detects match state (Progress / Innings Break / Lunch / Tea / Stumps) |
| **Clean Match Progress** | Strips full team names → abbreviations in the CPROG variable |
| **Last wicket And Bowler** | Extracts last wicket and current bowler details |
| **Input Link** | Dialog to manually enter a Cricbuzz match URL |
| **Receive Link** | Accepts a shared Cricbuzz URL from any browser |
| **Match Links** | Stores and manages the active match URL |
| **IPL_Schedule** | Reads upcoming IPL match from Google Calendar |
| **Toggle Auto Refresh** | Enables or disables the 5-minute refresh profile |
| **Streaming** | Handles streaming link for the match |
| **Clear / Clear score** | Resets widget variables to blank state |
| **Read cal** | Reads Google Calendar for next IPL fixture |

---

## 📡 KWGT Variables

Tasker pushes the following variables to the KWGT widget via the **Kustom Tasker Plugin**:

| Variable | Description |
|---|---|
| `CSCORE` | Main innings score (Team 1) |
| `CSCORE2` | Second innings / Team 2 score |
| `T1SCORE` | Team 1 full score string |
| `T2SCORE` | Team 2 full score string |
| `MATCH` | Match title / teams |
| `SERIES` | Series name |
| `FORMAT` | Match format (Test / ODI / T20) |
| `CPROG` | Match progress / status text |
| `BATSMEN` | Current batsmen at crease |
| `BATSMENDET` | Batsman details (runs, balls, 4s, 6s) |
| `BATONE` | Batsman 1 name |
| `BATTWO` | Batsman 2 name |
| `BATRUNS` | Batsman runs |
| `CURBAT` | Current striker info |
| `CRR` | Current Run Rate |
| `RRR` | Required Run Rate |
| `PCRR` | Projected score |
| `REQRR` | Required run rate display |
| `OVERREM` | Overs remaining |
| `PSHIP` | Current partnership runs |
| `NPSHIP` | Partnership balls |
| `LASTWKT` | Last wicket details |
| `LST10` | Last 10 deliveries (recent balls) |
| `RECENTN` | Recent commentary / events |
| `CRECENT` | Recent ball-by-ball |
| `MATCHDET1` | Match detail line 1 (venue, date) |
| `MATCHDET2` | Match detail line 2 |
| `NTNAMES` | Team names |
| `NMSTATUS` | Match status message |
| `PERFORM` | Player performance highlight |
| `MLINK` | Active Cricbuzz match URL |
| `START` | Match start time |
| `STREAMING` | Streaming platform / link |
| `COVERS` | Cover/rain interruption status |
| `COLOR` | Loading indicator dot colour |
| `AUTOR` | Auto-refresh status |

---

## ⚙️ Requirements

| App | Purpose |
|---|---|
| [Tasker](https://play.google.com/store/apps/details?id=net.dinglisch.android.taskerm) | Automation engine |
| [KWGT](https://play.google.com/store/apps/details?id=org.kustom.widget) | Home screen widget |
| [Kustom Tasker Plugin](https://play.google.com/store/apps/details?id=org.kustom.tasker) | Bridge between Tasker and KWGT |
| Google Calendar | IPL schedule auto-detection (optional) |

---

## 🚀 Setup Instructions

### 1. Import Tasker Project
1. Copy `New_Cricket_prj.xml` to your phone's Tasker backup folder (usually `/Tasker/` on internal storage).
2. Open Tasker → long-press the Home icon (Projects tab) → **Import Project**.
3. Select `New_Cricket_prj.xml`.

### 2. Import KWGT Widget
1. Copy `Cricket_April_2026.kwgt` to your phone.
2. Add a KWGT widget to your home screen.
3. Tap the widget → tap the folder icon → **Import** → select `Cricket_April_2026.kwgt`.

### 3. Grant Permissions
- Allow Tasker to access the internet.
- Allow Tasker to read Google Calendar (for IPL schedule feature).
- Enable the **Kustom Tasker Plugin** within Tasker settings.

### 4. Set a Match Link
There are three ways to load a match:

**Option A — Share from browser:**
Open any Cricbuzz match page in Chrome/Firefox → Share → Tasker → the match loads automatically.

**Option B — Manual input:**
Run the **Input Link** task from Tasker → paste the Cricbuzz URL in the dialog.

**Option C — IPL Calendar (automatic):**
Add your IPL match as a Google Calendar event titled `IPL_2025`. Tasker will auto-detect it and queue the match.

### 5. Enable Auto-Refresh
Run the **Toggle Auto Refresh** task to activate the 5-minute refresh profile. The widget dot turns **red** during each fetch and goes **transparent** when done.

---

## 🔄 How It Works

```
Cricbuzz match page (HTML)
        ↓
Tasker fetches via HTTP GET
        ↓
Parse Cricbuzz task extracts:
  - Scores, overs, run rates
  - Batsmen, bowler, partnership
  - Match state (Progress / Break / Stumps etc.)
  - Last wicket, recent balls
        ↓
Clean Match Progress task
  (abbreviates team names: "Mumbai Indians" → "MI")
        ↓
Display Cricbuzz Score task
  pushes variables → Kustom Tasker Plugin → KWGT widget
        ↓
Home screen widget updates live ✅
```

---

## 🏟️ Supported Match States

The widget correctly displays the following match states parsed from Cricbuzz HTML:

- 🟢 In Progress
- 🍽️ Lunch Break
- 🍵 Tea Break
- 🌙 Stumps
- 🔄 Innings Break
- ⛈️ Covers / Rain Interruption
- ⏸️ Other stoppages

---

## 🏏 Team Abbreviations (IPL)

The **Clean Match Progress** task automatically shortens team names:

| Full Name | Short |
|---|---|
| Mumbai Indians | MI |
| Chennai Super Kings | CSK |
| Royal Challengers Bangalore | RCB |
| Kolkata Knight Riders | KKR |
| Delhi Capitals | DC |
| Rajasthan Royals | RR |
| Sunrisers Hyderabad | SRH |
| Lucknow Super Giants | LSG |
| Punjab Kings | PBKS |
| Gujarat Titans | GT |

International teams (India, Australia, England, Sri Lanka, etc.) are similarly abbreviated.

---

## 📝 Notes

- The project scrapes the **public Cricbuzz website** (`www.cricbuzz.com` and `m.cricbuzz.com`). No API key is required.
- Parsing relies on Cricbuzz's HTML class names (e.g., `cb-text-inprogress`, `cb-text-stumps`). If Cricbuzz changes their markup, some tasks may need updating.
- The widget file (`Cricket_April_2026.kwgt`) is versioned for April 2026. Variable names must match exactly between Tasker and KWGT for the widget to display correctly.

---

## 🤝 Contributing

Pull requests are welcome for:
- Support for additional leagues (WPL, The Hundred, BBL, etc.)
- Improved HTML parsing resilience
- Additional widget layouts

---

## 📄 License

This project is shared for personal and educational use. Cricbuzz is a third-party website — use responsibly and in accordance with their terms of service.
