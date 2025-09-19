---
title: "Diskrete Packungsstrukturen als Randbedingung für die Feinstrukturkonstante"
subtitle: "Kurzpapier"
author: "Marco Gerodetti"
date: last-modified
fontsize: 11pt
lang: de-CH
mainfont: Libertinus Serif
mathfont: Libertinus Math
monofont: Iosevka
geometry: a4paper
margin: 1.5cm
colorlinks: true
linkcolor: blue
toc: true
toc-depth: 2
numbersections: true
header-includes:
  - \newcommand{\docversion}{1.0.0}
  - \usepackage{fontawesome5}
  - \usepackage{booktabs,longtable,array,tabularx}
  - \usepackage[table]{xcolor}
  - \usepackage{caption}
  - \definecolor{RowAlt}{HTML}{F7F7F7}
  - \arrayrulecolor{black!40}  
  - \renewcommand{\arraystretch}{1.15}  
  - \setlength{\tabcolsep}{6pt}  
  - \setlength{\LTpre}{0.5\baselineskip}  
  - \setlength{\LTpost}{0.5\baselineskip} 
  - \captionsetup[table]{skip=4pt,labelfont=bf}
  - \usepackage{etoolbox}
  - \AtBeginEnvironment{longtable}{\rowcolors{2}{RowAlt}{white}}
  - \usepackage[most]{tcolorbox}
  - \usepackage{xcolor}
  - \definecolor{CalloutFrame}{HTML}{B0BEC5}
  - \definecolor{CalloutBack}{HTML}{F7F9FA} 
  - \newtcolorbox{calloutbox}{
      colback=CalloutBack,
      colframe=CalloutFrame,
      leftrule=2pt, rightrule=0pt, toprule=0pt, bottomrule=0pt,
      boxrule=0.4pt, arc=2pt,
      left=2mm, right=2mm, top=1.2mm, bottom=1.2mm,
      breakable, enhanced
    }
  - \let\oldquote\quote
  - \let\endoldquote\endquote
  - \renewenvironment{quote}{\begin{calloutbox}}{\end{calloutbox}}
  - \usepackage{tikz}
  - \usepackage{float}
  - \usetikzlibrary{positioning}
  - \usetikzlibrary{arrows.meta}
  - \usetikzlibrary{shapes.misc}
  - \usepackage{fancyhdr}
  - \usepackage{slashed}
  - \pagestyle{fancy}
  - \fancyhead{}
  - \fancyfoot{}
  - \fancyhead[L]{\nouppercase{\rightmark}}
  - \fancyhead[R]{Rev. \docversion{}}
  - \fancyfoot[C]{\thepage}
  - \renewcommand{\sectionmark}[1]{}
  - \renewcommand{\subsectionmark}[1]{\markright{#1}}
  - \let\oldsubsection\subsection
  - \renewcommand{\subsection}[1]{\oldsubsection{#1}\markright{#1}}
  - \usepackage{parskip}
  - \setlength{\parskip}{0.6em}
  - \setlength{\parindent}{1.0pt}
  - \clubpenalty=10000
  - \widowpenalty=10000
  - \displaywidowpenalty=10000
  - \newcommand{\Tr}{\operatorname{Tr}}
  - \renewcommand{\figurename}{Abb.}
  - \renewcommand{\tablename}{Tab.}
bibliography: references/Alpha0.json
link-citations: true
---
<!-- markdownlint-disable MD025 -->
<!-- STYLEGUIDE
    PDF-Build: "xelatex"/"lualatex"; "--citeproc", "linkReferences:true",       "link-citations:true".
    Bibliographie: YAML "bibliography: [./refs/alpha.json]" (CSL-JSON bevorzugt).
    Zitate: "[@id]" parenthetisch, "@id" narrativ. Keine zusätzlichen () setzen.
    Links intern: Überschriften "{#id}" → "[Text](datei.md#id)"; Gleichungen/Abbildungen/Tabellen mit "(@eq:id)", @fig:id, @tbl:id.
    Gleichungen: "$$ … $$ {#eq:id}"; im Text "[Gleichung @eq:id]".
    Abbildungen/Tabellen: "![Text](pfad){#fig:id}" → „Abb. @fig:id“; "Table: … {#tbl:id}" →       „Tab. @tbl:id“.
    Web: "accessed: YYYY-MM-DD"; URLs umbrechbar mit "\PassOptionsToPackage{hyphens}{url}".
    Zeichensatz: UTF-8; nur ASCII in Dateinamen/IDs; keine NBSP/NBH; Mathe immer LaTeX-Math.
    Absätze/Umbrüche: Absätze mit Leerzeile, Hardbreaks mit zwei  Spaces.
    Callouts: "[!note]/[!tip]/[!abstract]" → "> **Note/Tip/Abstract:** …" (alle Zeilen mit "> ").
    Code: Fenced Code Blocks mit Sprache (```python, ```bash …); Inhalt unverändert.
-->

\newpage
# Abstract

Wir stellen eine phänomenologische, fitfreie Randbedingung im Thomson-Limit für die Feinstrukturkonstante α(0) vor, abgeleitet aus diskreten Packungsstrukturen (Tetra/BCC/FCC) und einem Orientierungsprojektor. Analytisch ergibt sich
$$
\alpha^{-1}_{\mathrm{Theo}}(0) = n_0 + \Delta_\eta,\qquad
\Delta_\eta = \Bigl(1 - \tfrac{1}{3\cdot5\cdot11}\Bigr)\,\frac{9\sqrt{3}}{\pi n_0},\quad
n_0=1+1+n_3,\quad n_3=\operatorname{round}(n_8)=135.
$$
Damit erhält man den Zahlenwert
$$
\alpha^{-1}_{\mathrm{Theo}}(0) = 137.035999179,
$$
konsistent mit CODATA 2022 und dem PDG-World-Average 2024.
Ein blinder Dichte-Cross-Check bestimmt $n_3$ über das $\rho$-Modell
$$
\frac{\rho_P}{\rho_{\mathrm{ref}}\eta_{\mathrm{eff}}}=12\cdot 8^{n_8},\qquad
n_3 = \operatorname{round}(n_8),
$$
ohne Zugriff auf $\alpha$.

**Motivation.** Ausgehend von der Annahme, dass auf Planck-Skalen diskrete Packungsprobleme relevant sein können, verfolgt dieses Papier nicht deren vollständige Lösung, sondern untersucht, ob einfache Packungsstrukturen im Zuge von Symmetriebildung Randbedingungen für fundamentale Konstanten wie die Feinstrukturkonstante nahelegen.

> **Kerndefinitionen (Kurz)**
>
> - $\eta_1=\tfrac12-\tfrac{1}{2\cdot3\cdot5\cdot11}$, $\ \eta_2=\tfrac{\pi\sqrt{3}}{8}$, $\ \eta_{\mathrm{FCC}}=\tfrac{\pi}{3\sqrt{2}}$.
> - **Projektor:** Faktor $2^k$ mit $k=3$ (drei Achsenklassen $\times$ zwei Orientierungen).
> - **Frustrationskorrektur:** $\displaystyle \Delta_\eta=\Bigl(1-\tfrac{1}{165}\Bigr)\frac{9\sqrt{3}}{\pi n_0}$.
> - **$\rho$-Pfad (blind):** $\displaystyle \frac{\rho_P}{\rho_{\mathrm{ref}}\eta_{\mathrm{eff}}}=12\cdot 8^{n_8}$, $n_3=\mathrm{round}(n_8)$, $n_0=1+1+n_3$.
> - **Effektive Dichte:** $\eta_{\mathrm{eff}}=\tfrac12\,\eta_{\mathrm{FCC}}^{4/3}+\tfrac12\,\eta_{\mathrm{FCC}}^{2}$.
> *Details siehe [Anhang A](#anhang-notation)*

\newpage
# Einleitung

Die inverse Feinstrukturkonstante $\alpha^{-1}(0)$ wird hier als Konsequenz einer diskreten Packungsstruktur betrachtet. Ausgangspunkt ist

$$
n_0=n_1+n_2+n_3=1+1+n_3,
$$

wobei $n_3\equiv n_{\mathrm{FCC}}=\operatorname{round}(n_8)$ aus einem dichtebasierten Modell bestimmt wird ([Anhang D](#anhang-rho-modell)).

Ziel ist nicht, $n_0$ aus ersten Prinzipien zu berechnen, sondern die Abweichung als geometrische Frustrationskorrektur $\Delta_\eta$ analytisch herzuleiten – ausschliesslich aus wohldefinierten Packungsdichten, ohne Fits.

Physikalisch ergibt sich so eine fitfreie Randbedingung für $\alpha^{-1}(0)$ im Thomson-Limit; die QED-Running bleibt Standard. Wir verwenden diskrete Packungsstrukturen (FCC/BCC) als Modellannahme. Mikroskopisch sind feste diskrete Belegungen nicht rotationsinvariant; makroskopisch ergibt eine isotrope Orientierungsmittelung eine isotrope effektive Antwort (Thomson-Limit; vgl. *Effektive Lorentzinvarianz* und [Anhang H](#anhang-maxwell-thomson)).  
Alle Grössen sind analytisch, reproduzierbar und falsifizierbar. Präzisere Messungen von $\alpha^{-1}(0)$ können die Hypothese direkt bestätigen oder widerlegen. Integritätsnachweise gegen a-posteriori-Anpassungen siehe [Validierung](#validierung).

> **Kurzüberblick.**  
> Wäre die frühe Raumteilung perfekt dicht, ergäbe sich $\alpha^{-1}(0)=n_0$. Die ersten beiden Teilungen sind jedoch minimal ineffizient; die Frustration summiert sich zu $\Delta_\eta\approx 0.036$, sodass $\alpha^{-1}(0)=n_0+\Delta_\eta$ entsteht – fitfrei aus Geometrie und projektiver Zählung.  

## Begriffe & Abgrenzungen  

- **Geltungsbereich (Thomson-Limit):** Aussage nur für $Q^2\to 0$; die QED-Running bleibt Standard.  
- **Kanäle (nur Randbedingung):** *Phasenraum* (E-Feld, tangential, isotrop) und *Magnetfluss* (B-Feld, normalorientiert; magnetische Flussdichte). Gleichgewichtung im Nullimpuls; Begründung und Ableitung siehe [Anhang H](#anhang-maxwell-thomson) sowie [H.1](#etaeffexp).  
- **Projektorfaktor (rein projektiv):** $2^{k}$ als Orientierungs-Zählmass mit $k=3$ (D$_6$-Isotropie; drei ungerichtete Achsenklassen). Dieser Faktor ist **getrennt** von geometrischen Dichten.  
- **Geometrische Dichten (rein geometrisch):** $\eta_{1}$, $\eta_{2}=\pi\sqrt{3}/8$ (BCC), $\eta_{\mathrm{FCC}}=\pi/(3\sqrt{2})$ (FCC-Referenz). Die „8“ in $\eta_{2}$ ist **geometrisch** und **nicht** der Projektorfaktor.  
- **Effektive Dichte:** $\eta_{\mathrm{eff}}=\tfrac12\,\eta_{\mathrm{FCC}}^{4/3}+\tfrac12\,\eta_{\mathrm{FCC}}^{2}$ (Thomson-Matching, isotrope Mode-Mittelung; Herleitung in [Anhang H](#anhang-maxwell-thomson)).  
- **$\rho_{\mathrm{ref}}$ (kosmologische Referenzdichte):** elektromagnetische Energiedichte (Photonen/CMB) als Anteil der kritischen Dichte; numerische Werte gemäss **Planck 2018**; Einheiten konsistent mit $\rho_P$. *Zweck:* definiert den Referenzmassstab im $\rho$-Pfad; die absolute Skala kürzt sich im Verhältnis $\rho_P/(\rho_{\mathrm{ref}}\eta_{\mathrm{eff}})$.
- **„12“ im $\rho$-Pfad (Normierung):** fester Vorfaktor $12$; **Definition & Begründung siehe [Anhang G](#anhang-12)**.  
*Leserführung:* Projektorfaktor: [Anhang B](#anhang-projektor) / [Anhang F](#anhang-projektor-zaehlmass); Rolle der „11“: [Anhang E](#anhang-satz11).

## Scope & Roadmap

- Fitfreie Randbedingung im Thomson-Limit; "11 *mod* (3,5)" als Arbeitshypothese mit BFS-Evidenz; QED-Running unverändert.
- Fahrplan: (1) $n_3$ blind aus dem $\rho$-Pfad, (2) $\Delta_\eta$ aus Packungsdichten + $2^{k}$ mit $k=3$, (3) $\alpha^{-1}(0)=n_0+\Delta_\eta$, Vergleich mit CODATA/PDG und Zertifikaten.
- Reproduzierbarkeit: Rechengang, Zahlen und Gleichungen im Notebook automatisch generiert; Referenzen CODATA 2022, PDG 2024, Planck 2018 [@codata2022; @pdg2024; @planck2018].

## Historischer Kontext: frühere numerologische Ansätze

Es gab zahlreiche Versuche, die Feinstrukturkonstante $\alpha$ rein mathematisch zu bestimmen.  
Arthur Eddington postulierte in den 1920er Jahren eine „kosmische Zahl“ und kam zunächst auf $1/136$, später auf $1/137$.  

Armand Wyler (1969/71) leitete eine Formel aus Volumina symmetrischer Räume her; sie traf damals ppm-genau, erwies sich jedoch als formal problematisch und blieb physikalisch unklar.  

Der vorliegende Ansatz unterscheidet sich grundlegend: Er verwendet **keine a-posteriori-Justage und keine Fits**, sondern quantifiziert eine geometrisch definierte Frustrationsstruktur als Korrektur zu $n_0=1+1+n_3$ (mit $n_3$ dichtebasiert).

\newpage

# Gegenstand

Eine systematische Analyse der geometrischen Packungsdichten der frühesten Raumteilungen liefert eine exakt berechenbare Korrektur zur idealisierten Zahl  
$$
n_0 = 1+1+n_3
$$ {#eq:n0}

(bei $n_3=135$ also $1+1+135$). Der resultierende Wert ist vollständig aus kleinen natürlichen Zahlen, $\pi$, $\sqrt{2}$ und $\sqrt{3}$ aufgebaut.

## Geometrische Teilungsdichten

Drei aufeinanderfolgende Raumteilungen bestimmen die Frustration:

| Teilung | Struktur                                      | Dichte $\eta$ | Exakter Ausdruck            |
|:------:|:-----------------------------|:-------------:|:----------------------------------------------------:|
| 1      | teträdrische Teilstruktur      | $\eta_1$      | $\dfrac{1}{2} - \dfrac{1}{2 \cdot 3 \cdot 5 \cdot 11}$ |
| 2      | BCC (körperzentriert kubisch)  | $\eta_2$      | $\dfrac{\pi \cdot \sqrt{3}}{8}$                    |
| 3      | FCC (flächenzentriert kubisch) | $\eta_{\mathrm{FCC}}$ | $\dfrac{\pi}{3 \cdot \sqrt{2}}$            |
*Referenz zu Standard-Packungsdichten (BCC/FCC/Tetra): [@ashcroft1976; @purdueChem].*

> **Hinweis (Faktoren 8 vs. Projektor):** 
> Der Nenner $8=2^3$ in der **BCC-Dichte** $\eta_2=\pi\sqrt{3}/8$ ist **rein geometrisch** (Packungsgeometrie) und **nicht** der projektive Faktor. Die **projektive Zählung** (Orientierungstrennung) wird **separat** als $2^{k}$ mit $k=3$ geführt. Siehe [Definitionskasten](#anhang-projektor-def).

> **Hinweis (Status von $\eta_1$):** 
> Die exakte geometrisch-topologische Ableitung von $\eta_1=\tfrac{1}{2}-\tfrac{1}{2\cdot3\cdot5\cdot11}$ (insbesondere die Identifikation des ersten homologisch **unabhängigen** Rückkehrzyklus der Länge 11) wird in [Anhang E](#anhang-satz11) ausgeführt; ergänzende Evidenz im Notebook.

### $n_0$-Bestimmung (dichtebasiert) {#n0dichte}

Wir schreiben
$$
n_0 = n_1+n_2+n_3,\qquad n_1=n_2=1,\qquad n_3\equiv n_{\mathrm{FCC}}:=\operatorname{round}(n_8).
$$ {#eq:n0-def}

\newpage

## Herleitung der Frustrationskorrektur $\Delta_\eta$

**Kompakte Form:** *(mit expliziter Projektion)*
Wir normieren die Frühphasen-Dichten gegen $\eta_{\mathrm{ref}}=\eta_{\mathrm{FCC}}$; die **projektive Zählung** erfolgt über den **Orientierungsprojektor $2^{k}$** (hier $k=3$):

$$
\Delta_\eta
= \dfrac{
\left(\dfrac{\eta_1}{\eta_{\mathrm{FCC}}}\right)
\left(\dfrac{\eta_2}{\eta_{\mathrm{FCC}}}\right)
\left(2^k\right)
}{
n_1+n_2+n_{\mathrm{FCC}}
},\quad
k=3,\qquad
n_0=n_1+n_2+n_{\mathrm{FCC}}.
$$ {#eq:Delta-eta}

**Entfaltet:**

$$
\Delta_\eta =
\left(
\frac{
  \left( \tfrac{1}{2} - \tfrac{1}{2 \cdot 3 \cdot 5 \cdot 11} \right)
}{
  \left( \tfrac{\pi}{3 \cdot \sqrt{2}} \right)
}
\cdot
\frac{
  \left( \tfrac{\pi \cdot \sqrt{3}}{8} \right)
}{
  \left( \tfrac{\pi}{3 \cdot \sqrt{2}} \right)
}
\right)
\cdot 2^3 \cdot
\left( \frac{1}{1 + 1 + n_3} \right).
$$ {#eq:Delta-eta-entfaltet}

**Kurzform (Spezialfall $k=3$):**

$$
\boxed{\ \Delta_\eta = \Bigl(1-\tfrac{1}{3\cdot 5\cdot 11}\Bigr)\,\frac{9\,\sqrt{3}}{\pi\cdot n_0}\ }
$$ {#eq:Delta-eta-kurz}

> **Notationseindeutigkeit:** $\Delta_\eta$ ist linear in $1/n_0$ und $1/\pi$; der Faktor $9$ resultiert rein aus den Dichteverhältnissen (inkl. $2^{3}$).

## Exakter Wert der Feinstrukturkonstante

Mit $n_0 = 1 + 1 + n_3$ (mit $n_3=135$ aus dem $\rho$-Modell) und $k=3$:

$$
\Delta_\eta = 0.035\,999\,179\,369
\qquad\Rightarrow\qquad
\boxed{\alpha^{-1}_{\mathrm{Theo}}(0)= 137.035\,999\,179}
$$ {#eq:alpha-theo}

**und daraus**

$$
\boxed{\alpha_{\mathrm{Theo}}(0)= 0.007\,297\,352\,564\,205\,256}
$$ {#eq:alpha-theo-alpha}

> **Hinweis (Notebook-Kernzahlen, automatisch generiert):**  
> $\alpha^{-1}$ (16 signifikante Stellen): 137.0359991793693 $\Rightarrow$ $\alpha$: 0.007297352564205256…

\newpage
# Validierung  {#validierung}

- **Synthetik:** A$_2$-Torus (isotrop) → $\min$ nichtlokal = 11 (*mod* 3/5); Patches → nur 3er. Siehe [Anhang C](#anhang-11).
- **Konsequenz:** **keine** nachträglichen Parameteranpassungen; „11“ nicht austauschbar.
- **Formelraum (Hinweis):** Die systematische Prüfung des Formelraums wird separat dokumentiert; diese Fassung konzentriert sich auf Herleitung und Kernzahlen.

## Querverifikation ($\rho$-Modell, blind)

**Pfad (ohne Zugriff auf $\alpha$):** siehe [Gleichung @eq:n8-anhang]; daraus
$n_3=\operatorname{round}(n_8) \Rightarrow n_0=1+1+n_3 \Rightarrow \alpha^{-1}(0)=n_0+\Delta_\eta$.

**Eigenschaften:** deterministisch; keine Fit-Parameter; blinder Pfad. **Notebook:** `notebooks/Alpha.ipynb` (Abschnitt $\rho$-Modell).

Aus den gefreezten Dichten (**Planck 2018**) ergibt sich $n_8 = 135.0001 \pm 0.0071$, gerundet $n_3 = 135$. Rundungsschwellen: $134.5 / 135.5$. **Robustheit:** Distanz zur unteren Rundungsschwelle: $0.5001$ bei $\sigma_{n_8}=0.0071$ → **$70.1\,\sigma$**; die Rundung $n_3=135$ ist damit **extrem stabil**.

### Sensitivität (Projektor-Exponent) {#rho-sensi}

Setzt man **$k=2$** (statt 3), ergibt sich $\alpha^{-1}(0)\approx 137.0179996$; bei **$k=4$** erhält man $\alpha^{-1}(0)\approx 137.0719984$. Beide Werte liegen **weit** neben den Präzisionsdaten. Daher ist **$k=3$** (und damit $2^3$) **entscheidend**.

## Vergleich mit Experiment *(Modellwert: [@eq:alpha-theo-alpha])* {#vergleich}

| Quelle         | $\alpha_0$ | $\sigma_{\alpha_0}$ | relative Abw. $\Delta\alpha_0/\alpha_0$ |
|:---------------|--------:|:-----:|:---------:|
| [@codata2022] | 0.0072973525643(11) | $1.1\times10^{-12}$ | $\approx -1.30\times10^{-9}\,\%$ |
| [@pdg2024] aus $\alpha_0^{-1}=137.035999178(8)$ | 0.007297352564278 | $4.26\times10^{-13}$ | $\approx -9.99\times10^{-10}\,\%$ |

### Abweichung [$\alpha_{\mathrm{Theo}}(0)$](#eq:alpha-theo) relativ zur Messgenauigkeit der 1-$\sigma$-Bandbreite {#zalpha}

| Quelle                                     |       **z($\alpha_0$)** | **Anteil der 1-$\sigma$-Bandbreite [%]** |
|--------------------------------------------|----------------:|-----------------:|
| [@codata2022]                              |       **0.086 σ**     | **8.61 %** |
| [@pdg2024]                                 |       **0.171 σ**     | **17.1 %** |

\newpage
## Datenverfügbarkeit / Reproduzierbarkeit & Code (Notebook) {#reproduzierbarkeit}

Alle Daten, Quellcode und Notebooks sind im GitHub-Repository [*alpha0*](https://github.com/geronimo66/alpha0) frei zugänglich und auf Zenodo archiviert. Details zur Reproduzierbarkeit, Software-Umgebung und Zitierrichtlinien siehe [README.md](https://github.com/geronimo66/alpha0/blob/main/README.md).  

* **Repository:** <https://github.com/geronimo66/alpha0>
* **Lizenz:** CC BY 4.0  

**Hinweis.** Der vollständige Rechengang, Referenzen und die numerische Einordnung gegenüber den aktuellen Standards (**CODATA 2022**, **PDG 2024**, **Planck 2018**) sind im begleitenden Notebook dokumentiert; alle in diesem Papier aufgeführten Zahlenwerte und Gleichungen werden dort automatisch erzeugt.

## Integritätsnachweise {#integritaetsnachweise}

**Ziel:** Transparente Absicherung gegen A-posteriori-Fits (Feynman-Check) und reproduzierbare Builds.

> **Hinweis (Integrität & Reproduzierbarkeit):** 
> Reproduzierbarkeit und Freeze-Schritte (Axiome/Konstanten, Build-Protokoll) sind **geplant** und werden – soweit sinnvoll – **nachgereicht**. Diese Fassung fokussiert auf die topologische Herleitung und Kernzahlen; operative Details werden **gegebenenfalls** in Begleitunterlagen dokumentiert.

## Effektive Lorentzinvarianz (Plausibilitätsgrenzen)

* **Randbedingung statt Dynamik.** $\Delta_\eta$ verschiebt nur $\alpha^{-1}(0)(Q^2\!\to\!0)$; die **Running** bleibt QED-standard.
* **Kohärente Propagation.** Für $\lambda\gg \ell_P$ mitteln Mikrodiskretheiten aus; **keine** zusätzliche Dispersion.
* **Isotropie.** **Orientierungsprojektor $2^{k}$ (hier $k=3$)** als diskrete Trennung; **keine** Raumrichtung.
* **EFT-Einordnung.** Siehe [Anhang G](#anhang-eft-thomson) (Thomson-Matching, Ward-Identitäten, Schema-Invarianz).
* **Gauge-Invarianz.** Unabhängigkeit vom $R_\xi$-Gaugeparameter; formal
$$
\frac{\partial \alpha^{-1}(0)}{\partial \xi}=0
$$ {#eq:gauge-indep}
(Nachweis in [Anhang G](#anhang-eft-thomson)).

> **Hinweis**
> Isotrope Orientierungsmittelung entspricht formal dem Haar-Mittel $\int_{\mathrm{SO}(3)} R A R^{\top}\,dR=\tfrac{\Tr(A)}{3}I$ und liefert so eine isotrope makroskopische Antwort.

\newpage
## Robustheitssatz (Diophantische Einzigkeit & Stabilität von $n_0=1+1+n_3$)

**Axiome (A–D):**  
A$_2$/Isotropie; lokale 3/5-Zyklen; erster nichtlokaler Generator = 11; **Orientierungsprojektor $k=3$**.

**Kompaktformel:**

$$
K=\Bigl(1-\tfrac{1}{165}\Bigr)\tfrac{9\sqrt{3}}{\pi},\qquad
\alpha^{-1}(0)=n_0+\dfrac{K}{n_0}\quad (\text{fitfrei}).
$$ {#eq:kompakt-k}

**Monotonie:**

$$
f(n+1)-f(n)=1-\dfrac{K}{n(n+1)}\!>\!0.9995,\qquad n\ge 100.
$$ {#eq:monotonie}

**Folgerung:**  
Im ppm-Messfenster ist **nur $n_0=137$** möglich; Dichte-Cross-Check impliziert **$n_8\approx135$**.

## Stochastische Formelraumsuche – Ausblick {#formelraum}

Die systematische Prüfung des Formelraums wird separat dokumentiert; diese Fassung konzentriert sich auf Herleitung und Kernzahlen. Ergebnisse und Methodik werden im Supplement/Repo nachvollziehbar bereitgestellt.

## Permutationstest – Ausblick {#permutation}

Permutationstests (Prime-Swaps, Grammar-Shuffles) werden separat dokumentiert; diese Fassung berichtet bewusst keine Testergebnisse. Veröffentlichte Resultate werden im Repository/Supplement referenziert.

\newpage
# Diskussion

## Kernbefund und Geltungsbereich
Die Arbeit liefert eine **fitfreie, analytisch definierte Randbedingung** für die inverse Feinstrukturkonstante im **Thomson-Limit**. Die QED-Running bleibt unverändert (Ward-Identitäten, schemainvariantes Matching); die Aussage betrifft explizit $Q^2\!\to\!0$ [@peskin1995].
Der Modellwert ist ppm-konsistent mit **CODATA 2022** und **PDG 2024** und **Planck-kompatibel** im Dichteabgleich [@codata2022; @pdg2024; @planck2018].

## Struktur der Herleitung: Trennung von Geometrie und Projektion {#diskussion-struktur}
Zentral ist die **strikte Trennung** zwischen  
1. **Geometrisch:** Packungsdichten, u. a. $\eta_2=\pi\sqrt{3}/8$ (BCC) und $\eta_{\mathrm{FCC}}=\pi/(3\sqrt{2})$ (FCC-Referenz; Basispositionen z. B. in [@purdueChem]).  
2. **Projektiv:** ein **rein projektives** Orientierungs-Zählmass $2^{k}$ mit **$k=3$** (D$_6$-isotrope Achsenklassen).

Die Frustrationskorrektur besitzt die **Kompaktform**
$$
\Delta_\eta=\Bigl(1-\tfrac{1}{3\cdot5\cdot11}\Bigr)\,\frac{9\,\sqrt{3}}{\pi\,n_0},\quad
n_0=1+1+n_3,
$$ {#eq:Delta-kompakt}
wobei die BCC-„8“ **rein geometrisch** ist und **nicht** zum Projektorfaktor zählt.  
Diese Trennung **minimiert die Gefahr versteckter Freiheitsgrade** und macht den Ansatz **innerhalb der gewählten Axiome** präzise falsifizierbar.

**Satz (Projektor – Kurzfassung).** Unter D$_6$-Isotropie und $v\sim -v$ verbleiben **drei** ungerichtete Achsenklassen. Jede D$_6$-invariante Projektivierung, die Orientierungs-Doppelzählungen entfernt, erzwingt **$k=3$** und damit **$2^k=8$**; dieser Projektorfaktor ist **unabhängig** vom geometrischen Nenner $8$ in $\eta_2=\pi\sqrt{3}/8$. (Begründung: [Anhang B](#anhang-projektor), [Anhang F](#anhang-projektor-zaehlmass).)

> **Hinweis (Analogie-Quellen).** 
> PSG/Projektionsliteratur [@sonnenschein2020] sowie die klassischen QCD-$\beta$-Funktionsarbeiten [@gross1973; @politzer1973; @caswell1974; @jones1974] dienen **nur** als Motivation/Kontext, **nicht** als Beweis. Die Herleitung von $2^{k}$ (hier $k=3$) erfolgt **eigenständig** aus D$_6$-Isotropie; die Kompaktform von $\Delta_\eta$ basiert **ausschliesslich** auf analytischen Packungsdichten und der separaten projektiven Zählung (vgl. [Anhang B](#anhang-projektor)).

\newpage
## Grafik: Pipeline der Herleitung {#fig-pipeline}
Abb. @fig:pipeline zeigt den Rechengang (Topologie → Geometrie → Projektion → Normalisierung); Details: **B/C/D/G**.

\begin{figure}[H]
\centering
\begin{tikzpicture}[font=\small, >=Latex, node distance=18mm]

\node[draw, rounded corners, align=center, text width=6cm] (S1) {
\textbf{1. Split — Topologie}\\[0.4ex]
$\displaystyle \left(\tfrac{\eta_1}{\eta_{\mathrm{ref}}}\right),\quad
\eta_1=\tfrac{1}{2}\Bigl(1-\tfrac{1}{165}\Bigr)$\\
$\eta_{\mathrm{ref}}=\tfrac{\pi}{3\sqrt{2}}$
};

\node[draw, rounded corners, align=center, text width=6cm, below=of S1] (S2) {
\textbf{2. Split — Geometrie (BCC)}\\[0.4ex]
$\displaystyle \left(\tfrac{\eta_2}{\eta_{\mathrm{ref}}}\right),\quad
\eta_2=\tfrac{\pi\sqrt{3}}{8}$\\
$8$ in $\eta_2$ ist geometrisch (BCC-Nenner)
};

\node[draw, rounded corners, align=center, text width=6cm, below=of S2] (S3) {
\textbf{Orientierungsprojektor (D$_6$)}\\[0.4ex]
$\displaystyle \times\,2^{k},\quad k=3\Rightarrow 2^3=8$
};

\node[draw, rounded corners, align=center, text width=6cm, below=of S3] (S4) {
\textbf{$n_3$ Splits — Normalisierung}\\[0.4ex]
$\displaystyle \times\,\tfrac{1}{n_0},\quad n_0=1+1+n_3$
};

\node[draw, rounded corners, align=center, text width=7cm, below=of S4] (Res) {
\textbf{Ergebnis}\\[0.4ex]
$\displaystyle
\Delta_\eta=\left(\frac{\eta_1}{\eta_{\mathrm{ref}}}\right)
\left(\frac{\eta_2}{\eta_{\mathrm{ref}}}\right)
\frac{2^3}{n_0}
=\Bigl(1-\frac{1}{165}\Bigr)\frac{9\sqrt{3}}{\pi n_0}$\\[0.6ex]
$\displaystyle \alpha^{-1}(0)=n_0+\Delta_\eta$
};

\draw[->, thick] (S1) -- (S2);
\draw[->, thick] (S2) -- (S3);
\draw[->, thick] (S3) -- (S4);
\draw[->, thick] (S4) -- (Res);

\end{tikzpicture}
\caption{Pipeline der fitfreien Herleitung: Topologie ($\eta_1$) → Geometrie (BCC, $\eta_2$) → Projektor ($2^3$) → Normalisierung ($1/n_0$).}
\label{fig:pipeline}
\end{figure}

## Topologie der Frühphase: die Rolle der „11“
Die „11“ tritt als **erste nichtlokale Rückkehrlänge** in der homologischen Struktur eines isotropen A$_2$-Torus auf (Quotient *mod* lokale 3/5-Zyklen). Formal liefert [Anhang C](#anhang-11) bzw. [Anhang E](#anhang-satz11) die Minimalitätsaussage und die kohomologische Trennung; **Zertifikat:** siehe [Anhang C](#anhang-11).

## Sensitivität und Robustheit
- **Projektor-Exponent:** $k=2$ oder $k=4$ verfehlen die Präzisionsdaten deutlich; **$k=3$** ist notwendig.  
- **Minimalzyklus „11“:** Ersetzungen (7/13/17 …) verschieben $\alpha^{-1}$ um $\mathcal{O}(10^{-4})$ und zerstören ppm-Konsistenz.  
- **Robustheitssatz (Kompaktform):** $f(n)=n+K/n$ ist im ppm-Fenster **nur** mit $n_0=137$ konsistent; die Dichte-Spur liefert $n_8\approx135$.

## Axiome (A–D) – Kurzliste {#axiome}
A: A$_2$-Isotropie; projektive Trennung $2^{k}$ mit $k=3$.  
B: Lokale 3/5-Zyklen; erster **nichtlokaler** Generator = 11 (ab $L\ge 11$). Siehe [Anhang C](#anhang-11).  
C: **Strikte Trennung** Geometrie (Dichten) vs. Projektion ($2^{k}$).  
D: $n_0=1+1+n_3$ (dichtebasiert); $\Delta_\eta=K/n_0$, $K=\bigl(1-\tfrac{1}{165}\bigr)\tfrac{9\sqrt{3}}{\pi}$.

## Falsifizierbarkeit (Kurzfassung; Volltext im Anhang)
1) **$k$-Test** ($k\ne3$) ⇒ ppm-Konsistenz bricht. (→ [Anhang F](#anhang-projektor-zaehlmass))  
2) **„11“-Minimalität** ⇒ kürzere nichtlokale Länge widerlegt. (→ [Anhang E](#anhang-satz11); [Anhang C](#anhang-11))  
3) **Thomson-Grenze** ⇒ Schema-/Gauge-Abhängigkeit widerlegt. (→ [Anhang G](#anhang-eft-thomson))  
4) **$\rho$-Cross-Check** ⇒ $n_8\not\approx135$ widerlegt. (→ [Anhang D](#anhang-rho-modell))

## Reproduzierbarkeit
Quellcode/Notebooks (inkl. Rechenpfad, Zahlen, Tabellen) im Repo/Zenodo; Build/Freeze/Artefakte siehe **J/K**. Messstandards: **CODATA 2022**, **PDG 2024** [@codata2022; @pdg2024].

## Ausblick
(i) Kohärenz-/Dekohärenz-Regime, (ii) weitere Topologie-Settings zur „11“, (iii) EFT jenseits $q^2\!=\!0$, (iv) auditierbare Formelraumsuche. Verweise: **[C](#anhang-11)/[E](#anhang-satz11)/[G](#anhang-eft-thomson)**.

## Hypothese (abgeleitet aus den Verhältniszahlen) 
Die im Verhältnisabdruck $E_{\mathrm{ph}}/E_{\mathrm{mag}}\approx0.9879$ sichtbar werdende Asymmetrie könnte darauf hindeuten, dass das Magnetfeld als **lokal gebundene Struktur** einer Packungsgeometrie folgt, während das elektrische Feld eine eher **holographisch-phasenartige Struktur** aufweist.  

Ergänzend lässt sich vermuten, dass oberhalb der Planckdichte das Universum nur im **Phasenraum** und ausschliesslich **kohärent** war, während erst mit der 3. Teilung als stabile kohärente Raumstrukturen bestehen konnten (FCC). Die ineffizienten ersten beiden Teilungen wären dann als Übergangsphasen interpretierbar.  

**Zusatzannahme:** Alle heute als isotrop und invariant gemessenen Grössen und Verhältniszahlen könnten aus dieser kohärenten Frühzeit stammen. Kleine **Anisotropien und Frustrationen** (wie $\Delta_\eta$) wären dann die direkten Spuren der ersten instabilen Dekohärenzprozesse.  

**Offene Perspektive:** Diese Deutung ist **eine mögliche Hypothese**; die Verhältniszahl selbst lädt dazu ein, **weitere alternative Erklärungen** zu untersuchen. Ob die Asymmetrie fundamental mit Packungs- oder Phasenstrukturen verknüpft ist, oder auf andere Mechanismen zurückgeht, bleibt eine offene Forschungsfrage.

# Anhang

## Anhang A – Notation & Symbole (erweitert)  {#anhang-notation}

> **Notation & Symbole (erweitert)**
> - **A$_2$-Gitter:** $\Lambda_{\mathrm{A2}}=\{x e_1+y e_2:x,y\in\mathbb{Z}\}$:
>   - Kantenrichtungen $\{\pm e_1,\pm e_2,\pm(e_1-e_2)\}$;  
>   - orientierter Kantenkomplex $\Gamma=(V,E)$.  
> - **Zyklenräume:** $C_1(\Gamma;\mathbb{Z})$, $Z_1=\ker\partial$; **orientierte** Kanten, Länge $\ell(C)$.  
> - **Lokaler Unterraum:** $L_{3,5}=\langle\partial \triangle,\partial P_5\rangle\subseteq Z_1$.  
> - **Quotient:** $Q=Z_1/L_{3,5}$ (nichtlokale Klassen mod 3/5).  
> - **Torus:** $T_{W,H}$; isotrop: $W=H=L$.  
> - **Projektor (Verweis):** D$_6$-Isotropie; wir verwenden $2^{k}$ mit $k=3$. **Definition & Herleitung siehe [Anhang B](#anhang-projektor).**  
> - **Weiterführend:** Grundlagen zu Gittern und Kugelpackungen: [@conway1999].  
> - *Konvention* Wir setzen $\alpha_0\equiv \alpha(0)$ für das Thomson-Limit.  

### A.1 — Parameter & Herkunft {#parameter-herkunft}
| Grösse | Wert(e) | Kategorie | Herkunft/Begründung |
|---|---:|---------|-------------------------|
| $n_0$ | $1+1+n_3$ | dichtebasiert | $n_1+n_2+\mathbf{n_3}$; **$\mathbf{n_3\equiv n_{\mathrm{FCC}}=\operatorname{round}(n_8)}$** |
| $n_1$ | $1$ | empirisch | erste Teilung |
| $n_2$ | $1$ | empirisch | zweite Teilung |
| $n_{\mathrm{FCC}}$ | $135$ | dichtebasiert | aus $\rho$-Modell |
| $2^{k}$ | $2^3=8$ | projektiv | Orientierungsprojektor (D$_6$: $k=3$) |
| $\eta_1$ | $\tfrac{1}{2}-\tfrac{1}{2\cdot3\cdot5\cdot11}$ | geom.-topolog. | bipartite Grundzerlegung; lokale/nichtlokale Zyklen |
| $\eta_2$ | $\pi\sqrt{3}/8$ | geometrisch | BCC-Dichte |
| $\eta_{\mathrm{FCC}}$ | $\pi/(3\sqrt{2})$ | geometrisch | FCC (Referenz) |
| $\{3,5\}$ | – | lokal/topolog. | lokale Zyklen am Tetraederrand |
| $11$ | – | topolog. | erste **nichtlokale** Rückkehrlänge (*mod* 3/5) |
| $2$ | – | topolog. | bipartite Grundzerlegung (Basisterm $1/2$) |
  
### A.2 — Notationskasten {#notation}
| Term | |
|:-------|:----------------|
| $n_0 = 1 + 1 + n_3$ | integernaher Anteil der Randbedingung |
| $n_3 = \operatorname{round}(n_8)$ | blind aus dem $\rho$-Pfad |
| $n_8$ | log-basierte Tiefenzahl |
| $\eta_1 = \tfrac12 - \tfrac{1}{330}$ | Tetra-Dichte (mit „11“) |
| $\eta_2 = \tfrac{\pi\sqrt{3}}{8}$ | BCC-Dichte (geometrisch; „8“ nicht Projektor) |
| $\eta_{\mathrm{FCC}} = \tfrac{\pi}{3\sqrt{2}}$ | FCC-Referenz |
| $\eta_{\mathrm{eff}} = \tfrac12\,\eta_{\mathrm{FCC}}^{4/3}+\tfrac12\,\eta_{\mathrm{FCC}}^{2}$ | Effektive Dichte (Begründung in Anhang G) |
| $2^{k}$, $k=3$ | projektiver Faktor (D$_6$-Isotropie) |
| $\Delta_\eta = \bigl(1-\tfrac{1}{3\cdot5\cdot11}\bigr)\tfrac{9\sqrt{3}}{\pi n_0}$ | Frustrationskorrektur |
| $\alpha^{-1}(0) = n_0 + \Delta_\eta$ | Randbedingung im Thomson-Limit |

## B — Orientierungsprojektor: Definition, Herleitung & Eindeutigkeit {#anhang-projektor}

### B.0 — Definitionskasten (separate Zählung) {#anhang-projektor-def}
**Definition A1.** Sei $\mathcal{C}$ die Menge mikroskopischer Belegungen pro Zelle. Der **Orientierungsprojektor** identifiziert Konfigurationen, die sich nur durch die Wahl einer der $k$ globalen Orientierungsachsen und deren Richtungsumkehr unterscheiden. Pro Achse existieren zwei Richtungen; die **Zählmultiplikität ist $2^{k}$**.  
**Annahme A1 (hier verwendet).** D$_6$-Isotropie impliziert **$k=3$** äquivalente Achsenklassen $\Rightarrow 2^k=2^3=8$. **Dieser $2^3$-Faktor ist projektiv** und **unabhängig** vom geometrischen $8$ in $\eta_2=\pi\sqrt{3}/8$.

### B.1 — Herleitung von $k=3$; $2^k=8$
Die gerichteten Kantenrichtungen des A$_2$-Gitters sind $\{\pm e_1,\pm e_2,\pm(e_1-e_2)\}$.  
Nach Identifikation $v\sim -v$ verbleiben **drei** ungerichtete Achsenklassen $\{[e_1],[e_2],[e_1-e_2]\}$ ⇒ **$k=3$**.  
Pro Achse zwei Richtungen ⇒ Zählmultiplikität **$2^k=8$**.

### B.2 — D$_6$-invariante Projektivierungen (Eindeutigkeit)
Jede D$_6$-invariante Projektivierung, die (i) Orientierungspaarungen $v\sim -v$ vollzieht und (ii) Achsenklassen **nicht** vermischt, induziert genau **$k=3$** Achsenklassen und damit den projektiven Faktor $2^k=8$. **Eindeutigkeit:** Unter den Arbeitsannahmen A–D ist $k=3$ **erzwungen**.

**Counting-Mass.**
$$
\mu_{k}(A)=\frac{1}{2^{k}}\#\,q^{-1}(A),\qquad k=\text{\# Achsenklassen (A$_2$: }k=3).
$$ {#eq:mu-k}

### B.3 — Drei verschiedene „8“ {#anhang-acht}
1. **Geometrische 8** – Nenner in $\eta_2=\pi\sqrt{3}/8$ (Packungsgeometrie).  
2. **Projektor-8** – Orientierungszählung $2^{k}$ mit $k=3\Rightarrow 8$ (projektiv).  
3. **Oktale 8** – Basis der Tiefenzahl $n_8$ im $\rho$-Modell ($8^{n_8}$, $\ln 8$).  
Alle drei sind **getrennt** (Geometrie, Projektion, Arithmetik).

## C — Nichtlokaler Minimalzyklus „11“ — Beweis & Zertifikate {#anhang-11}

### C.1 — Rahmen & Definitionen
*(Notation siehe Anhang A)*. Isotropieannahme; Koeffizientenring $\mathbb{Z}$; **orientierte** Kanten; Zyklenlänge $\ell(C)$ zählt Kanten mit Multiplizität.  

**Nichtlokal (Hinweis).** $\bar C\neq 0$ in $Q=Z_1/L_{3,5}$; präzise Definition und die Minimallänge siehe [Anhang E](#anhang-satz11), [Gleichung @eq:lmin].

### C.2 — Reduktion & Terminierung (Lemma)
(a) Dreiecksabzug $C\mapsto C\oplus\partial\triangle$ senkt $\ell$ um 3.  
(b) Fünfecksausgleich $C\mapsto C\oplus\partial P_5$ senkt $\ell$ um 5.  
(c) Die Massfunktion $\Phi(C)=(\ell(C),n_5(C))$ fällt strikt ⇒ Terminierung.

### C.3 — Exhaustion ≤ 10 und explizite Kokette
**Lemma.** Auf $T_{L,L}$ mit $L\ge 11$ ist jeder geschlossene $1$-Zyklus mit $\ell\le 10$ lokal.  
**Kokette $\varphi$** mit
$$
\varphi(v\!\to\!w):=\text{Koeffizient von }e_1\text{ in }(w-v)\in\{-1,0,+1\}
$$ {#eq:phi}
erfüllt $\langle\varphi,\partial\triangle\rangle=0$ sowie $\langle\varphi,\partial P_5\rangle=0$; damit annihiliert $\varphi$ $L_{3,5}$ und liefert $\langle\varphi,G_x\rangle=L$.

### C.4 — Satz & Beweis (Minimalität & Unabhängigkeit)
$$
\ell_{\min}^{\mathrm{nonloc}}=\begin{cases}
L,& L\ge 11,\\
\text{nicht definiert},& L\le 10,
\end{cases}
$$ {#eq:lmin-case}
Insbesondere besitzt $T_{11,11}$ nichtlokale Klassen der Minimallänge 11.

### C.5 — Zertifikate & synthetische Validierung {#anhang-11-cert}
Für $W,H\le 10$: $Z_1/L_{3,5}$ trivial; bei $(11,11)$: Dimension 2, kürzester Repräsentant Länge 11.  
**Zertifikat:** siehe Datei `anc/certificate_alpha11.csv`.

> **Hinweis (Begriffsabgleich BFS ↔ Homologie):** 
> Das BFS-Zertifikat belegt die **erste nichtlokale Rückkehrlänge** in der Zustandsgraph-Exhaustion. Die formale **Nichtlokalität** meint $\bar C\neq 0$ im Quotienten $Q=Z_1/L_{3,5}$; die Reduktion *mod* $L_{3,5}$ wird in **Lemma E.1–E.3** geführt (siehe [Anhang E](#anhang-satz11)).  

### C.6 — Primzahlen im Modell — Struktur & Falsifizierbarkeit {#primzahlen}
| Primzahl | Rolle | Status | Alternative |
|---|---------|---|-----------|
| 2 | bipartite Grundzerlegung (Basisterm $1/2$) | fix | – |
| 3,5 | lokale Zyklen | fix | Austausch widerspricht Topologie |
| 11 | erste nichtlokale Rückkehrlänge | fix (Minimalität) | 7/9/13/17 ⇒ $\mathcal{O}(10^{-4})$ in $\alpha^{-1}$ |

## D — Ergänzende Validierung aus dem $\rho$-Modell {#anhang-rho-modell}
**Deterministischer Pfad.**
$$
\eta_{\mathrm{eff}}=\tfrac12\,\eta_{\mathrm{FCC}}^{4/3}+\tfrac12\,\eta_{\mathrm{FCC}}^{2},\qquad
\frac{\rho_P}{\rho_{\mathrm{ref}}\,\eta_{\mathrm{eff}}}=12\cdot 8^{\,n_8}.
$$ {#eq:eta-eff-em}
$$
n_8=\frac{\ln\!\big(\rho_P/(\rho_{\mathrm{ref}}\eta_{\mathrm{eff}})\big)-\ln 12}{\ln 8},\qquad
n_3:=\operatorname{round}(n_8),\qquad
n_0=1+1+n_3.
$$ {#eq:n8-anhang}

**Fehlerbudget.**
$$
(\Delta n_8)^2\approx\frac{1}{(\ln 8)^2}\left[
  \left(\frac{\Delta\rho_P}{\rho_P}\right)^2+
  \left(\frac{\Delta\rho_{\mathrm{ref}}}{\rho_{\mathrm{ref}}}\right)^2+
  \left(\frac{\Delta\eta_{\mathrm{eff}}}{\eta_{\mathrm{eff}}}\right)^2
\right].
$$ {#eq:rho-fehlerbudget}

## E — Satz „11“ — Minimalität & Unabhängigkeit {#anhang-satz11}

> **Hinweis:** 
> Die knappe, referenzierte Darstellung zur „11“ wird in [**C — Minimaler nichtlokaler Zyklus (Zertifikat)**](#anhang-11) als *kanonische* Stelle geführt.  

**Voraussetzungen.**  
*(Notation siehe [Anhang A](#anhang-notation): A$_2$-Gitter, $Z_1$, lokaler Unterraum $L_{3,5}=\langle\partial\triangle,\partial P_5\rangle$, Quotient $Q=Z_1/L_{3,5}$, Torus $T_{W,H}$; isotrop: $W=H=L$.)*  
Isotropieannahme; Koeffizientenring $\mathbb{Z}$; **orientierte** Kanten; Zyklenlänge $\ell(C)$ zählt Kanten mit Multiplizität.  

**Definition.** Ein Zyklus $C \in Z_1$ heisst **lokal**, wenn $\bar C = 0$ in $Q = Z_1/L_{3,5}$; andernfalls **nichtlokal**.  
Die **nichtlokale Minimallänge** ist
$$
\ell_{\min}^{\mathrm{nonloc}} := \min\{\ell(C) : \bar C \neq 0\}.
$$ {#eq:lmin}

**Lemma E.1 (Reduktion & Terminierung).**

- (a) *Dreiecksabzug:* Enthält $C$ ein elementares Dreieck $\triangle$, so ist $C\sim C\oplus\partial\triangle$ und $\ell$ sinkt um 3.
- (b) *Fünfecksausgleich:* Enthält $C$ ein eingebettetes 5-Gon $P_5$, so ist $C\sim C\oplus\partial P_5$ und $\ell$ sinkt um 5.
- (c) *Terminierung:* Die lexikographische Massfunktion $\Phi(C)=(\ell(C),n_5(C))$ fällt unter (a)/(b) strikt; der Prozess terminiert.

**Lemma E.2 (Exhaustion ≤ 10 auf $T_{L,L}$; vollständiger Beweis).**  
*Sei $T_{L,L}$ mit $L\ge 11$. Jeder geschlossene $1$-Zyklus $C$ mit $\ell(C)\le 10$ ist lokal, d. h. $C\in L_{3,5}$ und $\bar C=0$ in $Q$.*

**Beweis.**  
- (1) *Überlagerung:* Hebe $C$ via $\pi:\mathbb{R}^2\to T_{L,L}$ zu $\widetilde C$ an. Die Nettoverschiebung ist $k_1(Le_1)+k_2(Le_2)$, $k_i\in\mathbb{Z}$. Da pro Schritt die $e_{1/2}$-Koordinate höchstens um 1 ändert, gilt $|k_i|L\le \ell(C)\le 10$. Mit $L\ge 11$ folgt $k_1=k_2=0$.  
- (2) *Planarität:* $\widetilde C$ ist kontraktibel und begrenzt eine endliche Vereinigung elementarer Dreiecke $U$. Damit $\widetilde C=\bigoplus_{\triangle\subset U}\partial\triangle$; nach Projektion $C\in L_{3,5}$.  
- (3) *Nicht-einfache Zyklen:* Zerlege in einfache; wende (1)–(2) an.  

**Lemma E.3 (Explizite $1$-Kokette $\varphi$; Trennung lokal/nichtlokal).**  
*Es existiert $\varphi\in Z^1(T_{L,L};\mathbb{Z})$ mit (i) $\langle\varphi,\partial\triangle\rangle=0$ **und** $\langle\varphi,\partial P_5\rangle=0$, (ii) $\langle\varphi,G_x\rangle=L$ für den geodätischen Fundamentalzyklus $G_x$ in $e_1$-Richtung.*

**Konstruktion.**  
Für eine orientierte Kante $v\!\to\!w$ setze

$$
\varphi(v\!\to\!w):=\text{Koeffizient von }e_1\text{ in }(w-v)\in\{-1,0,+1\}.
$$ {#eq:phi}

Somit $\varphi(e_1)=+1$, $\varphi(-e_1)=-1$, $\varphi(e_2)=\varphi(-e_2)=0$, $\varphi(e_1-e_2)=+1$, $\varphi(-(e_1-e_2))=-1$.  
Eigenschaften: Auf jedem Dreieck summiert $1+0-1=0$ und auf $\partial P_5$ ist die Nettosumme ebenfalls $0$ (kontraktibel) ⇒ (i); entlang $G_x$ addieren sich $L$ Stücke mit $+1$ ⇒ (ii).  
Also annihiliert $\varphi$ $L_{3,5}$ und definiert $\bar\varphi:Q\to\mathbb{Z}$ mit $|\langle\bar\varphi,\bar C\rangle|\le \ell(C)$.

**Satz E.1 (Minimalität & Unabhängigkeit).**

$$
\ell_{\min}^{\mathrm{nonloc}}=\begin{cases}
L,& L\ge 11,\\
\text{nicht definiert},& L\le 10,
\end{cases}
$$ {#eq:lmin-case}

insbesondere besitzt $T_{11,11}$ nichtlokale Klassen der Minimallänge 11; jede nichtlokale Klasse hat einen Repräsentanten mit $\ell\ge L$.

**Beweis.**  
Existenz durch $G_x$ (Lemma E.3(ii)); Minimalität durch Lemma E.2 und die Schranke aus Lemma E.3.  
Unabhängigkeit folgt aus D$_6$-Isotropie und kohomologischer Trennung.

### E.1 — Begründungsskizze ($\eta_1$) und Arbeitsannahmen {#zkizze}

**Ziel.**

$$
\eta_1=\frac12-\frac{1}{2\cdot3\cdot5\cdot11}.
$$ {#eq:eta1}

**Sensitivität (Rückkehrzyklus).** Ersetzt man **testweise** $11\to 7$, verschiebt sich $\alpha^{-1}(0)$ um $\Delta\alpha^{-1}(0)\approx -1.25\times 10^{-4}$, entsprechend **$\sim 1.6\times 10^{4}\,\sigma$** [@pdg2024]. Die Zykluslänge **11** ist innerhalb der Konstruktion **nicht austauschbar**; Varianten führen zu signifikanten Abweichungen.

**Rahmen:** Orientierter Kantenkomplex $\Gamma$ der Tetraederrand-Struktur in der ersten Teilungsschicht. Die **Grundzuteilung** ist **zweifärbbar (A/B)** ⇒ Basisterm $1/2$. Der **Kontaktgraph** selbst kann lokale **3- und 5-Zyklen** besitzen; dies widerspricht der Zweifärbbarkeit der **Belegung** nicht, da sie eine Zählvorschrift ist (nicht eine Aussage über die Zyklusstruktur von $\Gamma$).

* **Lemma 1 (bipartite Grundzerlegung).** Die Grundbesetzung ist zweifärbbar $\Rightarrow$ Basisterm $1/2$.  
* **Lemma 2 (lokale Zyklen).** 3- und 5-Zyklen erzwingen Ausschlussklassen im Kontaktgraphen; im **ersten Ordnungsansatz** faktorisiert ihr Beitrag lokal.  
* **Lemma 3 (erster unabhängiger Rückkehrzyklus).** Der erste homologisch **unabhängige** geschlossene Weg auf $\Gamma/\!\sim$ hat Länge **11**.

> **Tip** *Homologie-Deutung*:  
> Die „11“ als erste nichtlokale Rückkehrlänge erzeugt in $H_1$ einen Generator, zu dem in $H^1$ ein dualer Kofluss existiert. Das cap-/cup-Pairing liefert eine bilineare Erhaltungsrelation: Das Defizit im einen Kanal paart sich mit der Überfüllung im komplementären Kanal zu einer invarianten Summe (Energieerhaltung); der beobachtbare Abdruck ist das Verhältnis $E_{\mathrm{ph}}/E_{\mathrm{mag}}$.

> **Hinweis** *Geltungsbereich*:  
> **Nichtlokaler Minimalzyklus = 11.** Auf dem A$_2$-Torus (isotrop) erscheint der erste nichtkontraktible Generator bei $W=H=11$ (synthetische Validierung).  
> **Randbedingung.** In kohärenter Ausbreitung (Thomson-Limit, effektive Lorentzinvarianz) mitteln sich lokale Schiefstände aus; übrig bleibt die dimensionslose Randbedingung in $1/\alpha$.
> **Zertifikat:** siehe [Anhang C](#anhang-11).

### E.2 — Primzahlen im Modell — Struktur & Falsifizierbarkeit {#primzahlen}

| Primzahl | Herkunft / Rolle                                    | Status im Modell            | Hypothetische Alternative |
|----------|---------------------------|-------------------------|---------------------------|
| **2**    | bipartite Grundzerlegung (Basisterm 1/2)            | strukturell fix             | nicht ersetzbar           |
| **3**    | lokaler Zyklus an Tetra-Rand                        | strukturell fix             | Austausch widerspricht Topologie |
| **5**    | lokaler Zyklus an Tetra-Rand                        | strukturell fix             | Austausch widerspricht Topologie |
| **11**   | erste nichtlokale Rückkehrlänge im isotropen A$_2$-Quotienten (*mod* 3/5) | strukturell fix (Minimalität) | Austausch (7, 9, 13, 17 …) ⇒ verschiebt $\alpha^{-1}(0)$ um $\mathcal{O}(10^{-4})$, zerstört ppm-Konsistenz |

## F — Orientierungsprojektor als D$_6$-invariantes Zählmass (formal) {#anhang-projektor-zaehlmass}

> **Hinweis:** Die zusammengefasste Darstellung zum Projektor wird in [**B — Orientierungsprojektor**](#anhang-projektor) als *kanonische* Stelle geführt.  

**Orbitstruktur (Lemma F.1).**  
Die gerichteten Kantenrichtungen des A$_2$-Gitters sind $\{\pm e_1,\pm e_2,\pm(e_1-e_2)\}$.  
Nach Identifikation $v\sim -v$ verbleiben **drei** ungerichtete Achsenklassen $\{[e_1],[e_2],[e_1-e_2]\}$.  
D$_6$ operiert transitiv auf diesen Klassen.

**D$_6$-invariante Projektivierungen (Lemma F.2).**  
Jede D$_6$-invariante Projektivierung, die (i) Orientierungspaarungen $v\sim -v$ vollzieht und (ii) Achsenklassen **nicht** vermischt, induziert genau **$k=3$** Achsenklassen und damit den projektiven Faktor $2^k=8$.

**Eindeutigkeit (Satz F.1).**  
Unter den Arbeitsannahmen **A–D** ist $k=3$ **erzwungen**.  
Jede alternative D$_6$-invariante Zählvorschrift, die Orientierungsdoppelzählungen entfernt, liefert denselben Projektorfaktor $2^3$.  
Der projektive Faktor ist **unabhängig** vom geometrischen Nenner „8“ in $\eta_2=\pi\sqrt{3}/8$ (Trennung von Geometrie und Projektor).

**Quotient/Counting-Mass.**
$$
\mu_{k}(A)=\frac{1}{2^{k}}\#\,q^{-1}(A),\qquad k=\text{\# Achsenklassen (A$_2$: }k=3).
$$ {#eq:mu-k}

$\mu_k$ ist D$_6$-invariant und **unabhängig** von geometrischen Dichten; die BCC-„8“ bleibt rein geometrisch ⇒ **Trennung** von $2^{k}$ und $\eta$.

## G — EFT-Randbedingung & Thomson-Matching {#anhang-eft-thomson}

### G.1 — Ward/BFM-Identität und Thomson-Matching
QED-Ward-Identitäten $Z_1=Z_2$ ⇒ Ladungserhaltung.  
**Thomson-Matching:**
$$
\Gamma^\mu(p,p)\big|_{q^2=0}=e_R\gamma^\mu,\qquad
\alpha(0)=\frac{e_R^2}{4\pi}.
$$ {#eq:thomson}
**Formfaktor-Zerlegung (Vertex).**
$$
\Gamma^\mu(p',p)=\gamma^\mu F_1(q^2)+\frac{i\sigma^{\mu\nu}q_\nu}{2m}\,F_2(q^2),\qquad
F_1(0)=1.
$$ {#eq:vertex}

### G.2 — BFM-Lagrange­dichte & schemainvariante Randbedingung
$$
\mathcal L_{\mathrm{EFT}}
= -\frac{1}{4g_R^2(\mu)}F_{\mu\nu}F^{\mu\nu}
  -\frac{c_0}{4}\,F_{\mu\nu}F^{\mu\nu}
  +\sum_{d>4}\frac{c_d}{\Lambda^{d-4}}\mathcal O_d.
$$ {#eq:eft-lagrange}
Matching am Nullimpuls liefert
$$
\alpha^{-1}(0)=\alpha^{-1}*{\mathrm{QED}}(0)+\Delta*{\mathrm{geom}},\qquad
\Delta*{\mathrm{geom}}\equiv c_0\cdot\frac{4\pi}{e^2}=\frac{K}{n_0},
$$ {#eq:alpha-Delta-geom}
und
$$
\mu\frac{d}{d\mu}\Delta_{\mathrm{geom}}=0,\qquad
\frac{\partial \alpha^{-1}(0)}{\partial \xi}=0.
$$ {#eq:Delta-geom-invariance}
Damit bleibt die Running unverändert,
$$
\beta_{\mathrm{EFT}}(g)=\beta_{\mathrm{QED}}(g).
$$ {#eq:beta-eq}
mit
$$
\Delta_{\mathrm{geom}}=\dfrac{K}{n_0},\quad
K=\Bigl(1-\tfrac{1}{165}\Bigr)\dfrac{9\sqrt{3}}{\pi},\quad
n_0=1+1+n_3.
$$ {#eq:Delta-geom-final}

### G.3 — Maxwell-Stress ⇒ Thomson-Limit (dreiteilige Ableitung) {#anhang-maxwell-stress}
**Tensor.**
$$
{}^{\*}F^{\mu\nu}:=\tfrac12\,\epsilon^{\mu\nu\rho\sigma}F_{\rho\sigma},\qquad
T^{\mu\nu}=\tfrac12\!\left(F^{\mu\alpha}F^{\nu}{}*{\alpha}+{}^{\*}F^{\mu\alpha}\,{}^{\*}F^{\nu}{}*{\alpha}\right).
$$
*Äquivalente Standardform:* $$T^{\mu\nu}=F^{\mu\alpha}F^{\nu}{}_{\alpha}-\tfrac{1}{4}\eta^{\mu\nu}F_{\alpha\beta}F^{\alpha\beta}.$$
Energiedichte/Spannung:
$$
T^{00}=\tfrac12(E^2+B^2),\qquad
T^{ij}=-E^iE^j-B^iB^j+\tfrac12\Delta^{ij}(E^2+B^2).
$$

**Packungsskala.** $a\propto\eta^{-1/3}$; **Projektion/Arealdichte.** $\rho_{3\mathrm{D}}\propto\eta$, $\rho_{2\mathrm{D}}\propto \eta^{2/3}$.  
**Isotrope Mode-Mittelung.** Für $q^\mu\to0$ gilt
$$
\langle E^2\rangle_{\mathrm{iso}}=\langle B^2\rangle_{\mathrm{iso}}.
$$

### G.4 — Exponenten & Gewichte (Ende der Linearität) {#etaeffexp}
Tangential/Phasenraum koppelt an $\rho_{2\mathrm{D}}\propto\eta^{2/3}$ (quadratisch $\sim\eta^{4/3}$), normal/Magnetfluss volumetrisch an $\rho_{3\mathrm{D}}\propto\eta$ (quadratisch $\sim\eta^{2}$).  
Isotropie ⇒ **1/2-Gewichtung:**
$$
\eta_{\mathrm{eff}}=\tfrac12\,\eta_{\mathrm{FCC}}^{4/3}+\tfrac12\,\eta_{\mathrm{FCC}}^{2}.
$$

### G.5 — E/M-Kopplung → Phasenraum & FCC-Raum {#e-m-koppelung}
(1) **E-Kanal (tangential, isotrop):** $\rho_{2\mathrm{D}}\propto\eta^{2/3}$ ⇒ Beitrag $\propto\eta^{4/3}$.  
(2) **B-Kanal (normal, volumetrisch):** Beitrag $\propto\eta^{2}$.  
Normierung auf $\eta_{\mathrm{FCC}}=\pi/(3\sqrt{2})$ trennt Geometrie und Projektion.

### G.6 — Symmetrische Gegenwirkung (Energieverhältnisse) {#symmetrische-gegenwirkung}
$$
E_{\mathrm{ph}}=\Bigl(\tfrac12-\Delta\Bigr)E_{\mathrm{tot}},\quad
E_{\mathrm{mag}}=\Bigl(\tfrac12+\Delta\Bigr)E_{\mathrm{tot}},\quad
\Delta=\frac{1}{2\cdot3\cdot5\cdot11}=\frac{1}{330}.
$$
$$
\frac{E_{\mathrm{ph}}}{E_{\mathrm{mag}}}
=\frac{1-2\Delta}{1+2\Delta}
\approx 1-4\Delta+\mathcal{O}(\Delta^2)\approx 0.9879.
$$

### G.7 — Normierungsfaktor „12“ im $\rho$-Modell (Definition & Begründung) {#anhang-12}
**Definition.** $12 \equiv z_{\mathrm{FCC}}$ (Koordinationszahl) als fester Vorfaktor in
[Gleichung @eq:eta-eff-em]–[@eq:n8-anhang].  
**Stabilität.** $12\to c$ verschiebt $n_8$ um $\Delta n_8=\log_8(c/12)$; $n_3=\operatorname{round}(n_8)$ bleibt robust in realistischen Variationen.

## H — Background-Field-Herleitung (stärkere Ableitung) {#anhang-h}

> **Hinweis:** Die zusammengefasste EFT-Darstellung inkl. Thomson-Matching wird in [**G — EFT-Randbedingung (Thomson-Limit)**](#anhang-eft-thomson) als *kanonische* Stelle geführt.  

**EFT-Ansatz (BFM).**

$$
\mathcal L_{\mathrm{EFT}}
= -\frac{1}{4g_R^2(\mu)}F_{\mu\nu}F^{\mu\nu}
  -\frac{c_0}{4}\,F_{\mu\nu}F^{\mu\nu}
  +\sum_{d>4}\frac{c_d}{\Lambda^{d-4}}\mathcal O_d
$$ {#eq:eft-lagrange}

wobei $c_0$ **dimensionslos** ist und höhere Operatoren $\mathcal O_d$ für $q^2\to0$ unterdrückt sind.

**Ward/BFM-Identität.** Im Background-Field-Gauge gilt $Z_e=Z_A^{-1/2}$, somit $F_1(0)=1$; die geladene Vertizestruktur am Nullimpuls ist **gauge- und schemainvariant**.

**Thomson-Matching.**  

$$
\Gamma^\mu(p',p)=\gamma^\mu F_1(q^2)+\frac{i\sigma^{\mu\nu}q_\nu}{2m}F_2(q^2),\quad F_1(0)=1.
$$ {#eq:thomson-match}

Das Matching am Nullimpuls liefert

$$
\alpha^{-1}(0)=\alpha^{-1}_{\mathrm{QED}}(0)+\Delta*{\mathrm{geom}},\qquad
\Delta_{\mathrm{geom}}\equiv c_0\cdot\frac{4\pi}{e^2}=\frac{K}{n_0}.
$$ {#eq:alpha-Delta-geom}

mit

$$
\mu\frac{d}{d\mu}\Delta_{\mathrm{geom}}=0,\qquad
\frac{\partial \alpha^{-1}(0)}{\partial \xi}=0.
$$ {#eq:Delta-geom-invariance}

**Running unverändert:** Die $\beta$-Funktion wird durch die $q^2$-Ableitung der Photonenselbstenergie bei $q^2>0$ bestimmt.  
Da $c_0$ eine **konstante** (dimensionslose) Randbedingung ist, ändert $\Delta_{\mathrm{geom}}$ die **Running nicht**:

$$
\beta_{\mathrm{EFT}}(g)=\beta_{\mathrm{QED}}(g).
$$ {#eq:beta-eq}

**Physikalische Identifikation:** Die Geometrie/Topologie der Frühphase bestimmt $c_0$ fitfrei über

$$
\Delta_{\mathrm{geom}}=\dfrac{K}{n_0},\qquad
K=\Bigl(1-\tfrac{1}{165}\Bigr)\dfrac{9\sqrt{3}}{\pi},\qquad
n_0=1+1+n_3.
$$ {#eq:Delta-geom-final}

Dies ist eine **Randbedingung** im Thomson-Limit, keine neue Dynamik.

### H — Maxwell-Stress-Tensor ⇒ Thomson-Limit (dreiteilige Ableitung) {#anhang-maxwell-thomson}

Der Maxwell-Stress-Energie-Tensor und der Hodge-Dual sind gegeben durch
$$
{}^{\*}F^{\mu\nu}:=\tfrac12\,\epsilon^{\mu\nu\rho\sigma}F_{\rho\sigma},\qquad
T^{\mu\nu}=\tfrac12\!\left(F^{\mu\alpha}F^{\nu}{}_{\alpha}+{}^{\*}F^{\mu\alpha}\,{}^{\*}F^{\nu}{}_{\alpha}\right).
$$
*Äquivalente Standardform:* $$T^{\mu\nu}=F^{\mu\alpha}F^{\nu}{}_{\alpha}-\tfrac{1}{4}\eta^{\mu\nu}F_{\alpha\beta}F^{\alpha\beta}.$$
mit Energiedichte und Spannung
$$
T^{00}=\tfrac12\,(E^2+B^2),\qquad
T^{ij}=-E^iE^j-B^iB^j+\tfrac12\Delta^{ij}(E^2+B^2).
$$

**Lemma H.1 (Packungsskala).** $a\propto\eta^{-1/3}$.

**Lemma H.2 (Projektion/Arealdichte).** $\rho_{3\mathrm{D}}\propto\eta$ und $\rho_{2\mathrm{D}}\propto \eta^{2/3}$.

**Lemma H.3 (isotrope Mode-Mittelung).** Im Grenzfall $q^\mu\to0$ gilt
$$
\langle T^{00}\rangle_{\mathrm{iso}}=\tfrac12(\langle E^2\rangle_{\mathrm{iso}}+\langle B^2\rangle_{\mathrm{iso}}),\quad
\langle E^2\rangle_{\mathrm{iso}}=\langle B^2\rangle_{\mathrm{iso}}.
$$
Damit tragen elektrische und magnetische Anteile **gleich gewichtet** bei.

**Satz H (Exponenten & Gewichte; Ende der Linearität):** Tangential/Phasenraum koppelt an $\rho_{2\mathrm{D}}\propto\eta^{2/3}$ (quadratisch $\sim\eta^{4/3}$), normal/Magnetfluss volumetrisch an $\rho_{3\mathrm{D}}\propto\eta$ (quadratisch $\sim\eta^{2}$). Isotrope Mittelung ⇒ **1/2-Gewichtung**:
$$
\eta_{\mathrm{eff}}=\tfrac12\,\eta_{\mathrm{FCC}}^{4/3}+\tfrac12\,\eta_{\mathrm{FCC}}^{2}.
$$
*Ende der Linearität:* gültig für $qa\ll1$, isotrope Moden, lineare Maxwell-Antwort; Korrekturen $\mathcal{O}((a/\lambda)^2,\Delta^2)$ bei $qa\gtrsim1$, Anisotropie oder Nichtlinearität.

### H.1 — Exponentenbegründung in $\eta_{\mathrm{eff}}$ {#etaeffexp}
- **M1 (Skalenregel).** Für die FCC-Packung skaliert die Zelllänge wie $a\propto \eta^{-1/3}$ bei fixem Teilchenradius.
- **M2 (Projektion in $B^\perp$).** Die planare Arealdichte entlang einer Feldlinie ergibt sich als Linienintegration über eine Zellhöhe $\sim a$: $\rho_{2\mathrm{D}}\propto\rho_{3\mathrm{D}}\,a\propto \eta\,\eta^{-1/3}=\eta^{2/3}$.
- **M3 (Quadratische Antwort, Thomson-Limit).** Die relevante EM-Antwort ist quadratisch: transversal ($B^\perp$) $\propto \eta^{4/3}$, longitudinal/volumenbasiert $\propto \eta^{2}$.
- **Isotropie & Gewichtung.** D$_6$-Isotropie und Nullimpuls-Matching rechtfertigen eine Gleichgewichtung der zwei Kanäle, somit
$$
\eta_{\mathrm{eff}}=\tfrac12\,\eta_{\mathrm{FCC}}^{4/3}+\tfrac12\,\eta_{\mathrm{FCC}}^{2}.
$$
- *Kontext.* Dies begründet die in [Gleichung @eq:Delta-eta] verwendete Form von $\eta_{\mathrm{eff}}$ fitfrei; die QED-Running bleibt unverändert (Thomson-Randbedingung, vgl. [Anhang G](#anhang-eft-thomson)).
- **Mapping (Auszug Alpha):** tangential/Phasenraum (E) $\leftrightarrow$ Exponent $4/3$; normal/Magnetfluss $\leftrightarrow$ Exponent $2$.
- *Formale Ableitung über $T^{\mu\nu}$, isotrope Mode-Mittelung und Thomson-Matching siehe Abschnitt [H](#anhang-maxwell-thomson).*

### H.2 — E/M-Kopplung → Phasenraum & FCC-Raum {#e-m-koppelung}

Im **Thomson-Limit** ($q^\mu\!\to\!0$) mit isotroper Mittelung koppeln zwei Kanäle:

1. **Phasenraum (E-Kanal, tangential, isotrop):** Die relevante Dichte ist areal. Mit der FCC-Referenzzelle skaliert $a\propto\eta^{-1/3}$, also $\rho_{2\mathrm{D}}\propto\eta^{2/3}$; quadratische EM-Antwort $\Rightarrow$ Beitrag $\propto\eta^{4/3}$.
2. **Magnetfluss (B-Kanal, normal, volumetrisch):** Beitrag $\propto\eta^{2}$.

**Isotropie** erzwingt die **Gleichgewichtung**:  
$$
\eta_{\mathrm{eff}}=\tfrac12\,\eta_{\mathrm{FCC}}^{4/3}+\tfrac12\,\eta_{\mathrm{FCC}}^{2}.
$$
Die formale Ableitung erfolgt über Maxwell-Stress und Background-Field-Matching ([Anhang H](#anhang-maxwell-thomson)).

**FCC-Referenz.** Normierung auf $\eta_{\mathrm{FCC}}=\pi/(3\sqrt{2})$ trennt Geometrie (Packungsdichten) strikt von Projektion; dadurch bleibt die Herleitung fitfrei und falsifizierbar.

**Oktale Tiefenzahl & Koordination.** Die log-basierte Tiefenzahl $n_8$ misst Diskretisierung in Oktalschritten (Basis 8). Der Vorfaktor **12** ist die Koordinationszahl der FCC-Zelle (12 Nachbarn). Beide sind unabhängig vom Orientierungs-Projektor $2^{k}$ und von der geometrischen „8“ in $\eta_2=\pi\sqrt{3}/8$. *Hinweis:* Das „8“ in $8^{n_8}$ bezeichnet ausschliesslich die Oktal-Skalierung der Tiefenzahl und ist nicht identisch mit dem Projektorfaktor $2^{k}$.

### H.3 — Symmetrische Gegenwirkung (Energieverhältnisse) {#symmetrische-gegenwirkung}

**Interpretation (Auszug Alpha).** Der **elektrische** Feldkanal $ph$ bezeichnet den *Phasenraumanteil* der Wellenfunktion $\Psi$. Der komplementäre Kanal ist der **Magnetflusskanal $mag$**.

Wir modellieren die erste Teilung mit

$$
E_{\mathrm{ph}}=\Bigl(\tfrac12-\Delta\Bigr)E_{\mathrm{tot}},\qquad
E_{\mathrm{mag}}=\Bigl(\tfrac12+\Delta\Bigr)E_{\mathrm{tot}},\qquad
\Delta=\frac{1}{2\cdot3\cdot5\cdot 11}=\frac{1}{330}\approx 3.03\times10^{-3}.
$$ {#eq:ea-eb}

Damit ist die **Gegenwirkung** per Konstruktion **symmetrisch**: das Defizit $(-\Delta)$ in einem Kanal erscheint als $+\Delta$ im komplementären Kanal, und

$$
E_{\mathrm{ph}}+E_{\mathrm{mag}}=E_{\mathrm{tot}}.
$$ {#eq:ea-plus-eb}

**Verhältnisabdruck.**

$$
\frac{E_{\mathrm{ph}}}{E_{\mathrm{mag}}}=\frac{\tfrac12-\Delta}{\tfrac12+\Delta}
=\frac{1-2\Delta}{1+2\Delta}
\approx 1-4\Delta+\mathcal{O}(\Delta^2)
\approx 0.9879.
$$ {#eq:ea-eb-ratio}

**Einbettung** in der kompakten Korrektur
$$
\Delta_\eta=\Bigl(1-\tfrac{1}{3\cdot5\cdot11}\Bigr)\,\frac{9\,\sqrt{3}}{\pi\,n_0},
$$ {#eq:Delta-eta-embed}

manifestiert sich die „11“ multiplikativ als **Residualfaktor**; sie steuert **nicht** die spätere Running (Thomson-Limit, fitfrei).

### H.4 — Normierungsfaktor „12“ — Verweis {#anhang-12-xref}

Die ausführliche Definition und Begründung des festen Vorfaktors $12\equiv z_{\mathrm{FCC}}$ im $\rho$-Pfad findet sich in Abschnitt [G.7](#anhang-12).

**Definition H.0.1 (Feste Normierung).** Im $\rho$-Pfad [Gleichung @eq:eta-eff-em]–[@eq:n8-anhang] setzen wir den konstanten Vorfaktor auf  
$12 \equiv z_{\mathrm{FCC}}$, die Koordinationszahl der FCC-Packung.

**Motivation (kurz):**  
(i) *Geometrisch.* In der dichtesten Kugelpackung (FCC/HCP) besitzt jeder Punkt $z_{\mathrm{FCC}}=12$ nächste Nachbarn. Diese Zahl charakterisiert die minimalen Kontakt-/Flussrichtungen und liefert eine natürliche, gitterunabhängige Normierungsskala für die dichtebasierte Tiefe $n_8$.  
(ii) *Feldtheoretisch verträglich.* Im Background-Field-Formalismus verschiebt eine konstante, dimensionslose Normierung die endliche Randbedingung am Nullimpuls, nicht aber die Running (vgl. [Anhang G](#anhang-eft-thomson)). Die Wahl $12$ ist damit eine **festgelegte Referenznormierung** und **kein** Fit.  
(iii) *Separationsprinzip.* Der Vorfaktor $12$ (geometrische Normierung) ist **unabhängig** vom projektiven Faktor $2^{k}$ (Orientierungszählung) und von $\eta_2$’s geometrischer „8“.  
(iv) *Stabilität.* Eine hypothetische Änderung $12\to c$ würde $n_8$ um $\Delta n_8=\log_8(c/12)$ verschieben; für $c$ in der Nähe von $12$ bleibt $n_3=\operatorname{round}(n_8)$ robust (vgl. [Abschnitt Fehlerbudget im $\rho$-Pfad](#rho-fehlerbudget)).

*Hinweis.* Diese Normierung wird im Notebook konsistent verwendet; sie bestimmt lediglich die additive Konstante in $n_8$ und ist durch die FCC-Referenz motiviert, ohne zusätzliche Freiheitsgrade einzuführen.

## I — Threats to Validity (Checkliste) {#anhang-validitaet}
* Isotropieannahme
* Lokalfaktorisierung 3/5
* Minimalität/Unabhängigkeit 11
* **Strikte Trennung** Orientierungsprojektor vs. Geometriedichten

## J — Notebook-Artefakte (Auszug) {#anhang-notebook}
Notebook: `notebooks/Alpha.ipynb`.

**Erzeugte Dateien (Build-Pfad):**
- `anc/certificate_alpha11.csv` — BFS-Minimalitätszertifikat (L=3..15)
- (weitere Logs/Artefakte je nach Lauf)

## K — Integritätsnachweise {#anhang-integritaet}
Axiom-Freeze, Daten-Freeze, deterministische Pipeline, Repro-Artefakte (mit Preprint-Release dokumentiert).

## Y — Urheberschaft {#anhang-urheberschaft}

Offenlegung von KI-Hilfe: ChatGPT (OpenAI; GPT-5 Pro; 08/2025) wurde unterstützend eingesetzt als intelligente Bibliothek, Rechner und „Plausibilisierer“ – insbesondere für Literaturrecherche, Zitationsaufbereitung, anschlussfähige Formulierungen sowie zur Validierung und Implementierung von Code und Teilen der Prüf-Formeln.  
Alle neuen Ideen – einschliesslich der Kernformel zu $\alpha$, des Bezugs zur Dichte und der Packungsproblematik im Magnetfluss im Vergleich zum Phasenraum sowie des Anschlusses zu Primzahlen der QCD – stammen vom Autor; die Inhalte und Ergebnisse wurden vom Autor verifiziert. Die KI war nicht Urheberin wissenschaftlicher Resultate.

## Z — Literatur {#anhang-literatur}

*Bibliographie:*
