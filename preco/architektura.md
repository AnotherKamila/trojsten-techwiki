Akú architektúru chcem a prečo
==============================

TODO väčšina tohto tu in fact patrí do meta/gut.md

Trojstenový účet
----------------

Žiadne per-seminár oné -- existuje jedna celotrojstenová identita tvaru prezyvka@trojsten.sk (konflikty sa vyriešia na úrovni managementu, nie IT), spokojne si sediaca v spoločnom LDAPe. Emaily typu jano@ksp.sk a jano@fks.sk (čo sú rôzni ľudia) alebo kamila@ksp.sk a kamila@fks.sk (čo som tá istá ja) budú proste ručne napísané v LDAPe, lebo aj tak to nejde odlíšiť. Google Apps účty sa budú synchronizovať s LDAPom.

Prečo: pre jednoduchosť a jasnosť, ako pri používaní, tak aj pri administratíve.

Servery
-------

V mojej vízii má Celý Trojsten dokopy dva servre:

- 1 mašina s "vysokým SLA" (ako archiv) -- mala by ísť stále, preto tam budú práve tie podstatné veci; jedného pekného dňa prípadne replikovaná niekde ďaleko
  - weby (potenciálna diera, ale má ísť stále)
  - DNS
  - LDAP
  - hostname: inteligent

- 1 mašina s nižším SLA (ako element) -- na interné veci
  - homes
  - shell pre userov
  - maily (alebo hore? Mali by ísť, takže možno radšej hore, ale tu majú useri shell a tu nevadí, keď narobia bordel.)
  - repozitáre (Alebo to hore? Ale tu majú shell.)
  - user weby (~username)
  - jabber (ale ak dáme hore maily, tak aj jabber)

Backupy budú inde.

Extra KSP mašín typu testovač sa toto netýka, tie by ostali ako sú.
