# **Predikcia sily slnečných erupcií zo snímok slnečnej koróny**

## Popis
Tento repozitár obsahuje praktickú časť bakalárskej práce, cieľom ktorej bolo navrhnúť a implementovať vhodné modely strojového učenia na predikciu sily slnčených erupcií na základne obrazových dát slnečnej koróny.

Modely boli trénované na dátach z kanála AIA 1600 Å, získaných observatóriom Solar Dynamics Observatory (SDO), pričom ako zdroj informácií slúžili súbory ribbondb_v1.0.csv a flares3.csv.

## Štruktúra projektu
```
.
├── cnn/                                         
│   ├── ...                      - všetky uložené modely
│
├── csv's/                       - Zdrojové súbory slúžiace na sťahovanie snímok slnečnej koróny
│   ├── flares.csv               - Pôvodný dataset obsahujúci informácie o dátach typu flares, Zdroj: [Bobra Flares] (https://github.com/mbobra/mapping-solar-flares)
│   ├── flares2.csv              - Kópia flares.csv, upravené hodnoty latitude a longitude podľa prepočtov
│   ├── flares3.csv              - Kópia flares.csv, zamenené názvy stĺpcov latitude a longitude (konečný dataset, slúžil na sťahovanie obrázkov)
│   └── ribbondb_v1.0.csv        - Pôvodný dataset obsahujúci informácie o dátach rypu ribbons, Zdroj: [Kazachenko RibbonDB (https://solarmuri.ssl.berkeley.edu/~kazachenko/RibbonDB/)
│
├── notebooks/                 
│   ├── ...                        
│   ├── Experiment1              - Architektúra a výsledky modelov z Experimentu 1 (jednoduchá CNN, multi-class, dáta = ribbons)
│   ├── Experiment2              - Architektúra a výsledky modelov z Experimentu 2 (jednoduchá CNN, multi-class, dáta = flares)
│   ├── Experiment3              - Architektúra a výsledky modelov z Experimentu 3 (CNN s VGG16, multi-class, dáta = ribbons + flares)
│   ├── Experiment4              - Architektúra a výsledky modelov z Experimentu 4 (CNN s ResNet50, multi-class, dáta = ribbons + flares)
│   ├── Experiment5              - Architektúra a výsledky modelov z Experimentu 5 (CNN s ResNet50, multi-label, dáta = ribbons + flares)
│   ├── flares_stahovanie        - Sťahovanie obrázkov typu flares, rozdeľovanie do trénovacej, testovacej a validačnej množiny
│   ├── priprava_dat_ribbondb    - Príprava a analýza dát typu ribbons
│   ├── ribbons_stahovanie       - Sťahovanie obrázkov typu ribbons
│   └── ribbons_train_test       - Rozdeľovanie obrázkov typu ribbons do trénovacej, testovacej a validačnej množiny
│
├── README.md                    - Aktuálny súbor s popisom projektu

```
## Priečinky s obrázkami
- experimentFlaresRibbons - Kombinované obr. typu flares a ribbons (5 pred + PEAK + 5 po -> 11 obrázkov pre každú udalosť)
- flares                  - Obr. typu flares (5 pred + PEAK + 5 po -> 11 obrázkov pre každú udalosť)
- ribbons                 - Obr. typu ribbons (5 pred + PEAK + 5 po -> 11 obrázkov pre každú udalosť)

# Použité knižnice v programovacom jazyku Python
| Knižnica     | Verzia | Popis                                                     |
|--------------|--------|-----------------------------------------------------------|
| TensorFlow   | 2.19.0 | Trénovanie a vytváranie CNN modelov.                      |
| Scikit-learn | 1.1.3  | Metriky, váhy tried, rozdelenie dát.                      |
| Matplotlib   | 3.6.3  | Vizualizácia grafov a obrázkov.                           |
| Seaborn      | 0.11.2 | Vizualizácia dát cez confusion matrix.                    |
| NumPy        | 1.24.0 | Práca s číselnými poliami, normalizácia, predspracovanie. |
| Pandas       | 1.5.3  | Manipulácia s dátovými tabuľkami.                         |
| Astropy      | 6.1.4  | Astronomické jednotky a súradnice.                        |
| SunPy        | 6.0.3  | Manipulácia s astronomickými obrázkami z observatórií.    |
| hvpy         | 1.1.0  | Sťahovanie slnečných snímok z Helioviewera.               |
| aiapy        | 0.7.4  | Kalibrácia slnečných obrázkov.                            |
| Pillow (PIL) | 9.2.0  | Práca s obrázkami.                                        |
| SciPy        | 1.9.3  | Špeciálne matematické funkcie.                            |


Tento projekt bol realizovaný ako súčasť bakalárskej práce na Technickej Univerzite v Košiciach.


