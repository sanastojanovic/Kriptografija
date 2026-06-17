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
## Font issue (Linux)

Ukoliko se tokom kompajliranja pojavi greška:

```text
Package fontspec Error: The font "FiraSans-Regular" cannot be found.
```

u fajlu `beamerfontthemewildcat.sty` potrebno je zameniti kompletan blok:

```latex
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
%% DEFAULT — Fira Sans
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
...
\fi\fi\fi\fi  % end default block
```

sledećim kodom:

```latex
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
%% DEFAULT — Fira Sans
%%
%% Ships with MiKTeX and TeX Live as the "fira" package; pre-installed on
%% Overleaf. No font files need to be bundled with your presentation.
%%
%% MiKTeX:  auto-installs on first compile.
%% TeX Live: run  tlmgr install fira  if not already installed.
%% Overleaf: works out of the box.
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
\def\wc@tmp{nu}\ifx\wc@fontopt\wc@tmp\else
\def\wc@tmp{poppins}\ifx\wc@fontopt\wc@tmp\else
\def\wc@tmp{installed}\ifx\wc@fontopt\wc@tmp\else
\def\wc@tmp{noto}\ifx\wc@fontopt\wc@tmp\else

\newfontfamily\FiraRegular{Fira Sans}[
    UprightFont    = * Regular,
    ItalicFont     = * Italic,
    BoldFont       = * SemiBold,
    BoldItalicFont = * SemiBold Italic,
]

\newfontfamily\FiraLight{Fira Sans}[
    UprightFont    = * Light,
    ItalicFont     = * Light Italic,
    BoldFont       = * Regular,
    BoldItalicFont = * Italic,
]

\newfontfamily\FiraExtraLight{Fira Sans}[
    UprightFont    = * ExtraLight,
    ItalicFont     = * ExtraLight Italic,
    BoldFont       = * Light,
    BoldItalicFont = * Light Italic,
]

\setbeamerfont{title}{family=\FiraRegular, size=\LARGE}
\setbeamerfont{author}{family=\FiraLight, size=\small}
\setbeamerfont{frametitle}{family=\FiraLight, size=\Large}
\setbeamerfont{section}{family=\FiraExtraLight, size=\LARGE}

\setsansfont{Fira Sans}

\fi\fi\fi\fi  % end default block
```
