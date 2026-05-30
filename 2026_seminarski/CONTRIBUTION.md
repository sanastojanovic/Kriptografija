# Dodavanje sadržaja

Da biste dodali novo poglavlje u seminarski rad, pratite postojeći obrazac iz direktorijuma `chapters/uvod` i `chapters/zakljucak`.

## Struktura poglavlja

- kreirajte novi direktorijum u `chapters/ime_poglavlja` (ukoliko ne postoji)
- u njemu napravite fajl `ime_poglavlja.tex`
- u `main.tex` dodajte odgovarajući `\input{chapters/ime_poglavlja/ime_poglavlja.tex}` i naslov vašeg poglavlja

## Reference i paketi

- reference koje koristite dodajte u `references.bib`
- pakete i nove komande dodajte u `preambule.tex`

## Ako poglavlje ne postoji

Ako za neko poglavlje još ne postoji folder ili fajl, potrebno je da ih sami kreirate po istom obrascu kao za postojeća poglavlja. Nakon toga uključite novo poglavlje u `main.tex` kako bi se pojavilo u seminarskom radu.
