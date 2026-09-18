# Digitalni izdelki — navodila za postavitev

Trgovina je ena sama datoteka (`index.html`), ki teče popolnoma v brskalniku —
primerna za GitHub Pages. Izdelke bereš iz `products.json` v istem
repozitoriju, naročila pa prihajajo po e-pošti (brez plačevanja na strani).

## 1. Naloži datoteki na GitHub

1. Ustvari nov (ali uporabi obstoječi) javni repozitorij, npr. `moja-trgovina`.
2. Naloži vanj `index.html` in `products.json` (oba v koren repozitorija).
3. V nastavitvah repozitorija omogoči **Settings → Pages** in izberi vejo
   `main` (ali kakršno koli vejo uporabljaš) kot vir. GitHub ti bo dal
   povezavo, npr. `https://uporabnik.github.io/moja-trgovina/`.

## 2. Nastavi `CONFIG` na vrhu `index.html`

Odpri `index.html`, poišči blok `const CONFIG = { ... }` na začetku
`<script>` in izpolni:

- `githubOwner` — tvoje uporabniško ime na GitHubu
- `githubRepo` — ime repozitorija
- `githubBranch` — veja, npr. `main`
- `adminPassword` — geslo za vstop v skrbniško območje (spremeni ga!)
- `orderEmail` — e-poštni naslov, kamor naj prihajajo naročila

## 3. Nastavi prejemanje naročil po e-pošti (FormSubmit)

Naročilni obrazec uporablja brezplačno storitev
[formsubmit.co](https://formsubmit.co), ki pošlje vsebino obrazca naravnost
na tvoj e-poštni naslov — brez lastnega strežnika.

- Ob **prvem** naročilu ti bo FormSubmit poslal e-poštno sporočilo s prošnjo,
  da potrdiš aktivacijo za svoj naslov (klikni povezavo v e-pošti). Od takrat
  naprej vsa naročila prihajajo samodejno.
- Priporočljivo: pred objavo pošlji eno testno naročilo sam sebi, da preveriš,
  da vse deluje.

## 4. Ustvari GitHub token za skrbniško dodajanje izdelkov

Gumb "Admin" (zgoraj desno) najprej vpraša za geslo (`adminPassword`), nato
za **GitHub osebni dostopni žeton (token)**, s katerim skrbniška plošča
neposredno zapisuje spremembe v `products.json` v tvojem repozitoriju.

1. Pojdi na GitHub → **Settings → Developer settings → Fine-grained tokens**.
2. Ustvari nov token, omeji ga na ta repozitorij.
3. Pod **Repository permissions** nastavi **Contents: Read and write**.
4. Ustvari token in ga skrbno shrani (prikaže se samo enkrat).
5. Ta token vnašaš v obrazec ob prijavi v skrbniško območje — shrani se samo
   za trenutno sejo brskalnika (ne v datoteko, ne trajno).

⚠️ Token daje pravico do pisanja v repozitorij — ne deli ga in ga ne vnašaj
v skrbniško območje na tujem/deljenem računalniku.

## 5. Dodajanje izdelkov

V skrbniški plošči (po prijavi z geslom in tokenom) dodajaš izdelke z
naslovom, kategorijo, ceno, kratkim in polnim opisom, seznamom lastnosti in
sliko. Slike gostiš na [imgur.com](https://imgur.com): naloži sliko, nato z
desnim klikom nanjo izberi "Kopiraj naslov slike" (direktna `.jpg`/`.png`
povezava) in jo prilepi v polje za sliko.

Vsaka sprememba (dodajanje, urejanje, brisanje) se takoj zapiše kot nov
"commit" v `products.json` v tvojem repozitoriju — sprememba bo na spletni
strani vidna v nekaj sekundah do minuti (odvisno od predpomnjenja GitHub
Pages).

## Varnostna opomba

Geslo za skrbniški vstop je preverjeno v brskalniku (v kodi strani), zato je
namenjeno predvsem skrivanju gumba pred naključnimi obiskovalci — prava
zaščita je GitHub token, ki ga vnašaš posebej in ki edini omogoča dejansko
pisanje v repozitorij. Za resnično občutljive projekte razmisli o dodatni
zaščiti (npr. omejitev dostopa do skrbniške strani).
