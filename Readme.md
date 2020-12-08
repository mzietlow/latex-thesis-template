# Transferleistung-LaTeX
Dieses Markdown-File ist Schmu. Ich werde, irgendwann, versuchen es nach LaTeX
zu migrieren - und vor allem zu vervollständigen.

Installation:
1. texlive installieren (am besten im Hintergrund laufen lassen) -> https://www.tug.org/texlive/acquire-netinstall.html -> install-tl-windows.exe
2. VSCode installieren -> https://code.visualstudio.com/download
3. Plugins: LaTeX Workshop
3.1 Optionale Plugins: LaTeX Utilities, LTeX, SpellChecker

Nutzung:
1. git clone https://github.com/mzietlow/resource-mania-doc
2. VSCode -> File -> Open Folder -> <path> -> öffnen
3. main.tex auswählen
4. strg + alt + x für das LaTeX Menü
5. Build LaTeX project

So, zum LaTeX Einstieg erstmal alles was man so grob wissen sollte:
Der Einstiegspunkt für LaTeX ist main.tex
main.tex ist in zwei Abschnitte gegliedert, die Präambel und das Dokument.

In der Präambel wird das Dokument konfiguriert, der Titel wird festgelegt, die Autoren, das Format. Außerdem werden alle Pakete eingebunden, die genutzt werden sollen.

Die Pakete in unserer Präambel sind zusätzlich nach Wirkungsbereich untergliedert, um die Präambel übersichtlich zu halten. Alle Pakete zum Thema Zitation werden zum Beispiel über \input{preamble/references-and-citation.tex} eingebunden.

Das Dokument selbst beginnt ab \begin{document} ... \end{document}
Es ist unterteilt in Frontmatter, Mainmatter und Backmatter.

Eine Datei, die ein bisschen heraussticht, ist GlossarMetadaten. Hier werden alle Akronyme und Glossar-Einträge d…
Jedem Kapitel habe ich ein eigenes .tex-file zugeordnet. Mit strg+Rechtsklick öffnet VSCode die Datei automatisch in einem neuen Tab.

In unserem Dokument ist die höchste Gliederungsebene die section.
\section{Einleitung}
Jede weitere Untergliederung beginnt mit einem vorangestellten sub-
\subsection{Beispiel1}
\subsubsection{Beispiel2}
Zum Beginnen einer neuen Subsection einfach
\subsection{Beispiel3}
Alle sections/subsections landen im Inhaltsverzeichnis:
1. Einleitung
1.1 Beispiel1
1.1.1 Beispiel2
1.2 Beispiel 3
daher habe ich die Untergliederungstiefe auf subsubsection begrenzt.
Weitere Untergliederung kann über \paragraph{Ein Paragraph} erreicht werden. Die landen nicht im Inhaltsverzeichnis und werden nicht nummeriert.

Absätze macht man in LaTeX eher selten. Falls es wirklich notwendig ist, dann entweder
über 2x Enter oder
\par
Ich würde \par bevorzugen, weil es die Absicht eindeutig macht.

Querverweise sind noch cool:
\section{Einleitung}\label{sec:Einleitung}
[...]

[...] siehe \cref{sec:Einleitung}.
VSCode bietet hier btw automatisch code completion an


