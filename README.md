# Iosevka ![Version](https://img.shields.io/github/release/be5invis/Iosevka.svg) [![Donate](https://img.shields.io/badge/donate-alipay-orange.svg)](http://7xpdnl.dl1.z0.glb.clouddn.com/T1v4huXnleXXXXXXXX.png)

Coders' typeface, built from code. //[→ Inziu Iosevka for Chinese and Japanese.](http://be5invis.github.io/Iosevka/inziu.html)

![](https://raw.githubusercontent.com/be5invis/Iosevka/master/images/preview-all.png)

## Installation

Quit your editor/program. Unzip and open the folder.

* **[Instructions for OS X](http://support.apple.com/kb/HT2509)**
* **[Instructions for Windows](https://www.microsoft.com/en-us/Typography/TrueTypeInstall.aspx)**
* **Linux** : Copy the .ttf files to your fonts directory → Run `sudo fc-cache`. 
  - Arch Linux users can install the font from the AUR [here](https://aur.archlinux.org/packages/ttf-iosevka) using an AUR wrapper or by doing it manually. [All variants](https://aur.archlinux.org/packages/?O=0&SeB=nd&K=ttf-iosevka&SB=n&SO=a&PP=50&do_Search=Go).
  - Void Linux users can install the font with `xbps-install font-iosevka`.

## Weights, Variants and OpenType features

The typeface contains seven weights (thin, extra-light, light, regular, medium, bold and heavy) alongside with both italic and oblique versions, with the same metrics as the regular one. 

![Weights sample](https://raw.githubusercontent.com/be5invis/Iosevka/master/images/weights.png)

All versions include the same ranges of characters: Latin letters, Greek letters (including Polytonic Greek), some Cyrillic letters, IPA symbols and common punctuations and some symbols. You can check out the full list [here](http://be5invis.github.io/Iosevka/specimen.html).

![Languages Sample](https://raw.githubusercontent.com/be5invis/Iosevka/master/images/languages.png)

Iosevka supports accessing all letter variants using OpenType features.

![OpenType Sample](https://raw.githubusercontent.com/be5invis/Iosevka/master/images/opentype.png)

## Ligations (Experimental)

![Ligations Sample](https://raw.githubusercontent.com/be5invis/Iosevka/master/images/ligations.png)

Iosevka’s default ligation set is assigned to `calt` feature, though not all of them are enabled by default. Iosevka supports Language-Specific Ligations, which is the ligation set enabled only under certain languages. These ligation sets are assigned to custom feature tags, like `XHS_`.

## Building from Source

To build Iosevka you should:

1. Ensure that [`nodejs`](http://nodejs.org) (≥ 6.0), [`ttfautohint`](http://www.freetype.org/ttfautohint/), [`otfcc`](https://github.com/caryll/otfcc) (≥ 0.4.4) and `make` are runnable in your terminal.
   - Windows users may need to install MinGW and make \*nix utilities accessible (`mkdir.exe`, `cp.exe`, `cat.exe` and `rm.exe`, in particular) from Command Prompt. Utilities provided by [Git for Windows](https://git-for-windows.github.io/) works fine.
2. Install necessary libs by `npm install`. If you’ve installed them, upgrade to the latest.
3. `make`.
   - Use `make DONTHINT=1` to disable hinting.
   - Use `make DONTREF=1` to turn off reference-ify (will increase file size but provide better compatibility).


You will find TTFs in the `dist/` directory.

### Building the Web Font

The `webfonts/` directory is used to build Iosevka for web font uses. To build the web fonts you should:

1. Build Iosevka.
2. Ensure that `sfnt2woff` and `woff2_compress` are installed and runnable.
3. Run `make web` .

The web fonts will be generated into `dist/iosevka/web` and `dist/iosevka-slab/web`.

## Build Your Own Style

![Styles Preview](https://raw.githubusercontent.com/be5invis/Iosevka/master/images/variants.png)

Iosevka comes with several visual styles, however they are inactive using the default build. To build these variants, you should perform custom build:

1. `make custom-config [set=<name>]` with the parameters listed below to create a configuration. The `set=<name>` part is optional, it will be set to `custom` when absent.
2. `make custom [set=<name>]` to acquire your custom font.
   - `make custom-web [set=<name>]` is for web fonts.

The first step, `make custom-config` takes following parameters to set styles of your custom build. All of them are optional, and would default to Iosevka’s default configuration:

* `design='<styles>'`, styles for your custom font set.
* `upright='<styles>'`, styles for uprights only.
* `italic='<styles>'`, styles for italics only.
* `oblique='<styles>'`, styles for obliques only.

You can add arbitary styles for these variables, for example, `make custom-config upright='v-l-zshaped v-i-zshaped' && make custom` will create a variant with Z-shaped letter `l` and `i` for uprights.

The current avaliable styles are:

* Styles for general shape:
  * `sans` : Sans serif (default).
  * `slab` : Slab serif. When present, the family of your font would be `Iosevka Slab`.
* Styles related to ligations
  - `term` : Disable ligations. When this style is present, the font built will not contain ligatures, and its family name will be set to `Iosevka Term`. In case of your OS or editor cannot handle ligatures correctly, you can disable ligations with it.
* Styles for letter `l`:
  * `v-l-hooky` : Hooky `l`.
  * `v-l-zshaped` : Z-shaped `l`.
  * `v-l-serifed` : Serifed `l` (default for upright and oblique).
  * `v-l-italic` : Italic `l` (default for italic).
  * `v-l-tailed` : `l` with a curved tail.
  * `v-l-hookybottom` : `l` with a straight tail.
* Styles for letter `i`:
  * `v-i-hooky` : Hooky `i`.
  * `v-i-zshaped` : Z-shaped `i`.
  * `v-i-serifed` : Serifed `i` (default for upright and oblique).
  * `v-i-italic` : Italic `i` (default for italic).
* Styles for letter `a`:
  * `v-a-doublestorey` : Double-storey `a` (default for upright and oblique).
  * `v-a-singlestorey` : Single-storey `a` (default for italic).
* Styles for letter `g`:
  * `v-g-doublestorey` : Double-storey `g` (default).
  * `v-g-singlestorey` : Single-storey `g`.
  * `v-g-opendoublestorey` : Open Double-storey `g`.
* Styles for letter `m`:
  * `v-m-longleg` : `m` with long middle leg (default).
  * `v-m-shortleg` : `m` with shorter middle leg.
* Styles for letter `0`:
  * `v-zero-slashed` : Slashed Zero `0` (default).
  * `v-zero-dotted` : Dotted Zero `0`.
  * `v-zero-unslashed` : O-like `0`.
* Styles for ASCII tilde (`~`), asterisk (`*`), paragaraph(`¶`), and ASCII Caret (^):
  * `v-tilde-high` : Higher tilde `~`.
  * `v-tilde-low` : Lower tilde `~` (default).
  * `v-asterisk-high` : Higher asterisk `*` (default).
  * `v-asterisk-low` : Lower asterisk `*`.
  * `v-paragraph-high` : Higher paragraph symbol `¶` (default).
  * `v-paragraph-low` : Lower paragraph symbol `¶`.
  * `v-caret-high` : Higher circumflex `^` (default).
  * `v-caret-low` : Lower circumflex `^`.
* Styles for At (@):
  * `v-at-long` : The long, three-fold At symbol in Iosevka 1.7.x.
  * `v-at-fourfold` : The traditional, four-fold At symbol.
  * `v-at-short` : The shorter, Fira-like At symbol introduced in Iosevka 1.8.
* Styles for Eszet(ß)
  * `v-eszet-traditional` : Tratidional, Fraktur-like Eszet.
  * `v-eszet-sulzbacher` : A more modern, beta-like Eszet (default).
* Styles for curly brackets ({})
  * `v-brace-straight` : More straight braces.
  * `v-brace-curly` : More curly braces (default).

![Family Matrix](https://raw.githubusercontent.com/be5invis/Iosevka/master/images/matrix.png)