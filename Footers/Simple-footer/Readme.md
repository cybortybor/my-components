Egy egyszerű footer - HTML-váz

Kezdetnek építsünk egy nagyon egyszerű footert, szerzői jogi információval, és néhány navigációs linkkel:EDIT ON
￼
 

Megjegyzés: Természetesen most is megpróbálkozhatsz azzal, hogy megépíted a komponenst magad, utána pedig megnézed az itt bemutatott megoldást. De ha szeretnél velem haladni, az is rendben van. Nyiss egy új CodePent, és állítsd be a szokásos dolgokat.

CSS reset:
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/meyer-reset/2.0/reset.css">

Border-box váltás:
* {
  box-sizing: border-box;
}

Ha készen állsz, rátérhetünk a HTML-vázra.

A HTML

Minden a footer elemmel kezdődik:

<body>
  <footer>

  </footer>
</body>

Ehhez adom hozzá a .wrapper divet, mert tudom, hogy most is a táblázatos megjelenítést fogom alkalmazni a vertikális középre rendezéshez:

<body>
  <footer>
    <div class="wrapper">

    </div>
  </footer>
</body>

A szerzői jogi információt egy small elembe teszem, mert apró betűs résznek ("small print") számít szemantikailag:

<body>
  <footer>
    <div class="wrapper">
      <small>©2017 <strong>Awesome Company</strong>, All Rights Reserved</small>
    </div>
  </footer>
</body>

Végül egy nav elemet adok még hozzá, három linkkel:

<body>
  <footer>
    <div class="wrapper">
      <small>©2017 <strong>Awesome Company</strong>, All Rights Reserved</small>
      <nav class="footer-nav">
        <a href="#">Back to Top</a>
        <a href="#">Terms of Use</a>
        <a href="#">Privacy</a>
      </nav>
    </div>
  </footer>
</body>

Remek, a HTML-váz készen áll, már csak meg kell formázni CSS segítségével.

Miért használjuk a <small> taget a szerzői jogi információhoz?
 Nincs ötletem, ez az elem a HTML5-ben elavult, és már nem kellene használni.
 Ez csak egy konténer, amely nem jelent semmit.
 Azt szeretnénk, hogyha ez kisebb lenne, mint a szöveg többi része, és a <small> célja a HTML5-ben az, hogy egy elem betűméretét beállítsa.
✅ A szerzői jogi információ apró betűs résznek számít, amit szemantikailag a <small> elemmel tudunk kifejezni.

Helyes válasz. Piros pont jár érte!

CSS 1.
Mint mindig, most is a következő lépéseken haladunk végig a formázás során:
1. Pozicionáljuk a footert és a tartalmát.
2. Hozzáadjuk az alap tipografikus stílusokat.
3. Befejezzük a speciális állapotok kezelésével.
Lássunk is neki.

Az elemek pozicionálása
Hogy könnyebben követhetővé váljanak a módosítások, egy egyszerű sárga hátteret adok a footernek:
footer {
  background: yellow;
}


A footer olyan vékony vagy vastag lehet, amilyet csak szeretnénk (vagy amilyet a tartalom kíván). Jelen esetben legyen mondjuk egy közepes méretű:
footer {
  background: yellow;
  height: 8rem;
}
 

Igazítsuk középre a tartalmat horizontálisan:
footer {
  background: yellow;
  height: 8rem;
  text-align: center;
}
 

Aztán vertikálisan:
footer {
  background: yellow;
  display: table;
  width: 100vw;
  height: 8rem;
  text-align: center;
}

.wrapper {
  display: table-cell;
  vertical-align: middle;
}
 
Remek! Végső lépésként a hátteret cseréljük le egy visszafogott mintás háttérre, és növeljük meg a tartalom körüli padding méretét:

footer {
  background: url('https://orange.codeberryschool.com/content/images/project-assets/simple-footer.png') repeat center;
  display: table;
  width: 100vw;
  height: 8rem;
  text-align: center;
  padding: 1rem;
}

.wrapper {
  display: table-cell;
  vertical-align: middle;
}
 

Hogyan rendeztük középre a tartalmat vertikálisan?
 Úgy, hogy a .wrapper-nek azt mondtuk, hogy viselkedjen táblázatként, a <footer>-t pedig ennek a táblázatnak a cellájaként deklaráltuk, majd a cella tartalmát a vertical-align tulajdonsággal pozicionáltuk.
 Úgy, hogy a <footer>-nek azt mondtuk, hogy viselkedjen táblázatként, a .wrapper-t pedig ennek a táblázatnak a cellájaként deklaráltuk, majd a cella tartalmát a text-align tulajdonsággal pozicionáltuk.
 ✅Úgy, hogy a <footer>-nek azt mondtuk, hogy viselkedjen táblázatként, a .wrapper-t pedig ennek a táblázatnak a cellájaként deklaráltuk, majd a cella tartalmát a vertical-align tulajdonsággal pozicionáltuk.
 Úgy, hogy a .wrapper-nek azt mondtuk, hogy viselkedjen táblázatként, a <footer>-t pedig ennek a táblázatnak a cellájaként deklaráltuk, majd a cella tartalmát a text-align tulajdonsággal pozicionáltuk.
Ellenőrzöm a válaszom
Nagyon vágod a témát! Igen, ez a jó válasz.


CSS 2.

Tipográfia
Először is változtassuk meg a font-family és a font-size értékét a teljes footerre vonatkozóan:
footer {
  background: url('http://i.imgur.com/f4jGhSF.png') repeat center;
  display: table;
  width: 100vw;
  height: 8rem;
  text-align: center;
  padding: 1rem;
  font-family: 'Arial', sans-serif;
  font-size: .875rem;
}
 
Szuper, kivéve, hogy igazából ezen a háttéren nem látszik a fekete színű, apró betűs rész. Itt az ideje megváltoztatni a szöveg színét (és eltávolítani az alapértelmezett díszítőelemeket a linkekről):
footer small {
  color: #ccc;
}

.footer-nav a {
  text-decoration: none;
  color: #c74f78;
}

Alakulnak a dolgok, csak még minden egy kicsit zsúfolt. Egy kis margó, és a betűköz méretének változtatása megoldja ezt:
footer small {
  color: #ccc;
  letter-spacing: .025rem;
  margin-bottom: 1.5rem;
  display: block;
}

.footer-nav a {
  text-decoration: none;
  color: #c74f78;
  margin: 0 .5rem;
  display: inline-block;
}
 
+1 tipp: A display értékekre azért van szükség, mert a small és az a elemek alapértelmezetten inline elemek, és ezért nem érvényesek rájuk egyes box-model értékek, mint a margó.

Végső simítások
A footer majdnem készen van, még a speciális állapotok és a legvégső simítások maradtak hátra. Például a linkeknek nincs még hover (egérrel rámutatott) állapota. Javítsunk ezen:
.footer-nav a:hover {
  color: #f26896;
  transition: color .15s ease-in-out;
}

Azt is észrevehetted, hogy a <strong> tagben lévő szöveg nem félkövér. A CSS reset ezt is kinullázta nekünk. Kézzel kell visszaállítanunk az elem eredeti formázását. Másold az alábbi szabályt az általános kiválasztóval a kódodba:
strong {
  font-weight: 700;
}

És ennyi. A cég neve most már feltűnőbb (ahogy szerettük volna), és elkészültünk az egyszerű footerrel.
Feladat:
Add hozzá a tipografikus stílusokat a CSS-edhez. Ha készen vagy, másold ide a CodePened linkjét.
A megoldásod: https://codepen.io/cybortybor/pen/abJWwzV