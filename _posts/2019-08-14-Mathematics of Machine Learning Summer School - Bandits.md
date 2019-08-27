---
title: 'Mathematic of Machine Learning Summer School - Bandits'
date: 2019-08-14
permalink: /posts/2019/08/Mathematics of Machine Learning Summer School - Bandits/
excerpt: "This is my note of Mathematics of Machine Learning Summer School - Bandits at University of Washington, which was taught by Kevin Jamieson (University of Washington)."
toc: true
tags: [Bandits, Machine Learning, MSRI]
header-includes:
  - \usepackage{algorithm2e}
---

In the past few decades, machine learning was more focusing on how to analyze the past data to use them on future data, while the next decade, Kenvein think it will be more conversation and interaction. Bandits can hence close the loop on inferences and data collection to balance the exploration and exploitation to optimally complete a task. Bandits' problem is named after Casino, which is a way to find a optimal policy to pull down slot machines. The bandits' problems can be generally modeled as following:

{% include pseudocode.html id="1" code="
\begin{algorithm}
\caption{General Bandits' Problems}
\begin{algorithmic}
\Require $n$ arms of slot machines
\PROCEDURE{GeneralBandits}{$n$}
    \FOR{$t =1, ..., T$} 
        \STATE Algorithms pull arm $I_t \in [n] := \{1, 2, ..., n\}$
        \STATE Nature reveals $r_t \sim \mathbb{P}_{I_t}$, $\mathbb{E} \left [ r_t | I_t \right ] = \theta_{I_t}^*$
    \ENDFOR
\ENDPROCEDURE
\end{algorithmic}
\end{algorithm}
" %}

Which means supposed we have different i.i.d. with unknown means, yhe things we can do is simultaneously explore and exploit the situation. 

One of the goal of the bandits' problems is trying to figure out an algorithm to minimize the regret. We can define regreat as follows:

$$
\textrm{Regret: } R_T = \max_i \theta_i^*T - \mathbb{E}\left [ \sum_{t=1}^Tr_t \right],
$$ 

Which means the difference of the most reward can got in expectation and real rewards in each single time. This means how much worse the player is doing then playing the optimal policy. 



# UCB
Considering the following problems:

$$
\textrm{Regret: } R_T = \max_i \theta_i^*T - \mathbb{E}\left [ \sum_{t=1}^Tr_t \right]
$$ 


## Algorithm 1
Just a sample algorithmn

{% include pseudocode.html id="2" code="
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


# Linear Bandits
Considering the following problems:

$$
\textrm{Regret: } R_T = \max_i \theta_i^*T - \mathbb{E}\left [ \sum_{t=1}^Tr_t \right]
$$ 


# Contextual Bandits

References
------
