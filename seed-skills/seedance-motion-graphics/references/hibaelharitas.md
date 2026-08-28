# Hibaelhárítás — mit írj át a promptban

A javítás menete mindig ugyanaz: **nézd meg a visszaküldött videót**, állapítsd meg, melyik
másodpercnél és milyen jellegű a hiba, javítsd a promptot az alábbiak szerint, majd add ki a
**teljes javított promptot** újra.

| Tünet | Ok | Javítás a promptban |
|---|---|---|
| A felirat az első pár másodpercben tökéletes, aztán összekuszálódik | túl hosszú a szöveg, vagy túl sokáig kell egyben tartania | rövidítsd 2–5 szóra; bontsd két, egymás után megjelenő sorra; erősítsd meg a szövegvédelmi blokkot azzal, hogy `including the final second` |
| Kitalált szavak, értelmetlen karakterek jelennek meg | a modell "kitölti" a látványt szöveggel | tedd a `TEXT INVENTORY` blokk végére: `No other text, no watermarks, no captions, no UI labels appear anywhere.` |
| Egyszerre két-három felirat is látszik és mindegyik romlik | túl sok egyidejű szöveg | jelenetenként **egy** szövegblokk; a többit told át külön jelenetbe |
| Kapkodó, összepréselt animáció | a prompt hossza és a generátorban beállított hossz nem egyezik | állítsd egyezőre; ha kevés az idő, vegyél ki jeleneteket, ne gyorsítsd őket |
| A mozgás gépies, egyenletes | hiányzik vagy gyenge a `MOTION PRINCIPLES` blokk | vedd be az `ease-in-ease-out`, `subtle overshoot`, `settles completely still` hármast |
| A logó / termék nem hasonlít | nincs csatolva referenciakép, vagy nincs kimondva a kötés | csatold a képet, és írd be: `must match the attached reference image exactly in shape, colour and proportion` |
| A generálás lemásolta a referenciavideó színét és tartalmát is | nincs szétválasztva a látvány és a mozgás | vedd be: `The attached video is a reference for CAMERA MOVEMENT AND MOTION DYNAMICS ONLY. Do not copy its colours, typography, subject matter or branding.` |
| Idegen márkajelzés maradt a képen | a referencia márkás anyag volt | `No logos, brand marks or packaging text other than what is listed in the text inventory.` |
| A jelenetek nem folynak egymásba, ugrál | hiányoznak az `Exit:` sorok | minden jelenethez írj `Exit:` sort — mi viszi át a következőbe |
| Zsúfolt, olvashatatlan kompozíció | minden egyszerre animál | `Only one or two elements animate at a time; the rest hold still.` |

## Amikor nem a prompt a hibás

- **Ugyanaz a prompt kétszer futtatva más eredményt ad.** Ha a szerkezet jó és csak a részletek
  csúsztak, először futtasd újra — olcsóbb, mint átírni.
- **Az utolsó fél másodperc gyakran a leggyengébb.** Ha csak ott romlik, a vágóban vágd le,
  ne generálj újra.
- **Az apró textúra- és élességhibák** az utómunkában eltűnnek a szemcse alatt. Ne generálj újra
  olyasmiért, amit egy grain-réteg elfed.
