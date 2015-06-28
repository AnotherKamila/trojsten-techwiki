Prečo FreeBSD
=============

Po novom mám neveľa, ale nie úplne nula skúseností s FreeBSD. Vyzerá byť pomerne čarovné. Mohlo by uľahčiť zopár vecí. Takže by som tam pchala FreeBSD. Here's why (Disclaimer: This person's neutrality has been disputed):

- BSD má kultúrnu dokumentáciu (videl niekto niekedy nejaký "Linux handbook" okrem nečitateľného a out-of-date LDP?) a nepokúša sa vás zabiť. Tuším dokonca vyzerá, že ľudia sa najprv zamysleli a porozprávali a až potom to nakódili.
- Developeri poznajú slovné spojenia "Principle of Least Astonishment" a "do one thing well".
- Obvyklé veci typu konfigurovanie postfixu, apacha a podobne sú rovnaké, teda pre základnú administráciu tam nie je nevýhoda tvaru "s BSD nikto nevie robiť".
- Trojstenoví rooti pravdepodobne nebudú ľudia s 10 rokmi skúseností, takže hlboké vnútornosti, ktoré naozaj sú rôzne, sa budú učiť z nuly tak či tak. BSD má kultúrnu dokumentáciu a nepokúša sa vás zabiť. Teda tie veci, čo sa tak či tak budú musieť naučiť, sú v skutočnosti v prospech BSD.
- BSD má pekný natívny mechanizmus na izoláciu: jails. Narozdiel od chrootu to naozaj celkom izoluje (okrem filesystemu aj procesy (vnútri tie zvonka nevidno), userov, niečo málo siete (vlastná IP a hostname), a ťažšie sa dostáva von); narozdiel od virtualizácie to má nulový overhead a takmer nulový administrative overhead; narozdiel od nejakej kinda virtualizácie typu LXC je to jednoduché a vážne lightweight (aj z admin pohľadu, nie len akože to nežerie resources). S jailami je triviálne sharovať spoločný base/"template" a mať rôzne len to, čo naozaj treba, takže vyrobiť jail špeciálne na PHP alebo špeciálne na čokoľvek je jeden príkaz a nula práce navyše (lebo udržiavať stačí ten spoločný base, čiže O(1) roboty od počtu jailov). Dá sa presne nastaviť, aké privilégiá má mať root vo vnútri jailu. Dá sa kombinovať s rctl => nastaviť per jail limity na CPU, pamäť, bandwidth a podobne. Dá sa kombinovať s vnet, čo poskytuje plnú izoláciu/virtualizáciu network stacku. Dá sa kombinovať s milými features ZFS => úplná kontrola nad tým, čo môže jail robiť s filesystemom. Keď máme všetky tri semináre a kopu bordelu na málo mašinách, milý a adminom neneznášaný mechanizmus na izoláciu nemôže byť na škodu.
- BSD má ZFS, čo je hodne cool LVM+filesystem, ktorý som ochotná pustiť na podstatné dáta, lebo o data integrity garantuje rozumné veci a je to stabilné ako prasa a tak. Navyše ZFS má takú milú feature, že sa pred updatom alebo veľkou zmenou spraví (COW) snapshot a keď to nenabootuje, automaticky nabootuje to staré (a keď je to veľmi pokazené, povie sa tomu, aby to nabootovalo to staré). Nemôže byť na škodu.
- Buildy zo sourcu (ports, ktoré sú mimochodom skvelé) a binárne packages vedia veselo spolunažívať, takže môžem použiť to, čo sa momentálne hodí.
- Má to použiteľný firewall! iptables, beat that!

Aby sa nepovedalo, že som zaujatá (aj keď neviem, ako by vás také niečo mohlo napadnúť), tak listnem aj nevýhody:

- Menšia user base => menšia šanca, že nájdeme na nete, ako riešiť tento konkrétny obskúrny problém. Na druhej strane FreeBSD mailing list je úžasný a chutí ako hrozienka a dá sa pýtať tam a nepošlú nás do kelu.
- Používa to menej ľudí v okolí => nespýtame sa kamaráta, či už niekedy robil toto. Nuž, áno, no. Ja síce mám zopár kamarátov, ale pravdepodobne nebudem root večne, takže to je reálna nevýhoda.
- Horšia HW podpora ako Linux. Na serveroch pôjde, na laptopoch (keby root chcel aj doma také) už možno nie.
- Standards-compliant. BSD je POSIX-compatible, Linux má všelikde všelijaké GNU extensions. Takže veci spoliehajúce sa na existenciu GNU extensions nemusia behať a useri budú zmätení, lebo zrazu budú musieť písať `find .`. Chystám sa nainštalovať GNU verzie utilitiek, nasymlinkovať ich bez `g-` prefixu do `/usr/local/gnubin/` a by default ho ľuďom pridať do `PATH`. Problem solved.
