# Sumo Brothers: privacy note

This note applies from version 0.0.14, the first version with online play. Last changed: 25 October 2026.

## In short

Sumo Brothers is a free game made by Miles. Single player never connects to anything. When you open Multiplayer,
the game signs in to our server, play.sumobrothers.net. The server runs at Hetzner in Germany. This happens for
everyone who opens Multiplayer, including people who only play LAN games. There is no account, no password, no
e-mail, no ads and no tracking. The server keeps a random online id for your game and the online name you choose.
For ranked players only, it also keeps their ranked matches. It never stores or logs your internet address. Server
logs are deleted after 14 days. To have your data removed, write to shangapallia@gmail.com.

## When the game connects

- Single player: never.
- Multiplayer: as soon as you open the Multiplayer menu, and for as long as it stays open, also in LAN lobbies and
  LAN matches. If the server does not answer, the game keeps trying while the menu is open, at most 30 seconds
  apart. Going back to the title closes the connection.
- LAN matches go straight between the computers on your network. Nothing about them is sent to our server.
- When it signs in, the game sends its version and whether it runs on Windows or Linux, so the server can check
  that versions match. The server does not keep these.
- While you are connected, the server measures your ping every 2 seconds, so it can pair you with players near you.
  It keeps these numbers only in memory, except the connection numbers in ranked match records (see "Ranked").
- The sign-in uses an encrypted connection, like a website with a padlock. The match itself is not encrypted. It
  carries your moves, your online name and your online id, but no password or key.
- The browser version of the game never connects to our server.
- If you don't want an online id at all, don't open Multiplayer. LAN games also work without our server: if the
  game can't reach it, Multiplayer still finds and joins games on your network.

## Your online id

- **What:** the first time you open Multiplayer, your game makes a long random number and saves it on your PC in
  `online_id.json`. It is not made from your computer, your Windows account or anything else about you. The server
  keeps only a scrambled fingerprint of it (it looks like `dvc:` followed by 26 letters and digits) and the date it
  first saw it.
- **Why:** so the server knows you are the same player next time. That keeps your name and your rooms, and lets you
  get back into a match after a dropped connection. It also lets the server limit how many new ids one connection
  can make.
- **How long:** on the server, for as long as online play runs. Nothing deletes old ids automatically yet. On your PC, until you delete the
  file.
- **Who sees it:** nobody else. The game never shows it.
- **Removal:** delete `online_id.json`, and your game becomes a new player. To also have the old id blocked and its
  name removed, write to shangapallia@gmail.com (see "Removing your data").

The same file keeps a sign-in pass, so the game does not have to prove itself every time. A pass lasts 7 days. After
30 days the game proves itself again with its random number. The server keeps no list of passes.

## Your online name

- **What:** "Player", until you type a name in the Name field. This is the same field LAN games use. Your computer's
  account name is never sent. A name can have at most 16 characters, and the server refuses a name that looks like an
  internet address. It keeps your current name and the times you changed it during the last day, because you can
  change it at most 3 times a day.
- **Why:** so other players can see who they are playing.
- **How long:** until you change it, for as long as online play runs. Ranked match records keep the name you had
  in each match (see "Ranked").
- **Who sees it:** everyone you play with or against, your party partner, up to 4 watchers in a private room, and,
  if you play ranked, everyone who opens the leaderboard.
- **Removal:** change it in the Name field, or ask shangapallia@gmail.com to reset it to "Player".

## Casual matches: Quick play and private rooms

- **What:** the server saves nothing about these matches: no result and no recording. The server logs only note
  that a match was played and how it ended. They use a match number and no names (see "Server logs").
- **While you play:** the others see your name and your card (stats and special). In a private room they also see
  your ping. Room codes and party codes stay in the server's memory only and are never written to the logs. A room
  closes by itself when nobody plays in it (after 5 to 30 minutes). A party exists only while it is in use.

## Ranked (Season 0: invited testers only)

- **What:** for each ranked match, the server keeps a record with:
  - who played (online ids and names) and the teams;
  - the map, who won and by how many rounds;
  - who left early or did not show up;
  - connection numbers, such as ping and lost packets.

  Your rating, rank and placement are worked out from these records.
- **Replays:** a recording of every player's moves in a ranked match. Miles can play a match back to check a
  cheating report.
