---
name: seedance-motion-graphics
description: Motion graphics (feliratos animáció, logó-animáció, termékvideó, magyarázó/kollázs videó) készítése Seedance 2.5 videómodellel - referenciaképből vagy referenciavideóból generálásra kész, shot-by-shot promptot ír, majd utómunka-receptet ad (After Effects vagy CapCut), hogy a kész anyag ne AI-generáltnak, hanem profin animáltnak látsszon. Használd MINDIG, ha a felhasználó motion graphicset, feliratos/szöveges animációt, animált hirdetést, logó-intrót, termékbemutató videót, magyarázó (Vox-stílusú) vagy kollázs-animációt akar; ha Seedance-t, Higgsfieldet, videógenerálást, "AI videó promptot" említ; ha Pinterest-referenciát vagy egy tetszik-nekem-videót küld be azzal, hogy "ilyet szeretnék"; vagy ha egy már legenerált videóban elrontott/szétesett szöveget kell javíttatni. Trigger szavak: motion graphic, Seedance, Higgsfield, videó prompt, animált felirat, szöveges animáció, logó animáció, explainer, kollázs animáció, "csinálj ebből videót", "írj rá promptot", "szétesett a szöveg a videóban".
---

# Seedance 2.5 motion graphics

Referencia (kép vagy videó) + rövid brief → **generálásra kész prompt** → generálás → **utómunka-recept**.

A Seedance 2.5 három dologban tud újat az elődeihez képest, és a teljes eljárás erre a háromra épül:
könnyen olvasható **ép szöveget** rajzol a képbe, **egy generálásban 30 másodpercig / több jelenetig** elmegy,
és **hosszú, strukturált promptot** is helyesen értelmez. Ha a prompt rövid vagy pongyola, mindhárom előny elveszik.

## Munkamenet

### 1. Referencia bekérése (kötelező)

Ne generálj promptot vizuális referencia nélkül. Kérd be ezek valamelyikét:

| Referencia | Mit határoz meg | Hogyan dolgozd fel |
|---|---|---|
| **Kép** (pl. Pinterestről) | szín, tipográfia, felület, hangulat | nézd meg, és nevezd meg konkrétan: hex-közeli színek, betűtípus-karakter, kontraszt, textúra |
| **Videó** | kameramozgás, ritmus, átúszások, animációs elv | **kérd meg magad a képkockánkénti elemzésre** — videónál mindig mondd ki, hogy „elemezd képkockáról képkockára", különben csak a töredékét nézed át és elveszik a mozgás logikája |
| **Kép + videó együtt** | a kép a látvány, a videó CSAK a mozgás | ez a legerősebb kombináció, lásd lent |

**A legfontosabb trükk — a látvány és a mozgás szétválasztása.** Ha a felhasználó egy tetszetős videót
küld be, ne azt írd le, amit lát. Vedd el belőle **csak a kameramozgást és a ritmust**, a színt/tipográfiát/
tartalmat pedig a felhasználó saját anyagából (logó, brand-szín, termékfotó) vedd. A promptban ezt így kell
kimondani: *„a csatolt videó kizárólag a kameramozgás és a mozgásdinamika referenciája, nem a színé és nem a
stílusé"*. Így nem másolatot kapsz, hanem a saját arculatod profi mozgással.

### 2. Legfeljebb 3 kérdés, aztán dolgozz

Ha hiányzik, kérdezd meg — de egyszerre, felsorolásban, és ne többet háromnál:

1. **Mi a videó hossza?** (5 / 10 / 15 / 20 / 28 másodperc — a Seedance 2.5 max ~30 s)
2. **Milyen szöveg jelenjen meg benne, szó szerint?** (rövid, 2–6 szavas sorok)
3. **Mi a cél/termék?** (mit hirdet, kinek)

Ami nincs megadva, azt döntsd el magad és írd oda a prompt alá egy sorban, mit feltételeztél.
Ne interjúztasd a felhasználót — a bizonytalanságot inkább kreatív döntéssel oldd fel.

### 3. Prompt megírása

