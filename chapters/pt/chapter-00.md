```{=latex}
\definecolor{coverbg}{HTML}{1a1a2e}
\definecolor{covershape}{HTML}{16213e}
\definecolor{coveraccent}{HTML}{e94560}
\definecolor{covermuted}{HTML}{a0aec0}

\begin{titlepage}
\thispagestyle{empty}
\pagecolor{coverbg}

\begin{tikzpicture}[remember picture, overlay]
  \fill[coveraccent]
    (current page.north west) rectangle
    ([xshift=14pt]current page.south west);
  \fill[covershape]
    (current page.north east) --
    ([yshift=-16cm]current page.north east) --
    ([xshift=-16cm]current page.north east) --
    cycle;
\end{tikzpicture}

\vspace*{5.5cm}
\hspace{1.5cm}{\color{white}\fontsize{38}{46}\selectfont\bfseries {{BOOK\_TITLE}}}

\vspace{1cm}
\hspace{1.5cm}{\color{covermuted}\fontsize{18}{24}\selectfont {{BOOK\_SUBTITLE}}}

\vspace{0.7cm}
\hspace{1.5cm}{\color{coveraccent}\rule{4cm}{3pt}}

\vfill
\hspace{1.5cm}{\color{covermuted}\fontsize{16}{22}\selectfont {{AUTHOR\_NAME}}}

\vspace{2cm}
\end{titlepage}
\nopagecolor
\tableofcontents
\clearpage
```
