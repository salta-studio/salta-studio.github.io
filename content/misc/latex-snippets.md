+++
title = "latex snippets"
weight = 2
+++

Here are the snippets of things I add to my latex files to DRY my content structures.

#### Dialogue, Classic

<img src="/dialogue.png" class="radial-fade" alt="dialogue" style="margin: 0 auto;" />

```latex
\newcommand{\dialogue}[3]{
	\begin{quote}
		\centering
		\vspace{0.25cm}
		\textit{#2} \\ \textbf{\footnotesize{#1}} \\\textit{\footnotesize{#3}}
		\vspace{0.25cm}		
	\end{quote}
}

\dialogue{Star}{I said I’ve got this}{muttered, tightening her jaw}
```

#### For Graphic Novels

<img src="/graphic-novels.png" class="radial-fade" alt="dialogue" style="margin: 0 auto;" />

```latex
\NewDocumentEnvironment{GNPage}{ O{} }{%
  \refstepcounter{gnpage}
  \setcounter{gnpanel}{0}
  \vspace{1em}
  {\bfseries PAGE \thegnpage%
    \IfValueT{#1}{ - #1}%
  }\par
  \vspace{0.5em}
}{%
  \vspace{1em}
}

\NewDocumentCommand{\Env}{ +m }{%
  {\bfseries\MakeUppercase{#1}}\par
}

\NewDocumentCommand{\Panel}{ s O{} +m }{%
  \par\vspace{0.5em}
  \IfBooleanTF{#1}{%
    {\bfseries PANEL%
      \IfValueT{#2}{\ \textnormal{(\MakeUppercase{#2})}}%
    }\par
  }{%
    \refstepcounter{gnpanel}
    {\bfseries PANEL \thegnpanel%
      \IfValueT{#2}{\ \textnormal{(\MakeUppercase{#2})}}%
    }\par
  }%
  #3\par
}

\NewDocumentCommand{\Action}{ +m }{%
  #1\par
}

\NewDocumentCommand{\Caption}{ +m }{%
  {\itshape CAPTION: #1}\par
}
\NewDocumentCommand{\Narration}{ +m }{%
  {\itshape NARRATION: #1}\par
}

\NewDocumentCommand{\SFX}{ +m }{%
  {\bfseries SFX: \MakeUppercase{#1}}\par
}

\NewDocumentCommand{\Transition}{ +m }{%
  \hfill{\bfseries \MakeUppercase{#1}}\par
}

\NewDocumentCommand{\Note}{ +m }{%
  {\small\itshape [NOTE: #1]}\par
}

\NewDocumentCommand{\Dialogue}{ O{} m +m }{%
  {\par\noindent\centering\textsc{#2}\par}
  \begin{list}{}{%
    \setlength{\leftmargin}{\GNDialogueLeft}%
    \setlength{\rightmargin}{\GNDialogueRight}%
    \setlength{\itemsep}{0pt}%
    \setlength{\parsep}{0pt}%
    \setlength{\topsep}{2pt}%
  }%
    \item
      \IfValueT{#1}{\emph{(#1)}\par}
      #3
  \end{list}%
}

\NewDocumentCommand{\Beat}{}{%
  {\itshape (beat)}\par
}

\GNTitle{Lembas}{noumena}[Draft — \today]

\begin{GNPage}[Chapter 1 - The Universe Has HR]
\Env{EXT. ALIEN RIVERBANK - NIGHT}

\Panel[WIDE ESTABLISHING]{A black river cuts through neon mushrooms. Distant mountains look like broken teeth under a fully starry sky.}

\Caption{Somewhere that definitely isn't regulated by The Cosmic Federation.}

\Action{EA's helmet reflects constellations like an accusation. AHURA pokes a glowing fungus with deep suspicion.}

\Dialogue[deadly serious]{EA}{We need to talk.}

\Dialogue[deadpan]{AHURA}{Communication? In this economy?}

\Panel{A shadow passes over them. Something huge. Wings.}

\SFX{WHOOOOM}

\Dialogue{EA}{That's not a cloud.}

\Transition{CUT TO:}

\end{GNPage}
```

#### Book Template

<a href="/book-template.tex" alt="Book Template Latex" />

<object class="pdf-container" data="/book-template.pdf" type="application/pdf">
  <p>
    Your browser can’t display PDFs inline.
    <a href="/book-template.pdf">Open the PDF</a>
  </p>
</object>


#### Character Development Sheet

<a href="/character-development-sheet.tex" alt="Character Development Sheet Latex" />

<object class="pdf-container" data="/character-development-sheet.pdf" type="application/pdf">
  <p>
    Your browser can’t display PDFs inline.
    <a href="/character-development-sheet.pdf">Open the PDF</a>
  </p>
</object>