- **Why:** to rate players fairly, to show ranks and the leaderboard, and to check reports.
- **How long:** match records are kept for as long as ranked runs, so ranks can be recomputed and checked. Replays
  are kept until 60 days after the end of the season they were played in.
- **Who sees it:** your name, rank, points and tier appear on the leaderboard once you have finished your placement
  matches and played enough matches that season. When a match is found, your opponents see your name and rank. Only
  Miles sees the match records and replays.
- **Removal:** you can stop playing ranked at any time. Old ranked match records cannot be erased yet. Miles can
  reset your name to "Player", and it then no longer shows on the leaderboard or to other players. The old records still hold the name you had in each match.

## Invite codes (testers)

- **What:** Miles makes a code and sends it to you privately. For each code, the server keeps a scrambled
  fingerprint of it, your tester name, the date and who made it. A code works once, within 14 days. When you use it,
  your game gets a tester key and saves it in `online_id.json`. The server keeps only a fingerprint of that key.
- **Why:** so only invited testers can play ranked in Season 0.
- **How long:** for as long as ranked runs.
- **Who sees it:** only Miles.

## Your internet address

- **What:** our server needs your address to send you the game. It sees your address while you are connected and
  keeps it only in memory. It never writes it to a file or a log. The logs of the server's web entrance remove it
  too.
- **Instead:** the server makes a short scrambled code from your address. It uses a secret key and the date, so the
  code changes every day. The server uses it to limit sign-ins, wrong room codes, new ids and new rooms per
  connection, which stops spam and code guessing. When you sign in, this code appears in the server logs next to
  your online id, for 14 days.
- **Who sees it:** other players never get your address, because everyone connects to our server and never to each
  other. No screen in the game shows an address.

## Server logs and the daily summary

- **What:** technical lines about:
  - sign-ins: your online id, how it signed in, and the daily code above;
  - matches: the match number, its kind and how it ended;
  - errors and counts.

  The logs hold no addresses, names, codes or keys.
- **Why:** to find bugs and spot attacks.
- **How long:** 14 days.
- **Who sees it:** Miles.
- **Daily summary:** the server also writes a short summary for Miles each day: counts of matches and problems,
  and the online ids of players flagged for review or banned. It stays on the server for 14 days.

## Backups

Backups are not switched on yet. Before they are, this note will say what they hold, where they are stored and for
how long.

## Other services

- **Hetzner** (Germany) runs the server and its disk. Hetzner's own privacy policy covers its network records.
- No monitoring or uptime service is used yet. If one is added, it will only get "still running" signals or the
  public page play.sumobrothers.net/status.json (how many players are online and searching, and the server's
  version), never player data, and this note will name it first.
- **GitHub:** the GitHub version of the game asks GitHub for a newer version on the title screen and downloads it
  from there. GitHub sees that request as it sees any website visit, and GitHub's privacy policy applies.
- Nothing is sold or shared for ads. The game contains no analytics or tracking code.

## On your PC

Your game keeps these files in `%APPDATA%\sumo-rpg\` on Windows, and in `~/.local/share/sumo-rpg/` on Linux:
- `online_id.json`: your id's random number, a tester key if you have one, the sign-in pass, your online id and your
  name. Keep it private: anyone with this file can play online as you.
- `online_match.json`: while you are in an online match, what your game needs to get back in after a crash. It is
  deleted when the match ends.
- `logs\godot.log`: the game's own log. It stays on your PC unless you send it to us. It can contain network
  addresses from LAN games, so read it before you share it.

## Removing your data, and questions

Write to shangapallia@gmail.com. Give your online name, and copy the line that starts with `"id"` from
`online_id.json`. Never send the whole file, because it holds your keys.

What Miles can do today:
- reset your name to "Player";
- block your id so it can no longer sign in.

Some copies stay until they expire or until the tool to erase them exists:
- old ranked match records;
- the server logs, until their 14 days are up.

## Your rights

If you live in the EU or the UK, you can ask to see, correct or delete your data, and you can object to how it is
used. You can also complain to your country's data protection authority. The person responsible for this data is
Miles, who you can reach at shangapallia@gmail.com.

## Changes

If this note changes, for example for the Steam version, the new version goes here with its date before the change
reaches the game.
