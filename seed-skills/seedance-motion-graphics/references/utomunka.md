# Utómunka — hogy ne AI-videónak látsszon

A legenerált klip **nyersanyag**. Öt réteget rakunk rá, ami együtt kb. 5 perc munka, és ez választja el a
felismerhetően AI-generált anyagot a profi motion graphicstől. A trükk közös lényege: az AI-videó *túl tiszta* —
tökéletesen sima a mozgás, tökéletesen éles a teljes kép, tökéletesen egyenletes a színe. Egy valódi kamerán
és egy valódi animátor kezén átment anyagon ezek egyike sem igaz.

## Melyik stílushoz melyik réteg

| Réteg | Feliratos anim. | Márka/termék (prémium) | Kollázs-magyarázó |
|---|:--:|:--:|:--:|
| 1. Képkocka-ritkítás (stop-motion érzet) | opcionális | **nem** | **igen** |
| 2. Duotone-textúra | opcionális | **nem** | **igen** |
| 3. Színhiba a széleken (aberráció) | igen | **igen** | igen |
| 4. Sarok-torzítás / szélső elmosás | igen | **igen** | igen |
| 5. Vignetta + szemcse | igen | **igen** | igen |

A prémium termékvideó a kivétel: ott a tisztaság a lényeg, a duotone és a stop-motion tönkreteszi.
A kollázs-magyarázónál viszont épp az 1–2. réteg adja a Vox-os kézműves hatást.

---

## After Effects (a teljes Adobe-készlethez)

Importáld a klipet, `Ctrl+/` a kompozícióba. **Minden réteg külön Adjustment Layer** (`Layer > New >
Adjustment Layer`), a klip fölé, a teljes időtartamra kinyújtva. Az alábbi **sorrend számít** — alulról
felfelé: szín → torzítás → elmosás → szemcse → képkocka-ritkítás.

### 1. Képkocka-ritkítás — stop-motion érzet
`Effect > Time > Posterize Time`, `Frame Rate: 12` (durvább hatáshoz 8, finomabbhoz 15).
Fölé, ugyanarra a rétegre: `Effect > Time > Pixel Motion Blur`, `Shutter Angle: 360`, `Samples: 15`.
A kettő együtt adja a "lassú zár" hatást: ritkított képkockák, de elkenődött mozgás.
**Ezt a réteget tedd legfelülre**, hogy az összes többi effekt is ritkuljon vele.

### 2. Duotone-textúra
Adjustment layer, `Effect > Color Correction > Tint`. Állítsd a `Map Black To`-t a paletta sötét
színére, a `Map White To`-t a világosra, majd az `Amount to Tint`-et **20–30%**-ra — ne 100%-ra,
mert akkor elveszik az eredeti szín.

### 3. Színhiba a széleken (kromatikus aberráció)
Ez natívan három rétegből áll:

1. Duplikáld a klipet háromszor (`Ctrl+D`).
2. Mindháromra: `Effect > Channel > Shift Channels` — az elsőn csak a piros, a másodikon csak a
   zöld, a harmadikon csak a kék csatorna maradjon (a többit `Full Off`-ra).
3. A felső kettő rétegmódja `Add` (Hozzáadás).
4. `Scale` a három rétegen: `100.0` / `100.3` / `100.6` — ez a pár tizedes az egész hatás.
5. Fogd össze a hármat egy Pre-composba, és rakj rá egy **ellipszis maszkot középre**,
   `Inverted` bepipálva, `Mask Feather: 200`.

A maszk fordítása a kulcs: **középen tű-éles marad a kép, csak a széleken csúszik szét a szín.**
Ettől lesz fókuszpontja a képnek. (Ha van színkorrekciós plugin-készleted — Red Giant, Boris —
ott ez egy csúszka, használd inkább azt.)

### 4. Sarok-torzítás
Adjustment layer, `Effect > Distort > Optics Compensation`, `Field of View: 8–12`,
`Reverse Lens Distortion` **kikapcsolva**. Ez enyhén kifelé hajlítja a sarkokat, mintha széles
látószögű objektíven át néznénk. Alatta ugyanezen a rétegen `Effect > Blur & Sharpen > Fast Box Blur`,
`Blur: 8`, és egy **fordított, erősen lágyított ellipszis maszk** (`Feather: 300`), hogy csak a
legkülső sáv legyen elmosva.

### 5. Vignetta + szemcse
Adjustment layer:
- `Effect > Color Correction > Curves` — az RGB görbe jobb felső végét húzd le pár százalékkal,
  ettől lesz mélysége a képnek.
- Rajzolj rá **két lágyított, átlós maszkot** a bal alsó és a jobb felső sarokba (`Mask Feather: 250`),
  hogy a sötétítés csak ott érvényesüljön — így a néző szeme középre húz.
- Végül `Effect > Noise & Grain > Add Grain`, `Intensity: 0.3`, `Size: 1.0`. Nagyon halkan.
  Ha erősebbnek látszik, mint egy filmszemcse, akkor túl sok.

### Kimenet
`Composition > Add to Adobe Media Encoder Queue` → **H.264, 1080p, VBR 2-pass, Target 16 Mbps**.
Közösségi médiára ez bőven elég, és nem tömöríti szét a szemcsét.

---

## CapCut (ha nincs kéznél az Adobe)

Ugyanaz az öt réteg, a beépített effektekkel. Mindegyiket húzd a klip fölé, és nyújtsd ki a teljes hosszra.

| # | Effekt neve | Beállítás |
|---|---|---|
| 1 | `FPS lag` | erősség **40** körül |
| 2 | `Dual tone` | speed **2** |
| 3 | `Chrome blur` | blur **le a minimumra**, lateral chromatic aberration **52**; utána `Mask > Circle`, nagyra húzva, **Reverse** bekapcsolva, `Feather: 24` |
| 4 | `Radial blur 2` | size **27–29**, filters **ki**, glow **ki** |
| 5 | Adjustment réteg | `Color wheel > Offset` enyhén le; két `Split mask` átlósan a sarkokba, lágyítva. Majd a klipen `Adjust > Particles: 10` |

A `Chrome blur` alapból csúnya — a blur lehúzása és a fordított maszk teszi használhatóvá. Ha rögtön
ránézésre rossz, valószínűleg a `Reverse` maradt ki.

---

## Amit az utómunka nem old meg

- **Szétesett feliratot nem lehet megjavítani a vágóban.** Az vissza a promptra —
  lásd `hibaelharitas.md`.
- **A ritmust és a vágást** a generálás nem adja meg. Ha több klipet raksz össze, a vágópontokat a
  zene ütemére tedd, ne az AI által adott jelenethatárokra.
- **Hang nincs.** Zene és hangeffektek nélkül a legjobb motion graphics is félkész.
