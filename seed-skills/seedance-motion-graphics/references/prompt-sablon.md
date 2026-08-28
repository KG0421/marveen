# Seedance 2.5 prompt-szerkezet és sablonok

A prompt **angolul** készül, egyetlen összefüggő szövegblokkban, ebben a sorrendben.

---

## A hat blokk

### 1. FEJLÉC — mit csinálunk, mennyi ideig

```
A [DURATION]-second multi-shot motion graphics animation, 16:9, 1080p.
```

Egy mondat. A hossz itt is szerepeljen, nemcsak a generátor beállításában.

### 2. STYLE & LOOK — a látvány

A referenciaképből olvasd ki és nevezd meg **konkrétan**. Ne „modern és letisztult", hanem mérhető jellemzők:

- háttér (szín, anyag, gradiens, textúra)
- 2–4 kiemelt szín, lehetőleg megnevezve (soft lavender, warm cream, muted sage)
- tipográfia karaktere (geometric sans-serif, medium weight, generous letter-spacing)
- felület és mélység (soft drop shadows, subtle glass blur, flat with no shadow)
- fényviszony (even diffuse light, no harsh highlights)

Ha a felhasználó adott arculati színt vagy logót, az **felülírja** a referenciaképet — a kép ilyenkor
csak a hangulatért felel.

### 3. TEXT INVENTORY — a feliratok szó szerint

Külön blokk, mielőtt a jelenetekhez érnél. Minden megjelenő szöveg felsorolva, idézőjelben, pontos
helyesírással és kis/nagybetűzéssel:

```
TEXT THAT APPEARS IN THIS VIDEO (exact spelling, nothing else):
1. "MOTION GRAPHICS MADE EASY"
2. "in minutes, not days"
3. "Jasper"
```

Miért külön blokk: a modell így egyben látja a teljes szövegkészletet, és nem talál ki hozzá továbbiakat.
Írd oda a végére: `No other text, no watermarks, no captions, no UI labels appear anywhere.`

### 4. SHOT LIST — jelenetről jelenetre, időbélyeggel

Minden jelenet külön blokk. 2–4 másodperc jelenetenként az alapértelmezés.

```
SHOT 1 (0.0-2.5s)
- On screen: [mi látszik, mekkora kitakarásban]
- Text: [pontosan mi és hogyan jelenik meg — types in, fades up, slides in from below]
- Camera: [slow push-in / static / lateral drift, mennyire]
- Motion: [mi mozog és milyen lendülettel — eases in, settles, overshoots slightly]
- Exit: [hogyan megy át a következőbe — cut on motion / whip pan / element carries through]
```

Az `Exit` sort ne hagyd ki: az átmenet maga is jelenet, ettől lesz folyamatos a videó.

### 5. MOTION PRINCIPLES — hogyan mozogjon

Ez adja a „profi animátor" érzetet. Alap-készlet, amit szinte minden motion graphics promptba beírhatsz:

```
MOTION PRINCIPLES:
- All motion uses smooth ease-in-ease-out, never linear or robotic.
- Elements settle with a subtle overshoot, then rest completely still.
- Camera moves are slow, continuous and deliberate; no handheld shake.
- Only one or two elements animate at a time; the rest hold still.
- Every shot resolves into a clean, readable, static frame before it cuts.
```

Videó-referenciánál ide kerül a szétválasztás is:

```
The attached video is a reference for CAMERA MOVEMENT AND MOTION DYNAMICS ONLY.
Do not copy its colours, typography, subject matter or branding.
```

### 6. TEXT INTEGRITY LOCK — a szövegvédelmi blokk

**Ezt mindig másold be, változtatás nélkül.** Ez a leggyakoribb hibaforrás elleni védelem:

```
TEXT INTEGRITY (critical):
- Every word listed above must render as clean, sharp, correctly spelled text for its entire duration.
- Letters must never morph, scramble, flicker, duplicate or dissolve into abstract shapes.
- Text stays perfectly still and fully legible once it has finished animating in.
- No invented words, no gibberish characters, no distorted glyphs at any point, including the final second.
```

---

## Sablon A — egyszerű feliratos animáció (5–10 s)

Egy gondolat, egy erős felirat, 3–5 jelenet. Erre való: közösségi médiás beharangozó, idézet-kártya,
funkcióbejelentés, intró.

