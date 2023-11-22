\begin{tikzpicture}[main/.style = {draw, circle}]

{$x_1$}
This text will be centred since it is inside a special 
$int$
environment. Environments provide a efficient way of modifying 
blocks of text within your document.
\end{tikzpicture} 
\end{center}

\documentclass{article} \begin{document} \begin{tikzpicture}[main/.style = {draw, circle}] \node[main] (1) {$x_1$}; \end{tikzpicture} \end{document}