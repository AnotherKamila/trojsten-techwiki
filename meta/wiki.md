Ako sa používa táto dokumentácia
================================

Okrem nejakých drobností je tu (t.j. na serveroch v `/root/doc`) pohodená hromada markdownových súborov. Idea je, že keď, milý root, niečo robíš, 1. máš po ruke dokumentáciu a 2. rovno to aj píšeš, aby ďalšie generácie vedeli, komu nadávať. Viac info v [Ako byť dobrým rootom](meta/dobry_root.md) (to si *máš prečítať*).

Ten markdown sa dá aj čítať. Ale svet je trocha krajší, keď je farebný a s hyperlinkami. Takže je tu pohodený čarovný `index.html`, takže sa dá táto hromádka súborov zobrať a z hocikadiaľ servovať a byť ohyperlinkovaná a farebná.

Momentálne to visí na https://techwiki.trojsten.sk a mirror (keby niečo) je na https://techwiki.trojsten.7f000001.org; obe pýtajú meno a heslo, správna odpoveď je tvoj seminár a jeho miestnosť (čiže `FKS`:`TODO` alebo `KMS`:`TODO` alebo `KSP`:`T2`).

Note: Samozrejme, že to tam ešte nevisí. TODO.

Ako písať
---------

Celé toto tu je pod git-om, aby sme mohli používať git blame, keď to celé pokazíš. Push do master branchu updatne aj [techwiki.trojsten.sk](https://techwiki.trojsten.sk).

TODO kde pod git-om? :D

Čo kam kedy písať
-----------------

Keď sa chytáš serveru, vždy to chceš zapísať do jeho changelogu ($server.md#Changelog). V závislosti od toho, čo si spravil, to zvyčajne treba zapísať aj voľakde inde.

Kde čo patrí:

- **ako sa niečo robí** (napr. ako opraviť túto vec, alebo ako pridať používateľa): `playbooks/mojnavod.md` (existuje template: `playbooks/template.md`)
- **dokumentácia k službám**: `services/mojasluzba.md` (existuje template: `services/template.md`), plus ak je verejná a teda je otvorený port v [ujovom firewalle](masiny.md#Mašiny,_IPčky_a_do_von_otvorené_porty), treba hentam dopísať.

Note: Templaty v skutočnosti ešte neexistujú. TODO.

Ako funguje čarovný index.html
------------------------------

Proste píš markdown, linkovanie na iné súbory sa robí Úplne Normálne, čiže relatívny link, čiže [aha](../index.md). Navigácia je v `navigation.md`.

Viac info o použití čarovnej wiki: https://dynalon.github.io/mdwiki/#!quickstart.md  
Viac info o čarovnej wiki všeobecne: https://dynalon.github.io/mdwiki/

Prečo práve toto sa dočítaš [tu](preco/wiki.md).

Note: pozor na mixed content: ak sa servuje cez https a niečo je http, Chrome to blockne a JS sa z toho zblázni a Celé To Nefunguje.

Lokálne prezeranie
------------------

Chrome a Safari robia paranoidné blbosti, takže v nich nefunguje "otvor index.html" -- treba lokálny webserver. Ako nejaký ľahko zohnať: pusti `python3 -m http.server` alebo `python2 -m SimpleHTTPServer` a už máš, na http://localhost:8000 :-)

`index.html` ťahá nejaké veci z internetu, ale `offline.html` má všetko bundled, keby nešli internety. Takže ak nemáš internety, použi ten.