```
A 10-second multi-shot motion graphics animation, 16:9, 1080p.

STYLE & LOOK:
Soft off-white background with a barely visible paper grain. Pastel accent colours: muted
lavender, dusty peach, pale sage. Typography is a geometric sans-serif, medium weight, wide
letter-spacing. Elements have very soft, wide drop shadows. Even diffuse lighting, no highlights.

TEXT THAT APPEARS IN THIS VIDEO (exact spelling, nothing else):
1. "MOTION GRAPHICS MADE EASY"
No other text, no watermarks, no captions, no UI labels appear anywhere.

SHOT 1 (0.0-3.5s)
- On screen: a rounded rectangular input bar, centred, filling 60% of frame width.
- Text: the cursor blinks once, then the text "MOTION GRAPHICS MADE EASY" types in
  letter by letter at a natural typing rhythm.
- Camera: extremely slow push-in.
- Motion: the bar is completely still; only the text and cursor animate.
- Exit: cut on the last keystroke.

SHOT 2 (3.5-6.0s)
- On screen: close-up on the circular send button at the right edge of the bar.
- Text: none.
- Camera: static, tight framing.
- Motion: a cursor arrow enters from the lower right, presses the button; the button
  compresses slightly and springs back.
- Exit: the button flash carries into the next shot.

SHOT 3 (6.0-10.0s)
- On screen: the input bar shrinks and flies away from camera into soft depth; pastel
  geometric shapes and small motion-graphic cards bloom outward around it.
- Text: none.
- Camera: slow pull-back.
- Motion: shapes stagger in one after another, each easing to a stop.
- Exit: everything settles into a balanced, still composition and holds for the final half second.

MOTION PRINCIPLES:
[a fenti alap-készlet]

TEXT INTEGRITY (critical):
[a fenti blokk]
```

---

## Sablon B — több jelenetes márka-/termékvideó (20–28 s)

Erre való: ügyfélnek szánt bemutató, termékhirdetés, arculatos anyag. Itt jön szóba a
**kép = látvány / videó = mozgás** szétválasztás, és ide töltöd fel a saját logót vagy terméket.

Szerkezeti eltérések a Sablon A-hoz képest:

- **6–10 jelenet**, hármas tagolásban: felvezetés (0–30%) → a termék működése (30–75%) → lezárás
  logóval és állítással (75–100%).
- A `TEXT INVENTORY` 3–5 rövid sort tartalmaz, nem egyet.
- A záró jelenetben a logó és a szlogen **külön** jelenik meg, időben elcsúsztatva — együtt
  megjelenítve gyakran összemosódnak.
- Videó-referencia esetén a `MOTION PRINCIPLES` blokkba kerül a szétválasztó mondat.

Termékfotó felhasználásakor a képet referenciaként is csatolni kell, és a promptban ki kell mondani:

```
The product shown must match the attached reference image exactly in shape, colour and proportion.
No logos, brand marks or packaging text other than what is listed in the text inventory.
```

Ez a mondat teszi lehetővé, hogy egy tetsző idegen reklám látványvilágát a saját termékedre ültesd át —
az eredeti márkajelzés kikerül, a mozgás és a stílus marad.

---

## Sablon C — kollázs-magyarázó (Vox-stílus, 15–25 s)

Erre való: ismeretterjesztő, oktatóanyag, közösségimédia-magyarázó. Kétlépcsős munkamenet:

**1. lépés — előbb a szöveg.** Írj egy `[DURATION]` másodpercre időzített, felmondható forgatókönyvet
a témáról. Kb. **2,5 szó / másodperc** a reális beszédtempó (20 másodperc ≈ 50 szó).

**2. lépés — a forgatókönyvből a prompt.** A kollázs-stílus jellemzői, amiket a `STYLE & LOOK` blokkba írj:

```
Cut-paper collage aesthetic: layered paper textures with visible torn edges, halftone print
grain, archival photo fragments, hand-cut shapes. Limited palette of aged cream, deep ink blue,
muted brick red. Elements sit on distinct depth layers and slide over one another.
```

A `MOTION PRINCIPLES` blokk kollázsnál kiegészül:

```
- Elements move in flat 2D planes, sliding and rotating, never in 3D perspective.
- Motion is slightly stepped, as in stop-motion, rather than perfectly smooth.
- Paper layers cast small, hard-edged shadows on the layer beneath.
```

A feliratok itt a forgatókönyv **kulcsszavai**, nem a teljes mondatok — jelenetenként 2–4 szó.
