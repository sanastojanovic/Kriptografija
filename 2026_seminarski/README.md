# 2026_seminarski

## Preduslovi

Potrebno je da imate instaliran `pdflatex` i `make`.

### Instalacija (Ubuntu/Debian)

```bash
sudo apt update
sudo apt install -y make texlive-latex-base texlive-latex-recommended texlive-latex-extra texlive-fonts-recommended texlive-lang-cyrillic
```

## Build

Sve komande se pokreću iz foldera `2026_seminarski`.

### Glavni PDF - kompletna skripta sa svim poglavljima

```bash
make main
```

Rezultat: `kriptografija_napredne_teme.pdf`

### Sve

```bash
make all
```

### Čišćenje outputa

```bash
make clean
```

Makefile uklanja pomoćne fajlove nakon svake kompilacije, tako da ostaje
samo glavni PDF izlaz.
