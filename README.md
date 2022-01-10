# Dokumentacija

## Opis

Aplikacija bo športnim klubom in trenerjem omogočala vodenje obveznosti. Klubi lahko dodajajo nove trenerje in igralce kot uporabnike ter igrišča. Aplikacija omogoča rezervacijo igrišča, kjer se lahko določi čas in tip rezervacije kot tudi trenerja, ki bo vodil dogodek. Trenerji lahko za določene igralce doda opazke in mnenja o njihovem napredku. Prav tako se vodi evidenca prodanih rekvizitov, ki imajo shranjen tip in ceno rekvizita ter trenerja, ki je bil odgovoren za njegovo prodajo. Za trenerja lahko prav tako izračunamo njihov zaslužek, ki je sestavljen iz procenta cene rekvizitov, ki jih je prodal trener in števila rezervacij oziroma dogodkov, ki jih ima ta trener.

## Ogrodje

Za izdelavo aplikacije smo uporabili razvojno okolje IntelliJ IDEA, Javo 13 in ogrodju KumuluzEE. Kot ponudnika oblačnih storitev, kjer je nameščeno okolje kubernetes, pa smo izbrali Azure. Frontend je bil narejen v Angular-ju.

## Seznam izpostavljenih točk

Mikrostoritev Igralci:

       1.GET, POST, PUT in DELETE zahteve

Mikrostoritev Igrisca:

       1. GET, POST, PUT in DELETE zahteve 
       2. /igrisca/igriscaId -\> vrne vse id-je igrišč

Mikrostoritev Uporabniki:

       1. GET, POST, PUT in DELETE zahteve
       2. /uporabniki/trenerji -\> vrne vse uporabnike, ki so trenerji
       3. /uporabniki/trenerjiId -\> vrne vse id-je uporabnikov, ki so trenerji

Mikrostoritev Rezervacije:

       1. GET, POST, PUT in DELETE zahteve
       2. rezervacije?trenerId={trenerId} -> vrne rezervacije trenerja z id-jem trenerId
       3. rezervacije?igrisceId={igrisceId} -> vrne vse rezervacije, ki so na igrišči z id-jem igrisceId

Mikrostoritev Rekviziti:

       1. GET, POST, PUT in DELETE zahteve
       2. rekviziti//cena/{trenerId} -> vrne ceno vseh rekvizitov, ki jih je prodal trener z id-jem trenerId

Mikrostoritev Postavke:

       1. GET, POST, PUT in DELETE zahteve
       2. postavke/place -> vrne plače za vse uporabnike, ki so trenerji
       3. postavke?trenerId={trenerId} -> vrne postavko od trenerja z id-jem trenerId

## Shema povezav rešitve

![shema](https://user-images.githubusercontent.com/56541694/147965503-60c93adb-1d1a-455d-ae67-d913dda5dddc.PNG)

V shemi so skoraj vse povezave med mikrostoritvami HTTP/synchronous REST. Dodali pa smo tudi asinhrono povezavo med mikrostoritvama Postavke in Uporabniki. Tu je asinhrona povezava narejena tako, da ko se ustvari nov uporabnik z vlogo trenerja ali pa posodobi trenutni uporabnik na vlogo trenerja se kliče asinhron REST klic, ki novemu trenerju naredi privzeto postavko.

## Ingress

Ingress je nastavljen čez naslove vseh mikrostoritev, da so izpostavljene na skupnem IP-ju: http://40.76.175.239, z dodanimi maskami enakimi imenom mikrostoritev ("/igralci", "/igrisca",...).


