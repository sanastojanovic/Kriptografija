# 2026_prezentacije

## Preduslovi

Potrebno je da imate instaliran `xelatex` i `make`.

### Instalacija (Ubuntu/Debian)

```bash
sudo apt update
sudo apt install -y make texlive-latex-base texlive-latex-recommended texlive-latex-extra texlive-fonts-recommended
```

## Build

Sve komande se pokrecu iz foldera `2026_prezentacije`.

### Novi projekat

```bash
make new name=mpc1
```

### Build jednog projekta

```bash
make build name=mpc1
```

### Build svih projekata

```bash
make all
```

### Čišćenje outputa

```bash
make clean-aux name=mpc1
```
