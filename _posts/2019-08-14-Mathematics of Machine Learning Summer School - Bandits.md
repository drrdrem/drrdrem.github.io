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

In the past few decades, machine learning was more focusing on how to analyze the past data using them for future data, while the next decade, Kenvin think it will be more conversation and interaction. Bandits can hence close the loop on inferences and data collection to balance the exploration and exploitation to optimally complete a task. Bandits' problem is named after Casino, which is a way to find an optimal policy to pull down slot machines. The bandits' problems can be generally modeled as following:

{% include pseudocode.html id="1" code="
\begin{algorithm}
\caption{General Bandits' Problems}
\begin{algorithmic}
\Require $N$ arms of slot machines
\PROCEDURE{GeneralBandits}{$N$}
    \FOR{$t =1, ..., T$} 
        \STATE Algorithms pull arm $I_t \in [N] := \{1, 2, ..., N\}$
        \STATE Nature reveals $r_t \sim \mathbb{P}_{I_t}$, $\mathbb{E} \left [ r_t | I_t \right ] = \theta_{I_t}^*$
    \ENDFOR
\ENDPROCEDURE
\end{algorithmic}
\end{algorithm}
" %}

Which means supposed we have different i.i.d. with unknown means, the things we can do is simultaneously explore and exploit the situation. 

One of the goals of the bandits' problems is trying to figure out an algorithm to minimize the regret. We can define regret as follows:

$$
\textrm{Regret: } R_T = \max_i \theta_i^*T - \mathbb{E}\left [ \sum_{t=1}^Tr_t \right],
$$ 

which means the difference of the most reward can be gotten in expectation and real rewards in each single time. This means how much worse the player is doing than playing the optimal policy. 



# UCB
Considering the following problems:

$$
\textrm{Regret: } R_T = \max_i \theta_i^*T - \mathbb{E}\left [ \sum_{t=1}^Tr_t \right]
$$ 

{% include pseudocode.html id="2" code="
\begin{algorithm}
\caption{Upper Confidence Bound (UCB)}
\begin{algorithmic}
\Require $N$ arms of slot machines
\PROCEDURE{UCB}{$N$}
    \STATE \textbf{Initialize:} Count $C_n^0 \leftarrow 0$; Estimate maen $\hat{\theta}_n^0 \leftarrow 0$
    \FOR{$t =1, ..., T$} 
        \IF{$t \leq N$}
        \STATE Play arm t
        \STATE $C_n^t \leftarrow \mathbb{I} \left [n = t \right ]$
        \STATE Observe $r_t$
        \STATE $\hat{\theta}_n^t \leftarrow r_t \cdot \mathbb{I} \left [ n = t \right ]$
        \ELSE
        \STATE Play arm $I_t = \argmax_{n \in \left [ N \right]} \left ( \hat{\theta}_n^{t-1} + U_n^{t-1} \right )$
        \STATE $C_n^t \leftarrow C_n^{t-1} + \mathbb{I} \left [ n = I_t \right]$
        \STATE Observe $z_t$
        \STATE $\hat{\theta}_n^t \leftarrow \frac{r_t + C_n^{t-1} \cdot \hat{\theta}_n^{t-1}}{C_n^t} \cdot \mathbb{I} \left [n = I_t \right]  + \hat{\theta}_n^{t-1} \cdot \left ( 1 - \mathbb{I} \left [n = I_t \right ] \right )$
        \ENDIF
    \ENDFOR
\ENDPROCEDURE
\end{algorithmic}
\end{algorithm}
" %}

## Algorithm 1

<!-- {% include pseudocode.html id="2" code="
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
" %} -->


# Linear Bandits
{% include pseudocode.html id="3" code="
\begin{algorithm}
\caption{Linear Bandits}
\begin{algorithmic}
\Require $\mathcal{X}$ 
\PROCEDURE{LinearBandits}{$N$}
    \FOR{$t =1, ..., T$} 
        \STATE Algorithms pick $x_t \in \mathcal{X}$
        \STATE Nature reveals $y_t = \langle x, \theta^* \rangle + \xi_t$
    \ENDFOR
\ENDPROCEDURE
\end{algorithmic}
\end{algorithm}
" %}

# Contextual Bandits

References
------