A prompt szerkezetét, a kötelező szövegvédelmi sorokat és a három kész sablont (feliratos animáció /
több jelenetes márkavideó / kollázs-magyarázó) lásd: **`references/prompt-sablon.md`**.

Négy szabály, ami minden promptra vonatkozik:

- **Angolul írd a promptot**, akkor is, ha a beszélgetés magyarul megy. A modell angolul érti a
  legpontosabban a szakkifejezéseket. A videóban *megjelenő* szöveg természetesen lehet magyar —
  azt idézőjelben, szó szerint kell megadni.
- **Minden felirat szó szerint, idézőjelben, jelenetenként.** Ne írd, hogy „megjelenik a szlogen" —
  írd le pontosan: `the text "MOTION GRAPHICS MADE EASY" types in, letter by letter`.
- **Kell egy szövegvédelmi blokk** a prompt végére (kész szöveg a referenciafájlban). Ez a leggyakoribb
  hibaforrás: hosszabb generálásoknál a felirat a videó közepétől összekuszálódik.
- **A hossz a promptban és a generátorban ugyanaz legyen.** Ha 20 másodperces jelenetsort írtál,
  a felületen is 20 s-ot kell beállítani, különben a modell összepréseli vagy szétnyújtja az egészet.

### 4. Átadás generálásra

A promptot **egyetlen, összefüggő kódblokkban** add ki, hogy egy kattintással másolható legyen.
Alatta 3 sorban a beállítások, amiket a generátor felületén be kell állítani:

```
Modell: Seedance 2.5   |   Hossz: <ugyanaz, amit a prompt mond>   |   Felbontás: 1080p   |   Képarány: 16:9
Referencia: <csatold be ugyanazt a képet, amit én is láttam>  (kollázs/arculatos anyagnál kötelező)
```

A Seedance 2.5 több felületen is elérhető; a felhasználó által megszokott generátort használja
(pl. Higgsfield vagy más szolgáltató) — a skill a promptot adja, nem a felületet.

### 5. Javítókör — ha elromlott a generálás

Ez a munkamenet szerves része, nem kudarc. Ha a felhasználó visszaküldi a sikerületlen videót:

1. **Nézd meg a visszaküldött videót**, és mondd meg konkrétan, hányadik másodpercnél romlik el.
2. Azonosítsd a hibatípust és javítsd a promptot a **`references/hibaelharitas.md`** táblázata szerint.
3. Add ki a **teljes javított promptot** újra, ne csak a különbséget — a felhasználó másolni fogja.

A leggyakoribb: a szöveg az első pár másodpercben tökéletes, aztán szétesik. Ilyenkor rövidíteni kell a
feliratot, csökkenteni az egyidejűleg látszó szövegek számát, és megerősíteni a szövegvédelmi blokkot.

### 6. Utómunka-recept

**Mindig add oda**, ne csak kérésre. Ez választja el a felismerhetően AI-generált videót a profi anyagtól,
és 5 perc munka. A pontos effektek, paraméterek és a két szoftver (After Effects és CapCut) lépésről lépésre:
**`references/utomunka.md`**.

Ne borítsd rá mindet minden videóra — a referenciafájl megmondja, melyik stílushoz melyik réteg való
(a duotone-textúra például kifejezetten ront egy letisztult, prémium termékvideón).

## Buktatók

- **Referencia nélkül generált prompt szinte mindig kidobott kredit.** Inkább kérd be a képet.
- **Videó-referenciánál a képkockánkénti elemzés kimondása nélkül** a mozgás lényege elvész.
- **A hosszú felirat a legdrágább hiba.** Több rövid sor egymás után jobban működik, mint egy hosszú mondat.
- **A prompt és a generátor hossza eltér** → összepréselt, kapkodó animáció. Mindig ellenőrizd.
- **Túl sok effekt az utómunkában** ugyanúgy elrontja, mint a semennyi. Stílusonként válogass.
- **Ne az AI-videóra tegyél mindent**: a kész generálás nyersanyag. A tempó, a vágás és a hang továbbra is
  a vágóprogramban dől el.
