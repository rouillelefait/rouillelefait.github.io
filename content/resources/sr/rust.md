---
name: rust.md
title: Osnovni resursi
summary: za učenje osnova jezika i njegovih specifičnosti
icon: cuddlyferris.svg
index: 1
date: 2025-10-12
---

# Uvod

Kriva učenja Rust-a je dugačka i osnovni koncepti su teški za razumevanje. Za razliku od većine jezika, kompajliranje prvog programa, čak i za jednostavan primer, je komplikovano i brzo se suočavate sa porukama o greškama kompajlera koje su na početku često nerazumljive.

Dva pristupa su vam na raspolaganju:
1. Odvojite vreme da pročitate dokumentaciju kako biste dobili pregled jezika i njegovih koncepata pre nego što zaronite u kod
2. Skočite direktno u kod i napredujte kako se pojavljuju poteškoće:
    - radeći "obrnuti inženjering" na osnovu grešaka koje prijavljuje kompajler
    - tražeći informacije kako se problemi pojavljuju: zvanični sajt, video zapisi, delovi knjige, pitanje AI-ju, ...

Lično (i samim tim subjektivno), mislim da je Rust jezik koji apsolutno zahteva da počnete sa tačkom 1, kako ne biste odustali odmah slomivši zube na kodu koji će brzo proizvesti obeshrabrujuće greške. Paradigme Rust-a (borrow checker, lifetime, ...) su toliko različite od drugih jezika da je potreban minimum čitanja da bi se razumele pre početka.

Zatim, kada se osnovni koncepti usvoje (čak i delimično), možete bolje razumeti greške kompajlera i prelazak na korak 2 postaje najbolji način za napredovanje. Idite napred-nazad između pisanja koda i dubljeg čitanja da biste postepeno savladali koncepte.


# Zvanična dokumentacija

Zvanični sajt [Rust](https://www.rust-lang.org/)-a je nezaobilazan izvor informacija.

Naći ćete opštu dokumentaciju o jeziku:
- kako [instalirati Rust](https://www.rust-lang.org/tools/install)
- referentnu [knjigu](https://doc.rust-lang.org/book/)
Ova knjiga je takođe dostupna za [kupovinu](https://nostarch.com/rust-programming-language-2nd-edition) u PDF ili papirnom formatu
Specifičnija dokumentacija o:
- [standardnoj biblioteci](https://doc.rust-lang.org/std/index.html)
- [cargo](https://doc.rust-lang.org/cargo)
- [rustdoc](https://doc.rust-lang.org/rustdoc/index.html)
- stranica sa informacijama o [alatima](https://www.rust-lang.org/tools)

# Alati za učenje

- [rustlings](https://github.com/rust-lang/rustlings): vežbe koje prate zvaničnu knjigu
- [Rust by Example](https://doc.rust-lang.org/rust-by-example/): učenje osnovnih koncepata kroz kod
- [playground](https://play.rust-lang.org/): za brzo testiranje delova koda

Zvanični sajt ostaje referentni izvor informacija ali nije izvor koji sistematski smatram najpedagoškijim.

# Knjige

## "Programming Rust, Fast, Safe Systems Development"

Dostupna u [2. izdanju](https://www.oreilly.com/library/view/programming-rust-2nd/9781492052586/), [3. izdanje](https://www.oreilly.com/library/view/programming-rust-3rd/9781098176228/) je očigledno planirano za jun 2026.

Ova knjiga je veoma dobro organizovana, omogućava progresivno čitanje sa velikom pedagogijom.

Ako imate hrabrosti, toplo preporučujem skoro kompletno prvo čitanje (osim async programiranja i dalje) pre nego što zaronite u kod. Nije strašno ako se sve ne usvoji iz prvog puta, ali to daje jasnu i strukturiranu viziju osnovnih koncepata.

Zatim, korak po korak, ova knjiga ostaje referenca za pregled koncepata sa veoma dobro strukturiranim sadržajem.

## "Rust for Rustaceans" *(napredni nivo)*

Dostupna [ovde](https://nostarch.com/rust-rustaceans) sa [posvećenom veb stranicom](https://rust-for-rustaceans.com/)

Ova knjiga predstavlja veoma napredne pojmove programiranja u Rust-u iz perspektive veoma iskusnog programera.

Treba je čitati tek u drugom koraku jer izloženi koncepti zahtevaju solidno poznavanje jezika. Ovo nije knjiga za početnike, već odličan resurs kada su osnove dobro savladane.

Autor [Jon Gjengset](https://thesquareplanet.com/) je Rust entuzijasta koji nudi mnoge resurse (pogledajte odeljak Video zapisi u nastavku).

# Video zapisi

- [Jon Gjengset](https://www.youtube.com/c/JonGjengset): detaljni video zapisi o naprednim temama, kao i veoma zanimljiv [intervju](https://www.youtube.com/watch?v=nOSxuaDgl3s) o njegovoj viziji Rust-a i AI-ja, koju delim
- [Let's Get Rusty](https://www.youtube.com/@letsgetrusty): idealno za početnike, prati zvaničnu knjigu poglavlje po poglavlje

# Zajednica

- [Zvanični forum](https://users.rust-lang.org/): za postavljanje pitanja i razmenu sa zajednicom
- [r/rust](https://www.reddit.com/r/rust/): Rust subreddit, veoma aktivan
- [Rust Discord](https://discord.gg/rust-lang): za pomoć u realnom vremenu
