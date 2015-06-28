Update systému
==============

Base system
-----------

Note: `fetch` a `install` sú dva separátne kroky preto, aby sa dalo pozrieť, čo presne sa stane, a ak to nevyzerá dobre, aby sa dalo nepokračovať. Inými slovami, nad výstupom `fetch` sa treba *zamyslieť*.

1. `freebsd-update fetch` -- poťahá updaty základného systému a povie update inštrukcie
   V skutočnosti raz denne robí cron a pošle email s update inštrukciami ak treba updatovať. Čiže ak neprišiel mail, hotovo.
2. `freebsd-update install` -- nainštaluje updaty

Ports tree + porty
------------------

1. `portsnap fetch` -- poťahá diff `/usr/ports`, ale ešte ho neprepíše
   V skutočnosti raz denne robí cron.
2. `portsnap update` -- updatne živý `/usr/ports`
3. `portmaster -abd` -- preinštaluje všetky (`-a`) porty, ktoré majú update, robiac backup (`-b`) momentálnych verzií a mažúc (`-d`) zdrojáky z `/usr/ports/distfiles`.
