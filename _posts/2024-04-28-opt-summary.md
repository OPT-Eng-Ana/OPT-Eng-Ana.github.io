---
layout: distill
title: Be Careful When Claiming Theoretical Outperformance of Your Optimization Algorithms - Review and Beyond
description: In this blog, we revisit the convergence analysis of first-order algorithms in minimization and minimax optimization problems. Within the classical oracle model framework, we review the state-of-the-art upper and lower bound results in the literature, categorizing various settings based on convexity, smoothness, and stochasticity, aiming to identify gaps in existing research. Then regarding the rapid development of applications in areas like machine learning and operation research, we review some recent works that revised the classical settings of optimization algorithms study inspired from practices, e.g., smoothness, silver stepsize, and heavy-tailedness.
tags: optimization
giscus_comments: true
date: 2024-04-28
featured: true

# Take care the difference compared to the actual template of ICLR Blog
# Diff 1: image, figure.html and figure.liquid

# anonymize when submitting 
authors:
  - name: Anonymous 

# authors:
#   - name: Albert Einstein
#     url: "https://en.wikipedia.org/wiki/Albert_Einstein"
#     affiliations:
#       name: IAS, Princeton
#   - name: Boris Podolsky
#     url: "https://en.wikipedia.org/wiki/Boris_Podolsky"
#     affiliations:
#       name: IAS, Princeton
#   - name: Nathan Rosen
#     url: "https://en.wikipedia.org/wiki/Nathan_Rosen"
#     affiliations:
#       name: IAS, Princeton

bibliography: 2024-04-28-opt-summary.bib

# Add a table of contents to your post.
#   - make sure that TOC names match the actual section names
#     for hyperlinks within the post to work correctly.
toc:
  - name: Introduction
  - name: Notations and Terminology
  - name: Framework Oracle Model
  - name: Summary of Results
  - name: To Have a Better Bound
  - name: Conclusion
  - 
---

## Introduction

content

$$
\min_{x\in\mathcal{X}}\ f(x)
$$

The citation is presented inline like this: <d-cite key="gregor2015draw"></d-cite> (a number that displays more information on hover).

Here is another one: <d-cite key="zhang2021complexity"></d-cite>

---

## Notations and Terminology

content

> **Definition (Deterministic Algorithm)**

> **Definition (Finite-Sum Algorithm)** 

> **Definition (Stochastic Algorithm)**

---

## Framework Oracle Model

> **Definition (Upper Bound)**

> **Definition (Lower Bound)**

content

```markdown
{% raw %}{% include figure.html path="assets/img/2025-04-28-distill-example/iclr.png" class="img-fluid" %}{% endraw %}
```

{% include figure.liquid path="assets/img/2024-04-28-opt-summary/complexity_analysis.jpg" class="img-fluid" %}

<div class="caption">
    Oracle Complexity Framework
</div>

---

## Summary of Results

We categorize the discussion based on the problem formulation, stochasticity and convergence measurement, for convenience of presentation, we divide the tables into the following cases:

**Minimization Problems**
1. Deterministic optimization algorithms
2. Finite-sum and stochastic optimization algorithms

**Minimax Problems**
1. SC-SC/SC-C/C-C deterministic minimax optimization
2. SC-SC/SC-C/C-C finite-sum and stochastic minimax optimization
3. NC-SC/NC-C deterministic minimax

{% include figure.liquid path="assets/img/2024-04-28-opt-summary/upper_lower.png" class="img-fluid" %}

<div class="caption">
    A simple, elegant caption looks good between image rows, after each row, or doesn't have to be there at all.
</div>

| Problem Type               | Measure                   | LB                     | UB          | Reference<d-footnote>Note that here possibly we may not choose the most original work which proposed the results, rather we may select the literature which we are more familiar with, also with a clearer presentation. Readers are encouraged to check the reference therein for the original works.</d-footnote>                                |
|----------------------------|---------------------------|------------------------|-------------|------------------------------------------|
| $L$-Smooth Convex          | $f(x^K) - f^*$           | $\Omega \left( \sqrt{L \epsilon^{-1}} \right)$                | $\checkmark$ | [<d-cite key="nesterov2018lectures"></d-cite>, Theorem 2.1.7; Theorem 2.2.2]       |
| $L$-Smooth $\mu$-SC        | $f(x^K) - f^*$           | $\Omega \left( \sqrt{\kappa} \log \frac{1}{\epsilon} \right)$ | $\checkmark$ | [<d-cite key="nesterov2018lectures"></d-cite>, Theorem 2.1.13]                     |
| NS $L$-Lip Ct Convex       | $f(x^K) - f^*$           | $\Omega (L^2 \epsilon^{-2})$                                  | $\checkmark$ | [<d-cite key="bubeck2015convex"></d-cite>, Theorem 3.8]                        |
| NS $L$-Lip Ct $\mu$-SC     | $f(x^K) - f^*$           | $\Omega (L^2 (\mu \epsilon)^{-1})$                            | $\checkmark$ | [<d-cite key="bubeck2015convex"></d-cite>, Theorem 3.8]                        |
| $L$-Smooth Convex          | $\|\| \nabla f(x^K) \|\|$    | $\Omega \left( \sqrt{\Delta L \epsilon^{-1}} \right)$     | $\checkmark$ | [<d-cite key="carmon2021lower"></d-cite>, Theorem 1 & Appendix A.1]              |
| $L$-Smooth NC              | $\| \nabla f(x^K) \|$    | $\Omega (\Delta L \epsilon^{-2})$                             | $\checkmark$ | [<d-cite key="carmon2020lower"></d-cite>, Theorem 1]      |
| NS $L$-Lip Ct $\rho$-WC    | Near-stationarity        | Unknown                                                       | $\mathcal{O}(\epsilon^{-4})$      | [<d-cite key="davis2018stochastic"></d-cite>, Theorem 2.1 implied]                  |
<div class="caption">
    **Case 1:** Summary of lower bounds (LB) and upper bounds (UB) for different problem types and measures, with references to key theorems.
</div>


---

## To Have a Better Bound

content

---

## Conclusion

content


Colons can be used to align columns.

| Tables        |      Are      |  Cool |
| ------------- | :-----------: | ----: |
| col 3 is      | right-aligned | $1600 |
| col 2 is      |   centered $\times$    |   $12 |
| zebra stripes |   are neat $\checkmark$   |    $1 |

There must be at least 3 dashes separating each header cell.
The outer pipes (|) are optional, and you don't need to make the
raw Markdown line up prettily. You can also use inline Markdown.

| Markdown | Less      | Pretty     |
| -------- | --------- | ---------- |
| _Still_  | `renders` | **nicely** |
| 1        | 2         | 3          |

> Blockquotes are very handy in email to emulate reply text.
> This line is part of the same quote.

Quote break.

> This is a very long line that will still be quoted properly when it wraps. Oh boy let's keep writing to make sure this is long enough to actually wrap for everyone. Oh, you can _put_ **Markdown** into a blockquote.

Here's a line for us to start with.

This line is separated from the one above by two newlines, so it will be a _separate paragraph_.

This line is also a separate paragraph, but...
This line is only separated by a single newline, so it's a separate line in the _same paragraph_.
