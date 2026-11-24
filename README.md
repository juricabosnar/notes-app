# Bilješke – PWA za pisanje olovkom

Jedan `index.html` + service worker. Radi online i offline, instalira se na Samsung Tab (Chrome/Samsung Internet → "Dodaj na početni zaslon / Instaliraj").

## Pokretanje
1. Postavi na bilo koji HTTPS hosting (npr. Firebase Hosting: `firebase deploy --only hosting,firestore`).
2. Otvori na tabletu i instaliraj kao aplikaciju. Bez Firebasea sve radi lokalno (IndexedDB).
3. U Postavkama (⚙) odaberi "Pripremi offline" dok si online – sprema OCR (hrvatski) i PDF module za offline.

## Sync i javni linkovi (opcionalno)
1. Firebase Console → projekt → Authentication → uključi Google; Firestore → Create database.
2. Project settings → Your apps → Web → kopiraj config u `FIREBASE_CONFIG` na vrhu skripte u `index.html`.
3. Objavi pravila iz `firestore.rules`. Dodaj domenu hostinga u Authentication → Authorized domains.
4. Na popisu bilješki dodirni ☁ i prijavi se istim Google računom na tabletu i telefonu.

Sync je "zadnja izmjena pobjeđuje" po bilješci. Bilješke se spremaju u Firestore u komadima (nema Storagea). Jedna bilješka može imati nekoliko MB (slike, PDF).

## OCR i AI
- Tekst sa slike: Tesseract.js (hrvatski + engleski), radi i offline nakon "Pripremi offline".
- Rukopis → tekst, AI sažetak, zadaci, uređivanje: Claude API. Ključ se unosi u Postavkama i sprema samo na uređaj (poziv ide direktno iz preglednika).

## Olovka
- Pritisak, S Pen tipka = gumica, prst pomiče/zumira dok olovka piše (palm rejection; isključivo u alatnoj traci ✋).
- Zadrži olovku na kraju poteza → ravna crta, elipsa ili pravokutnik (◇ uključuje/isključuje).
- PIN na bilješci je zaključavanje otvaranja, a ne enkripcija.
