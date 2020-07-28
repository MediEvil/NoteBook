latex笔记
```tex
\AtBeginEnvironment{minted}{%
  \renewcommand{\fcolorbox}[4][]{#4}}
```
用来消除error导致的red box