Typesetting ist eine Sache für sich. Studenten dazu zu zwingen, das Rad stets
neu zu erfinden, ist eine schlechte Idee. Der folgende Guide richtet sich,
entsprechend, an Studenten, die bisher noch keine Erfahrungen auf diesem Gebiet
angesammelt haben. Einen sehr viel Umfassenderen Ansatz verfolgt TheMegaTB unter
https://github.com/TexNAK/Science-Paper-Template. Dieser Guide entspringt
persönlicher Erfahrung, den Arbeiten meines Bruders sowie den Arbeiten von
FWellers (https://gitlab.com/fwellers/texfornak) und OleKoring
(https://gitlab2.nordakademie.de/OleKoring-I16/LaTeX-Transferleistung/)
Ziel ist es letztlich, Minimalbeispiele für die häufigsten Problemstellungen
bieten zu können und diese übersichtlich aufzubereiten.


Softwarestack: VSCode, TeX Live, LuaLaTeX
Entwicklungsumgebung

### Aussprache: LaTeX: Latech < - 'frech'.

### LaTeX & Entwicklungsumgebung

Das Anfang der 80.-Jahre von Leslie Lamport entwickelte LaTeX (Lamport Tex) ist
eine Erweiterung des ursprünglichen Textsatzsystems TeX. Für LaTeX selbst
existieren ebenfalls zahllose Zusatzprogramme, die von unterschiedlichen Gruppen
zu Distributionen zusammengefasst wurden. Deren bekannteste MikTeX und TeX Live.
Weiterführend hierzu: https://www.schlosser.info/miktex-vs-texlive/ Im Folgenden
soll die Installation von TeX Live unter Win10 durchexerziert werden.

Weitere Informationen über https://www.latexbuch.de/latex-windows-installieren/

### TeX Live Installation

Es ist unbedingt auf eine Stabile Internetverbindung zu achten, da der Setup
bei einem Disconnect komplett abbricht.
http://www.tug.org/texlive/ -> download -> install-tl-windows.exe
oder direkt: http://mirror.ctan.org/systems/texlive/tlnet/install-tl-windows.exe
Optional auch als zip verfügbar, das Archiv entpacken und install-tl-windows.bat
ausführen.

Standard-Papierformat: A4
TeXworks wird in dieser Einleitung nicht benötigt, als Editor wird VSCode genutzt.

Da Tex Live ursprünglich per CD vertrieben wurde (und auch weiterhin wird),
fehlen der Distribution einige grundsätzlich kostenlose Fonts (Schriftarten).
Diese werden im nächsten Schritt nachgeladen.
1. Hierzu install-getnonfreefonts
(http://tug.org/fonts/getnonfreefonts/) herunterladen.
2. Kommandozeile öffnen (win+r: cmd oder win+x->Kommandozeile/Command Prompt)
3. cd '<download-pfad>'
4. texlua install-getnonfreefonts
   getnonfreefonts --sys --all (falls keine Admin-Rechte, statt --sys:--user)
5.

### VSCode Installation und Setup

Da mich hässliche Editoren deprimieren (bin da oberflächlich), nutze ich VSCode.
Als ich mich das erste Mal mit LaTeX Editoren auseinandergesetzt hatte, bin ich
bei Atom gelandet. 2018 war das eine schlechte Wahl, wie es heute ist, kann
ich nicht beurteilen. Mit VSCode bin ich allerdings sehr glücklich.

### Das einbinden von Grafiken, Installation von Ghostscript
https://www.latexbuch.de/latex-windows-installieren/#x1-70002 (Postscript)

### Hinweise zu Schriftarten

Mit \usepackage{fontspec} können die auf dem PC verwendeten Schriftarten
verwendet werden. \setmainfont{Arial} wählt dann Arial als Schriftart aus. So
kann auch Times New Roman ausgewählt werden.

Alternativ kann auch \usepackage{lmodern} genutzt werden. Damit werden
Schriftarten genutzt, die eigentlich wie Arial und Times New Roman aussehen.
Standardmäßig ist eine Schrift mit Serifen ausgewählt.
\renewcommand*\familydefault{\sfdefault} setzt dann eine serifenlose Schriftart.

### Hinweise zum Zitieren

\usepackage[backend=biber, style=apa, citestyle=authoryear-ibid]{biblatex}
Die Option style setzt den Stil des Literaturverzeichnisses, citestlye setzt den
Stil bei Zitaten.

Zitiert werden kann dann zum Beispiel mit \cite{bibid} oder mit
\footcite{bibid}. Wenn noch ein Vgl. davor und eine Seitenangabe dahinter soll
geht das mit \cite[Vgl.][150]{bibid}.

Dokumentation Biblatex:
https://mirror.hmc.edu/ctan/info/translations/biblatex/de/biblatex-de-Benutzerhandbuch.pdf

### Hinweise für Tabellen
Todo

### Absätze

Mit \par können Absätze eingefügt werden.
