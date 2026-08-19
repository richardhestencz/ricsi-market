# Ricsi-market 🛒

A haverok boltja — egyetlen `index.html`, semmi build, semmi függőség.

**Élő oldal:** https://richardhestencz.github.io/ricsi-market/

## Mi ez

155 termék 15 sorban (élelmiszertől a „középső sor" fúrógépéig), kereséssel,
kosárral és valódi rendeléssel. A kosár a böngészőben megmarad, a rendelés
pedig **e-mailben** érkezik meg — szerver nélkül, a [FormSubmit](https://formsubmit.co) segítségével.

## Beállítás

A fájl tetején, a `<script>` elején:

```js
const ORDER_TO = "ruglaktokon@gmail.com";   // ide jön a rendelés
const REVTAG   = "hrichard";                // fizetés: revolut.me/hrichard
const DELIVERY_FEE = 1980;                  // kiszállítás — mindig, ingyen nincs
```

**Fizetés:** csak Revolut. A sikeres rendelés után a vevő egy
„Fizetés Revoluttal" gombot kap (revolut.me link a végösszeggel),
a közleménybe pedig a rendelésszám kerül — így az e-mailben érkező
rendelést könnyű párosítani a beérkező utalással.

**Az első rendelés aktiválja a címet:** miután valaki először megrendel valamit,
a FormSubmit küld egy levelet — a benne lévő linkre kattintva élesedik.
Onnantól minden rendelés automatikusan megérkezik.

Ha nem akarod, hogy az e-mail-címed benne legyen a nyilvános forráskódban:
az aktiváló levélben kapsz egy véletlen azonosítót, cseréld arra az `ORDER_TO`
értékét — a működés ugyanaz marad.

## Termék hozzáadása

A `CATS` tömbben, a megfelelő sorban egy sor az egész:

```js
['Termék neve','1 kg', 1290, '🍎']
//  név          kiszerelés  ár   ikon
```

Az egységárat (Ft/kg, Ft/l, Ft/db) a kiszerelésből magától számolja.
