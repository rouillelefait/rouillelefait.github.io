---
title : O nama
---
Nakon nekoliko decenija razvoja i dizajna softvera u mnogim programskim jezicima (ASM, Pascal, C/C++, Python, Go, ...), **otkrio sam Rust i njegov ekosistem 2024. godine**.

Brzo sam zaronio u ovaj jezik koji mi je fascinantan, ali zašto?

# Komplikovan jezik?

Da, **Rust ima prilično strmu krivu učenja** i zahteva trud jer koristi paradigme koje se razlikuju od uobičajenih jezika. Međutim, kada se pripitomi, čak i sa osnovnim nivoom veština, jezik je jednako efikasan, a funkcionalnosti koje nisu u potpunosti savladane mogu se zaobići kodom koji je možda manje performantan, ali funkcionalan. I kako napredujete, način pisanja koda se menja i postaje sve više "rusty" i efikasan.

# Zahtevan jezik?

Da, Rust je zahtevan po pitanju preciznog razumevanja onoga što radite. **Nemoguće je ostaviti za kasnije problem** sa memorijom ili deljenjem podataka između niti. Kompajler to neće propustiti, i upravo je to najveća snaga Rust-a.

Pored svih aspekata bezbednosti koji se često ističu, ova snaga Rust-a ima značajan uticaj na sve projekte.
Teško je, čak i nemoguće, napraviti špageti kod — ne zato što jezik to ne bi dozvolio ako to zaista želite, već zato što razumevanje svih aspekata koda prirodno vodi ka sve čistijem dizajnu kako projekat raste.

# Opuštajući jezik?

Da, na kraju krajeva, Rust je opuštajući. Možete se u velikoj meri osloniti na kompajler da obezbedi sve aspekte za koje je a priori analiza često složena za naš mozak.

Tipično, prekoračenja bafera, uslovi trke, deadlock-ovi i drugi bagovi koji se reprodukuju jednom u sto puta pod veoma specifičnim uslovima lakše se izbegavaju u Rust-u.
Čak i ako alati poput [Valgrind](https://valgrind.org/)-a mogu pomoći kod standardnih jezika kao što su C/C++, **Rust omogućava da se ovi problemi izbegnu ili barem značajno ograniče već u fazi kompajliranja**.

Tokom pregleda koda nema potrebe tražiti ovaj tip greške jer znamo da **Rust to neće propustiti**. Tada se možemo fokusirati na algoritme i arhitekturu jer je kompajler obavio "niskonivovski" posao.

# Cenjen jezik?

Da, Rust je [najcenjeniji jezik](https://survey.stackoverflow.co/2024/technology#2-programming-scripting-and-markup-languages) ... među programerima koji istraju u njegovom učenju.

# Kompletan ekosistem?

Da, **Rust-ov ekosistem je kompletan** sa, između ostalog, Cargo-om za upravljanje paketima, nativno podržanim jediničnim i integracionim testovima, generisanjem dokumentacije i alatima za reviziju.

I sa velikom i entuzijastičnom zajednicom koja razvija brojne [crate-ove](https://crates.io/), Rust omogućava da se sve uradi sa velikom efikasnošću, performansama i bezbednošću. Doduše, još uvek ima dosta posla da se dostigne nivo drugih zrelijih ekosistema, ali to je samo pitanje vremena.

Nadam se da će vas ovaj sajt ubediti i pomoći vam da otkrijete, cenite i koristite Rust u svim vašim projektima.


> **Korišćenje veštačke inteligencije**: Neki delovi ovog veb sajta (tekst i izvorni kod) i konkretnije svi prevodi na engleski i srpski, izrađeni su uz pomoć veštačke inteligencije, ponekad sa ljudskom revizijom, ali bez garancije 100% kvaliteta prevoda.
> Neki primeri izvornog koda na [github](https://github.com/rouillelefait/) repozitorijumu su takođe generisani uz pomoć veštačke inteligencije, ponekad veoma delimično da bi se ubrzali određeni aspekti, ponekad u većoj meri ili čak u potpunosti u pristupu vođenom veštačkom inteligencijom (Spec Driven Development na primer). Svaki put je ova informacija navedena u odgovarajućem repozitorijumu.
