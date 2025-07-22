# LATEX-Template für den Praxisbericht bei der HSBA

## Allgemeines
Die hier zu findenen Dateien bilden ein Template, das einen Praxisbericht der HSBA abbildet. Es wird also auf die Chicago-Zitierweise, Seitennummerierungen sowie auf Regularien wie die Declaration of Honour geachtet. 

Die abgelegten Dateien beinhalten keinen Build - dieser muss selbst über einen eigenen Compiler erstellt werden. Es ist keine LATEX-Installation vorhanden und keine Perl-Umgebug, diese müssen ggf. selbst installiert werden.

Es wird kein Anspruch auf Vollständigkeit erhoben.

## Dokumentstruktur
Es existiert eine `main.tex`, in die alle anderen Dateien eingebunden werden. Es wird empfohlen, für jedes Kapitel eine eigene Datei zu erstellen, um der Konvention zu folgen. Mehr dazu unter **Inhalt hinzufügen**

## Fragestellung und allgemeine Informationen
Die entsprechenden Informationen können unter __Header/firstPage.tex__ verändert werden <br> <br>

```latex 
\def\Fragestellung{Hier steht eine sehr wichtige Fragestellung, die den ganzen Praxisbericht beeinflussen wird}
\def\Modul{Modul} 
\def\Dozent{Dozent} 
\def\Datum{Datum}
\def\Name{Name} 
\def\Immatrikualtionsnummer{Ik.Nr.}
\def\Emai{Email}
\def\Unternehmen{Unternehmen}
\def\Wortzahl{Wortzahl}
```

Die entsprechenden Informationen kommen in die geschweiften { } Klammern.

## Verzeichnisse
### 1. Abkürzungsverzeichnis <br>
   Das Abkürzungsverzeichnis muss manuell gepflegt werden. Dies geschieht in __Header/Verzeichnisse.tex__. <br> <br>
   ```latex
   \begin{acronym}
         \acro{Abkürzung}{Langform} 
         \acro{NocheineAbkürzung}{Langform}
         \acro{WiedereineAbkürzung}{Langform}
\end{acronym}
```

Eine neue Abkürzung wird mit `\acro` hinzugefügt, danach folgt die Abkürzung und die Langform der Abkürzung.

Für mehr Informationen, sowie Verwendungshinweise: https://www.namsu.de/Extra/pakete/Acronym.html
### 2. Abbildungsverzeichnis
Das Abbildungsverzeichnis wird automatisch generiert. Sobald der Befehl `\caption` in einer __figure-Struktur__ zu finden ist, wird sie ins Verzeichnis aufgenommen

Für mehr Informationen: https://www.heise.de/tipps-tricks/LaTeX-Abbildungsverzeichnis-automatisch-erstellen-7261837.html
### 3. Tabellenverzeichnis
Wie das Abbildungsverzeichnis wird auch das Tabellenverzeichnis generiert. Wieder muss der Befehl `\caption` in der __table-Struktur__ sein, um sie ins Verzeichnis zu überführen.
### 4. Literaturverzeichnis
Das Literaturverzeichnis baut sich automatisch anhand der genutzten Quellen auf. Die Quellen müssen manuell unter __Literatur/literatur.bib__ gepflegt und angelegt werden. Die Quellen tauchen erst im Verzeichnis auf, wenn diese auch im Text zitiert werden. Sollten keine Quellen zitiert werden, generiert sich auch das Literaturverzeichnis nicht.

Siehe https://www.overleaf.com/learn/latex/Bibliography_management_with_bibtex#Enter_\(\mathrm{Bib\TeX}\) ab Punkt 4.

Häufig lassen sich die Einträge generieren, etwa über Generatoren im Internet oder direkt über Literatursuchmaschinen wie Google Scholar.

### Ich brauche ein Verzeichnis nicht?
Wird ein Verzeichnis nicht benötigt, lässt es sich einfach unter __Header/Verzeichnisse.tex__ löschen (nicht das Literaturverzeichnis). 

```latex
\section*{Abkürzungsverzeichnis}
\addcontentsline{toc}{section}{Abkürzungsverzeichnis}

%Abkürzungen pflegen
\begin{acronym}
   \acro{Abkürzung}{Langform}
   \acro{NocheineAbkürzung}{Langform}
   \acro{WiedereineAbkürzung}{Langform}
\end{acronym}

\newpage
\listoffigures
\newpage
\listoftables
\newpage
```

Zum entfernen muss jeweil das `\name` und das `\newpage` gelöscht werden. Für das Abkürzungsverzeichnis alles von `\section` bis `\end`

## Inhalt hinzufügen
Es existiert bereit eine Datei für die Einleitung unter __Inhalt/Einleitung.tex__. Für jedes weitere Kapitel wird empfohlen eine seperate Datei anzulegen und diese später über `\include` in die `main.tex` einzubinden. Es sollte auf das `\section` am Anfang jeder Datei geachtet werden, damit das Kapitel im Literaturverzeichnis auftaucht.

## Anhänge 
Die verschiedenen Anhänge können unter __Anhaenge__ bearbeitet werden. Sollte ein Anhang nicht benötigt werden, so kann dieser gelöscht oder der `\include` aus der `main.tex` entfernt werden.

## Zitieren
Zum zitieren existieren zwei selbstverfasste Makros. 

1. `\zganz`
Zitiert im Stil (Autor, Jahr, Seitenzahl)
2. `\znenn`
Zitiert im Stil Autor (Jahr, Seitenzahl)

Beide Befehle lassen sich jederzeit im Text verwenden.
Der Aufruf erfolgt so:

```latex
z\ganz[Seitenzahl]{Objekt aus der .bib Datei}
```
Beispielaufrufe mit den Beispielquellen aus der ``literatur.bib``:

```latex
z\ganz[S. 344]{PP95}           %Output: (Parusi´nski und Pragacz 1995, S. 45)

z\nenn[S. 12]{aigner2015buch}  %Output: Aigner, Ziegler und Hofmann (2015, S. 12)
```
