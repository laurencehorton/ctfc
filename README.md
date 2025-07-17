# Cheltenham Town Association Football Club: 1989–2025

## Table of Contents

- [About](#about)
- [Version](#version)
- [License](#license)
- [Contact](#contact)
- [Value Definitions](#cvalue-definitions)
- [Variable Definitions](#variable-definitions)
  - [Game Metadata](#game-metadata)
  - [Competition and Venue](#competition-and-venue)
  - [Attendance and Outcome](#attendance-and-outcome)
  - [Player Participation](#player-participation)
  - [Disciplinary Records and Goals](#disciplinary-records-and-goals)
- [Known Issues](#known-issues)
- [Data Sources](#data-sources)
- [Changelog](#changelog)
- [Detailed Known Issues](#detailed-known-issues)

---

## About

This dataset contains information on first-team matches, goals, player appearances, and disciplinary actions for Cheltenham Town AFC from the 1989/90 season through the 2024/25 season.  

It covers 1,943 matches, 36 seasons, 14 competitions, and 1,225 players.

Usage is intended for football researchers, football historians, and data scientists, but not limited to these groups.  

The data are available for download in UTF-8 encoded CSV format. CSV file includes headers. 

## Version
cheltenham_game_1.0.csv

## License

Distributed under a Creative Commons Zero (CC0) license.

## Contact

- Contact: hortonlaurence@gmail.com.
- Project Link: https://github.com/laurencehorton/ctfc.

## Value Definitions

- `NA`: The variable does not apply to this case.
- Blank value: Information does apply but is missing and hopefully can be added later.
- `0`: Zero value.

## Variable Definitions

### Game Metadata

- `game_season`: Integer. Season identifier in `YYYYYYYY` format, covering July 1 to June 30.
- `game_match`: Integer. Sequential number of the match within the season.
- `game_league_match`: Integer. Sequential number of league matches within the season.
- `game_date`: Integer. Local date of the match (`YYYYMMDD`).
- `game_kickoff`: Integer. Local kickoff time (`HHMM`). Blank value indicates missing data.
- `game_kickoff_type`: Integer. Kickoff time category. `0` = 15:00, `1` = 19:45, `2` = other.

### Competition and Venue

- `game_opponents`: Character. Name of the opposing team.
- `game_venue`: Character. Ground where the match was played. Sponsorship names excluded unless original.
- `game_venue_type`: Integer. Venue type. `0` = Home, `1` = Away, `2` = Neutral.
- `game_competition`: Character. Initials of the competition (e.g., `EFL`, `FAC`). Sponsorship titles generally avoided.

**Competition Key**:  
`APL`: Alliance Premier League. League competition at level 5 of the English football league system. Also known as the GM Vauxhall Conference (1986-1998), Nationwide Conference (1999-2004), Vanarama National League (2015-).  
`CCS`: Conference Charity Shield. One-off game between winners and runners-up in the previous season's APL.  
`CLC`: Conference League Cup. Knock-out cup competition open to members of the APL. Also known as the Bob Lord Trophy from 1979-2001.  
`EFL`: English Football League. League competition at levels 2 to 4 of the English football league system. Also known as the Nationwide Football League (1996-2004), Coca-Cola Football League (2004-2010), npower Football League (2010-2013), Sky Bet Football League (2013-2016), Sky Bet EFL (2016-).  
`FAC`: Football Association Challenge Cup competition. Knock-out cup competition open to clubs from level 1 to 9 of the English football league system. Clubs at level 5 enter the competition in the fourth preliminary round. Clubs at levels 3 and 4 enter the first round proper. Clubs at levels 1 and 2 join from the third round proper.  
`FAT`: English Football Association Challenge Trophy competition. Knock-out cup competition only open to clubs in the English league system at level 5 or below.  
`FAW`: Football Association of Wales Welsh Cup. Knock-out cup competition open to clubs playing in the Welsh or English league system from areas bordering Wales were able to participate.  
`FLC`: English Football League Cup competition. Knock-out cup competition only open to clubs at level 1 to 4 of the English league system. Also known as Worthington's Cup (1998-2003), Carling Cup (2003-2012), Capital One Cup (2012-2016), EFL Cup (2016-2017), and Carabao Cup (2017-).  
`FLP`: English Football League Play-Offs. End of season knock-out promotion play-off competition for EFL clubs.  
`FLT`: English Football League Trophy. Knock-out cup competition that features group stages in its early rounds from 2016. Open to clubs at level 3 and 4 of the English league system. Also open to some level 5 clubs from 2000 to 2006 and Under-21 teams from the level 1 and level 2 clubs from 2016-. Competition also known as Auto Windscreens (1994-2000), LDV Vans (2000-2007), Johnstone's Paint (2007-2016), Checkatrade (2016-2019), Leasing.com (2019-2020), and Papa John's Trophy (2020-2023).  
`GSC`: Gloucestershire Football Association Northern Senior Professional Cup. Knock-out cup competition featuring clubs from the north of the county of Gloucestershire (above Thornbury) until the 1990s when it became known as the Gloucestershire Cup and clubs from the Bristol area could join. Ceased to be a first team competition after 1998/99.  
`MFC`: Midland Floodlit Cup. Knock-out cup competition.  
`SFL`: Southern Football League. League competition at level 5 (1979-2004) of the English football league system. Also known as the Beazer Homes League (1987-1996) and Dr Martens League (1996–2004).  
`SLC`: Southern Football League Cup. Competition open to members of the Southern Football League.  

- `game_level`: Numeric. League level (e.g., `1` = Premier League). For cups, indicates round (e.g., `1.1` = first round, first leg). Preliminary round games feature a zero value followed by a point decimal separator and then the round of the competition.

### Attendance and Outcome

- `game_attendance`: Integer. Reported total match attendance.
- `game_away_attendance`: Integer. Reported away supporter attendance.
- `game_home_attendance`: Integer. Home attendance = total minus away attendance.
- `game_outcome`: Integer. Match result. `3` = Win, `1` = Draw, `0` = Loss. Penalty shootouts are excluded.
- `game_goals_for`: Integer. Goals scored by Cheltenham.
- `game_goals_against`: Integer. Goals conceded.
- `game_manager`: Character. First name and last name of Cheltenham manager(s), including caretakers.
- `game_division_position`: Integer. League position after the match.
- `game_pyramid_position`: Integer. Overall English league system position after the match.
- `game_cumulative_points`: Integer. Cumulative points obtained in league competition that season after a match.

### Player Participation

- `game_p1` to `game_p11`: Character. Unique ID for each starting player (`NNNN_First_Last`).

  - Format: Last two digits of first season + order of debut.
  - Missing: `9998_Missing_Name`.
  - Missing component (e.g., first name): replaced with `?`.

- `game_p1mins` to `game_p11mins`: Integer. Minutes played by each starter.

  - Range: `1` to `90` (or `120` if extra time).
  - Substitution times: e.g., `45` = halftime.
  - Dismissals: time of sending off.
  - Missing or partial data: left blank or best estimate.

- `game_s1` to `game_s9`: Same format as starters for substitutes.

  - Unknown: `9998_Missing_Name`
  - Not named: `NA`

- `game_s1mins` to `game_s9mins`: Minutes played by each substitute.

  - Range: `1` to `89` (or `119` if extra time).
  - Stoppage time entry: `1`
  - Missing substitution time: left blank.

### Disciplinary Records and Goals

- `game_goal1` to `game_goal8`: Goalscorer ID. Own goals: `9999_Own_Goal`.
- `game_yellow1` to `game_yellow6`: IDs of Cheltennham players cautioned (up to twice each).
  - Not recorded before 1999/00.
- `game_red1` to `game_red2`: IDs of Cheltenham players dismissed (non-repeating).
  - Red cards not systematically tracked before 1999/00.

## Known Issues

- Missing kickoff time (`game_kickoff`, `game_kickoff_type`) for seasons 1989/90 to 1999/2000.
- Missing division and pyramid positions (1992/93 to 1996/97).
- Gaps in `game_away_attendance` between 1989/90 and 2014/15.
- Several missing player names and minute data for early seasons (listed in detail above).

## Data Sources

- **1989–1999**: Local newspaper match reports via the British Newspaper Archive, primarily those of the _Gloucestershire Echo_.
- **2000–2002**: Results pages from the _Sunday Telegraph_ augmented by local newspaper match reports via the British Newspaper Archive, and match data on soccerbase (https://www.soccerbase.com/teams/team.sd?team_id=579&season_id=157&teamTabs=results) and 11v11 (https://www.11v11.com/teams/cheltenham-town/).
- **2002–2014, 2015/16**: Match pages on ESPN (https://www.espn.co.uk/football/team/results/_/id/320/eng.cheltenham) and transfermarkt (https://www.transfermarkt.co.uk/cheltenham-town/spielplandatum/verein/3371).
- **2016–Present**: fbref match pages (https://fbref.com/en/squads/7c4744f7/history/Cheltenham-Town-Stats-and-History).  
Where data sources cover the same period they have been used to cross-reference information.  

## Changelog


## Detailed Known Issues  
Missing away attendence figures for:  
- game_season 20122013, game_match 28 to 54.  
- game_season 20162017, game_match 27.  
- game_season 20182019, game_match 21.  
- game_season 20192020, game_match 22.  
- game_season 20192020, game_match 37.  
- game_season 20242025, 3, 31, 37, 50.  
- game_season 20152016, game_match 4, 8, 33, 35, 43.  
- game_season 20232024, 10, 44, 49.  
- game_season 20222023, game_match 5, 16, 19, 52.  
- game_season 20212022, game_match 6, 20, 23, 26.  

Missing players.  
- game_p1 to game_p11 for game_season 19921993, game_match 1 to 2, 4 to 7, 9 to 11.   
- game_s1 and game_s2 for game_season 19921993 game_match 1, 4 to 7, 10 and 11.  
- game_s2 for game_season 19891990, game_match 1 and game_match 3.  
- game_s2 for game_season 19901991, game_match 1.  
- game_s2 for game_Season 19921993, game_match 8.  
- game_s2 for game_Season 19921993, game_match 11 and 22.  

Missing minutes.  
- game_season 19891990, game_match 1, game_s2mins.  
- game_season 19891990, game_match 3, game_p8mins, game_s1mins, game_s2mins.  
- game_season 19891990, game_match 30, game_p6mins, game_s1mins.  
- game_season 19891990, game_match 32, game_p11mins, game_s2mins.  
- game_season 19891990, game_match 53, game_p6mins, game_s1mins.  
- game_season 19891990, game_match 4, game_s2mins.  
- game_season 19901991, game_match 20, game_p11mins.  
- game_season 19901991, game_match 20, game_s2mins.  
- game_season 19901991, game_match 26, game_p1mins to game_s4mins.  
- game_season 19911992, game_match 17, game_p8mins.  
- game_season 19911992, game_match 17, game_s2mins.  
- game_season 19921993, game_match 8 and 9, game_s1mins.  
- game_season 19921993, game_match 8, game_p8mins.  
- game_season 19921993, game_match 9, game_s2mins.  
- game_season 19961997, game_match 17, game_p3mins.  
- game_season 19961997, game_match 17, game_s3mins.  
- game_season 19981999, game_match 10, game_s1mins.  
- game_season 19981999, game_match 10, game_s2mins.  
- game_season 19981999, game_match 10, game_s3mins.  
- game_season 19981999, game_match 35, game_p6mins.  
- game_season 19981999, game_match 35, game_s1mins.  
