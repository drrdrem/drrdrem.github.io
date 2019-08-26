---
title: 'Mathematic of Machine Learning Summer School - Bandits'
date: 2019-08-14
permalink: /posts/2019/08/Mathematics of Machine Learning Summer School - Bandits/
toc: true
tags: [Bandits, Machine Learning, MSRI]
header-includes:
  - \usepackage{algorithm2e}
gallery_iterations:
    alt: "Iteration 0"
    title: "Iteration 0"
---

This is the note of Mathematics of Machine Learning Summer School - Bandits at University of Washington, which was taught by Kevin Jamieson (University of Washington).

$$
\frac{n!}{k!(n-k)!} = {n \choose k}
$$

UCB
======


# Algorithm 1
Just a sample algorithmn

{% include pseudocode.html id="1" code="
\begin{algorithm}
\caption{Quicksort}
\begin{algorithmic}
\PROCEDURE{Quicksort}{$A, p, r$}
    \IF{$p < r$} 
        \STATE $q = $ \CALL{Partition}{$A, p, r$}
        \STATE \CALL{Quicksort}{$A, p, q - 1$}
        \STATE \CALL{Quicksort}{$A, q + 1, r$}
    \ENDIF
\ENDPROCEDURE
\PROCEDURE{Partition}{$A, p, r$}
    \STATE $x = A[r]$
    \STATE $i = p - 1$
    \FOR{$j = p$ \TO $r - 1$}
        \IF{$A[j] < x$}
            \STATE $i = i + 1$
            \STATE exchange
            $A[i]$ with     $A[j]$
        \ENDIF
        \STATE exchange $A[i]$ with $A[r]$
    \ENDFOR
\ENDPROCEDURE
\end{algorithmic}
\end{algorithm}
" %}


Linear Bandits
======

Contextual Bandits
======

References
------
