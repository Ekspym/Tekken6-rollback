# Tekken 6 rollback (RPCS3)

Modified RPCS3 with rollback netcode (GGPO principle) for Tekken 6 online play (PS3, BLUS30359 v1.03) over RPCN.
Works in Player Match and Ranked Match.

Download: see **Releases** (`tekken6_rollback.zip`). The package contains neither the PS3 firmware nor the game.
Both players must use the same build. Start the game with `play_online.bat`.

```
TEKKEN 6 (PS3, RPCS3) - ONLINE WITH ROLLBACK NETCODE
=====================================================

What is this
------------
A modified RPCS3 that gives Tekken 6 online matches (RPCN: Player Match and Ranked Match)
rollback netcode, the same principle as GGPO. Instead of waiting for your opponent's input,
the game predicts it. When a prediction was wrong, the game goes back a few frames
(rollback, at most 5 frames) and re-simulates them with the real input. Your own character
is never rolled back. Only the opponent can "jump" slightly.
The input delay is set automatically: 1 frame (~17 ms) up to ~100 ms ping, plus one frame more
on worse connections so the game does not have to wait. Intros, KO scenes and replays run with
a larger delay so they stay smooth (your inputs there only skip the scene).

Both players MUST have:
  - this exact same build of RPCS3 (this package),
  - Tekken 6 USA (BLUS30359) with update 1.03,
  - a CPU with AVX2 (Intel Core 4th gen or newer, any AMD Ryzen).
A player with an unmodified RPCS3 or a different build cannot play with you reliably
(the match would desync).

Installation (first time only)
------------------------------
1. Extract the package into its own folder (not into Program Files).
2. Start rpcs3.exe.
3. File > Install Firmware: install the PS3 firmware (download PS3UPDAT.PUP from the official
   PlayStation website).
4. Add the game (File > Add Games) and install update 1.03 (File > Install Packages/Raps/Edats).
5. Configuration > RPCN: log in with your RPCN account (or create one there).
6. Do NOT change the game's settings. The file config\custom_configs\config_BLUS30359.yml must be
   identical on both PCs (it makes both PCs compute the game bit for bit the same way).
7. Close RPCS3.

Playing
-------
1. Start play_online.bat. RPCS3 opens with the rollback settings. Starting rpcs3.exe directly,
   without the .bat, gives you NO rollback. The delay is automatic. A fixed delay is only for
   special cases, e.g.: play_online.bat 2
2. In RPCS3 start Tekken 6 and go to Online Mode.
   Player Match: one player creates a session (Create Session), the other joins
   (Custom Match > Search > Join). Ranked Match works too.
3. Play normally. A stable connection matters (cable is better than Wi-Fi). When packets stop
   arriving for a moment, the game waits (like the original online mode). It never guesses
   further than the rollback limit.
4. After a match RPCS3 may open a window with received messages. Just close it.

After playing (bug reports)
---------------------------
If something goes wrong (desync, freeze, crash), send these files to each other:
  - the rollback_log folder (boj_*.csv files),
  - the file log\RPCS3.log.

Known limitations
-----------------
- Rollback only runs during the fight itself. Character select and menus run as in the original
  game.
- During a re-simulation new sounds are not started again (so a hit is not heard twice).
- Sound: the stage music is muted during the fight itself (rollbacks distorted it); intros,
  KO scenes and menus keep it. Hit sounds are not rolled back: a hit that only the corrected
  timeline has may stay silent. Sound may still be slightly imperfect. Being worked on.
- The PS3 firmware and the game are not included. You need your own copy.
```

---

## Česky

Upravené RPCS3 s rollback netcodem (princip GGPO) pro online režim Tekken 6 (PS3, BLUS30359 v1.03) přes RPCN.

Stažení: viz **Releases** (tekken6_rollback.zip). Balíček neobsahuje firmware PS3 ani hru.

```
TEKKEN 6 (PS3, RPCS3) - ONLINE S ROLLBACKEM
==========================================

Co to je
--------
Upravené RPCS3, které v online zápasu Tekken 6 (Player Match přes RPCN) místo čekání
na soupeře předpovídá jeho vstupy a při chybné předpovědi hru vrátí (rollback, max. 5 snímků)
a přepočítá (stejný princip jako GGPO). Vlastní postava se nevrací, skočit může jen soupeř.
Zpoždění vstupu (delay) se nastavuje samo: 1 snímek (~17 ms) do pingu ~100 ms, při horším
spojení přidá snímek, aby hra nemusela čekat.

Oba hráči MUSÍ mít:
  - tuto stejnou verzi RPCS3 (tento balíček),
  - Tekken 6 USA (BLUS30359) s aktualizací 1.03,
  - procesor s AVX2 (Intel Core 4. generace a novější, jakýkoli AMD Ryzen).

Instalace (jen poprvé)
----------------------
1. Rozbal balíček do vlastní složky (ne do Program Files).
2. Spusť rpcs3.exe.
3. File > Install Firmware: nainstaluj firmware PS3 (PS3UPDAT.PUP stáhni z oficiálního webu PlayStation).
4. Přidej hru (File > Add Games) a nainstaluj aktualizaci 1.03 (File > Install Packages/Raps/Edats).
5. Configuration > RPCN: přihlas se svým RPCN účtem (případně si ho tam vytvoř).
6. Nastavení hry NEMĚŇ. Soubor config\custom_configs\config_BLUS30359.yml musí být na obou PC stejný
   (zajišťuje, že obě PC počítají hru bit po bitu stejně).
7. Zavři RPCS3.

Hraní
-----
1. Spusť play_online.bat (RPCS3 se otevře s nastavením rollbacku; samotné rpcs3.exe bez .bat
   rollback NEMÁ). Delay je automatický. Ruční pevný delay jen výjimečně: play_online.bat 2
2. V RPCS3 spusť Tekken 6 a jdi do Online Mode > Player Match.
   Jeden vytvoří místnost (Create Session), druhý se připojí (Custom Match > Search > Join).
3. Hraj normálně. Spojení má být stabilní (kabel lepší než Wi-Fi). Když pakety chvíli
   nechodí, hra počká (jako původní online), nic se nehádá.
4. Po zápase může RPCS3 otevřít okno s přijatými zprávami - zavři ho.

Po hraní
--------
Pošlete si navzájem (pro kontrolu, že hra zůstala synchronní):
  - složku rollback_log (soubor boj_*.csv),
  - soubor log\RPCS3.log.

Známá omezení
-------------
- Rollback je jen v boji (výběr postav a menu běží jako v původní hře).
- Při přepočtu se nové zvuky nespouští znovu (aby úder nezazněl dvakrát).
- Pokud by se hra rozešla nebo spadla, pošlete logy výše.
```

## Licence
RPCS3 je licencováno pod GPL-2.0 (https://github.com/RPCS3/rpcs3). Tento balíček je upravený build RPCS3; zdrojový kód úprav je dostupný na vyžádání u autora repozitáře.
