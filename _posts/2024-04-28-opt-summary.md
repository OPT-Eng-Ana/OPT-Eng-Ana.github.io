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

test citation <d-cite key="ruder2016overview"></d-cite>, <d-cite key="arjevani2016lower"></d-cite>

### Existing survey literature
content, papers, blogs, 

---

## Notations and Terminology

content

> **Definition (Deterministic Optimization)**

> **Definition (Finite-Sum / Stochastic Optimization)** 

> **Definition (Convexity, Strong Convexity, Weak Convexity)**

> **Definition (Lipschitz Continuity)** 

> **Definition (Lipschitz Smoothness)**

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
1. Deterministic optimization
2. Finite-sum and stochastic optimization

**Minimax Problems**
1. SC-SC/SC-C/C-C deterministic minimax
2. SC-SC/SC-C/C-C finite-sum and stochastic minimax optimization
3. NC-SC/NC-C deterministic minimax optimization
4. NC-SC/NC-C finite-sum and stochastic minimax optimization

{% include figure.liquid path="assets/img/2024-04-28-opt-summary/upper_lower.png" class="img-fluid" %}

<div class="caption">
    A simple, elegant caption looks good between image rows, after each row, or doesn't have to be there at all.
</div>

### Case 1-1: Deterministic Minimization

| Problem Type               | Measure                   | Lower Bound            | Upper Bound      | Reference (LB-UB)<d-footnote>Note that here possibly we may not choose the most original work which proposed the results, rather we may select the literature which we are more familiar with, also with a clearer presentation. Readers are encouraged to check the reference therein for the original works.</d-footnote>                                |
|----------------------------|---------------------------|------------------------|-------------|--------------------------------|
| $L$-Smooth Convex          | $f(x^K) - f^\star$           | $\Omega \left( \sqrt{L \epsilon^{-1}} \right)$                | $\checkmark$ | [<d-cite key="nesterov2018lectures"></d-cite>, Theorem 2.1.7; Theorem 2.2.2]       |
| $L$-Smooth $\mu$-SC        | $f(x^K) - f^\star$           | $\Omega \left( \sqrt{\kappa} \log \frac{1}{\epsilon} \right)$ | $\checkmark$ | [<d-cite key="nesterov2018lectures"></d-cite>, Theorem 2.1.13]                     |
| NS $L$-Lip Ct Convex       | $f(x^K) - f^\star$           | $\Omega (L^2 \epsilon^{-2})$                                  | $\checkmark$ | <d-cite key="bubeck2015convex"></d-cite>, Theorem 3.8                        |
| NS $L$-Lip Ct $\mu$-SC     | $f(x^K) - f^\star$           | $\Omega (L^2 (\mu \epsilon)^{-1})$                            | $\checkmark$ | [<d-cite key="bubeck2015convex"></d-cite>, Theorem 3.8]                        |
| $L$-Smooth Convex          | $\|\| \nabla f(x^K) \|\|$    | $\Omega \left( \sqrt{\Delta L \epsilon^{-1}} \right)$     | $\checkmark$ | [<d-cite key="carmon2021lower"></d-cite>, Theorem 1 & Appendix A.1]              |
| $L$-Smooth NC              | $\|\| \nabla f(x^K) \|\|$    | $\Omega (\Delta L \epsilon^{-2})$                             | $\checkmark$ | [<d-cite key="carmon2020lower"></d-cite>, Theorem 1]      |
| NS $L$-Lip Ct $\rho$-WC    | Near-stationarity        | Unknown                                                       | $\mathcal{O}(\epsilon^{-4})$      | [<d-cite key="davis2018stochastic"></d-cite>, Theorem 2.1 implied]                  |

**Remark:**

1. content

### Case 1-2: Finite-sum and Stochastic Optimization (double check)

| Problem Type            | Measure | Lower Bound                                                | Upper Bound                               | Reference (LB-UB)                                       |
|-------------------------|---------|---------------------------------------------------|----------------------------------|-----------------------------------------------------------|
| FS $L$-IS $\mu$-SC      | Optimality gap        | $\Omega \left( n + \sqrt{\kappa n} \log \frac{1}{\epsilon} \right)$ | $\checkmark$ ($\times$)          | [<d-cite key="woodworth2016tight"></d-cite>, Theorem 8] [<d-cite key="defazio2016simple"></d-cite>, Cor 6], [<d-cite key="allen2018katyusha"></d-cite>, Cor 2.1]                          |
| FS $L$-IS C             | Optimality gap        | $\Omega \left( n + D \sqrt{n L \epsilon^{-1}} \right)$         | $\checkmark$ ($\times$)          | [<d-cite key="woodworth2016tight"></d-cite>, Theorem 7] [<d-cite key="allen2018katyusha"></d-cite>, Cor 3.7] |
| FS $L$-AS $\mu$-SC      | Optimality gap        | $\Omega \left( n + n^{\frac{3}{4}} \sqrt{\kappa} \log \frac{\Delta}{\epsilon} \right)$ | $\checkmark$                     | [<d-cite key="xie2019general"></d-cite>, Theorem 3.5], [<d-cite key="allen2018katyusha"></d-cite>, KatyushaX, Sec 5]                                 |
| FS $L$-AS C             | Optimality gap        | $\Omega \left( n + n^{\frac{3}{4}} D \sqrt{L \epsilon^{-1}} \right)$ | $\checkmark$                     | [<d-cite key="zhou2019lower"></d-cite>, Theorem 4.2], [<d-cite key="allen2018katyusha"></d-cite>, KatyushaX, Sec 5]                                 |
| FS $L$-IS NC            | Stationarity        | $\Omega \left( \Delta L \epsilon^{-2} \right)$               | $\times$                          | [<d-cite key="zhou2019lower"></d-cite>, Theorem 4.7], [<d-cite key="wang2019spiderboost"></d-cite>, Thm 1] |
| FS $L$-AS NC            | Stationarity       | $\Omega \left( \sqrt{n \Delta L \epsilon^{-2}} \right)$       | $\checkmark$                     | [<d-cite key="zhou2019lower"></d-cite>, Theorem 4.5], [<d-cite key="fang2018spider"></d-cite>, Thm 2, 3]|
|                         |         |                                                     |                                  |                                                           |
| Stoc $L$-$S$ $\mu$-SC   | Stationarity        | $\Omega (\epsilon^{-1})$                            | $\checkmark$                     | [<d-cite key="rakhlin2012making"></d-cite>, Thm 2] (?), [<d-cite key="ghadimi2012optimal"></d-cite>, Prop 9]                        |
| Stoc $L$-$S$ C          | Stationarity        | $\Omega (\epsilon^{-2})$                            | $\checkmark$                     | [<d-cite key="woodworth2018graph"></d-cite>, Thm 1] (?), [<d-cite key="lan2012optimal"></d-cite>, Thm 1], Modified SA          |
| Stoc NS $\mu$-SC        | Stationarity        | $\Omega (\epsilon^{-2})$                            | $\checkmark$                     | [<d-cite key="agarwal2009information"></d-cite>, Thm 2], [<d-cite key="nemirovski2009robust"></d-cite>, Sec 2.1]                          |
| Stoc NS C               | Stationarity        | $\Omega (\epsilon^{-2})$                            | $\checkmark$                     | [<d-cite key="agarwal2009information"></d-cite>, Thm 1], [<d-cite key="nemirovski2009robust"></d-cite>, Sec 2.2]                        |
| Stoc $L$-$S$ $\mu$-SC   | Stationarity        | $\Omega (\epsilon^{-2})$ (implied)                  | $\checkmark$                     | [<d-cite key="foster2019complexity"></d-cite>, Theorem 1], AC-SA$^2$: $\mathcal{O} \left( \sqrt{\frac{LD}{\epsilon}} \log k + \frac{\sigma_x^2}{\epsilon^2} \log^3 k \right)$ |
| Stoc $L$-$S$ C   | Stationarity        | $\Omega \left( \frac{LD}{\epsilon} + \frac{\sigma_x^2}{\epsilon^2} \log \frac{LD}{\epsilon} \right)$ | $\checkmark$       | [<d-cite key="foster2019complexity"></d-cite>, Theorem 1, Corollary 1], AC-SA$^2$: $\mathcal{O} \left( \sqrt{\frac{LD}{\epsilon}} \log k + \frac{\sigma_x^2}{\epsilon^2} \log^3 k \right)$ |
| Stoc L-SS NC   | Stationarity        | $\Omega \left( \Delta \sigma_x \epsilon^{-4} \right)$         | $\checkmark$                     | [<d-cite key="arjevani2023lower"></d-cite>, Theorem 1], [<d-cite key="ghadimi2013stochastic"></d-cite>, Cor 2.2]                                           |
| Stoc L-AS NC            | Stationarity        | $\Omega \left( \Delta \sigma_x^2 + 3 \sigma_x \epsilon^{-2} \right)$ | $\checkmark$                     | [<d-cite key="arjevani2023lower"></d-cite>, Theorem 2], [<d-cite key="fang2018spider"></d-cite>, Theorem 1]                          |
| Stoc L-AS IC            | Stationarity        | Unknown | Unknown                     | [<d-cite key="wang2019spiderboost"></d-cite>, Theorem 5]                          |
| NS $L$-Lip $\rho$-WC    | Near-stationarity        | Unknown     | $\mathcal{O} (\epsilon^{-4})$ | [<d-cite key="davis2018stochastic"></d-cite>, Thm 2.1]              |

**Remark:**

1. content

### Case 2-1: SC-SC/SC-C/C-C Deterministic Minimax Optimization

| Problem Type          | Measure | Lower Bound                                             | Upper Bound                           | Reference (LB-UB)                                      |
|-----------------------|---------|-------------------------------------------------|------------------------------|----------------------------------------------------------|
| C-C, bilinear, NS     | Duality Gap        | $\Omega(L / \epsilon)$                          | $\checkmark$                 | [<d-cite key="ouyang2021lower"></d-cite>, Thm 9], [<d-cite key="chambolle2011first"></d-cite>, Thm 1]                                            |
| C-C, general          | Duality Gap        | $\Omega(L D_X D_Y / \epsilon)$                  | $\checkmark$                 | [<d-cite key="xie2020lower"></d-cite>, Thm 3], [<d-cite key="nemirovski2004prox"></d-cite>, Thm 4.1]  |
| SC-C, bilinear, NS    | Duality Gap        | $\Omega(\sqrt{\kappa_x} / \epsilon)$            | $\checkmark$ ($\times$)      | [<d-cite key="ouyang2021lower"></d-cite>, Thm 10], [<d-cite key="chambolle2011first"></d-cite>, Thm 2] $\mathcal{O}(\kappa_x^2 / \sqrt{\epsilon})$ |
| SC-C, general         | Duality Gap        | $\Omega(D_Y \sqrt{L \kappa_x} / \epsilon)$      | $\checkmark$ ($\times$)      | [<d-cite key="xie2020lower"></d-cite>, Thm 2 imply], [<d-cite key="yang2020catalyst"></d-cite>, Sec 3.2] $\tilde{\mathcal{O}}(D \sqrt{L \kappa_x} / \epsilon)$  |
| C-SC, bilinear        | Duality Gap        | ?                                               | $\mathcal{O}(\log \frac{1}{\epsilon})$ | (UB $\neq$ SC-C ?)?, [<d-cite key="du2019linear"></d-cite>, Thm 3.1] |
| C-SC, general         | Duality Gap        | $\Omega(L D_X / \sqrt{\mu_y \epsilon})$         | ?                            | [<d-cite key="xie2020lower"></d-cite>, Thm 2 imply]   |
| SC-SC, bilinear       | Duality Gap        | $\Omega(\sqrt{\kappa_x \kappa_y} \log \frac{1}{\epsilon})$ | $\checkmark$               | [<d-cite key="zhang2022lower"></d-cite>, Thm 3.5], [<d-cite key="chambolle2016ergodic"></d-cite>, Thm 5, PIFO]                                      |
| SC-SC, general        | Duality Gap        | $\Omega(\sqrt{\kappa_x \kappa_y} \log \frac{1}{\epsilon})$ | $\checkmark$ ($\times$)    | [<d-cite key="zhang2022lower"></d-cite>, Thm 4.5], [<d-cite key="wang2020improved"></d-cite>, Thm 3]                                            |
| SC-SC, general        | Duality Gap        | same                                            | $\checkmark$ ($\times$) | [<d-cite key="liang2019interaction"></d-cite>, Thm 1, (last iterate)] $\mathcal{O}(\sqrt{\kappa} \log \frac{1}{\epsilon})$ |
|                       |         |                                                 |                              |                                                          |
| **Note**              |         | LB SC-SC bilinear: [<d-cite key="ibrahim2020linear"></d-cite>, Cor 4] and extension to SCLI framework<d-cite key="arjevani2016lower"></d-cite> |

**Remark:**

1. content

### Case 2-2: SC-SC/SC-C/C-C Finite-sum and Stochastic Minimax Optimization

| Problem Type         | Measure | LB                                         | UB                            | Reference-LB      | Reference-UB                                   |
|----------------------|---------|---------------------------------------------|-------------------------------|-------------------|------------------------------------------|
| C-C, Fin-Sum         | Duality Gap | $\Omega(n + L / \epsilon)$                 | $\times$                      | [<d-cite key="xie2020lower"></d-cite>, Theorem 3, PIFO]     | [<d-cite key="yazdandoost2023stochastic"></d-cite>, Cor 2.1]  $\mathcal{O}(\sqrt{n}/\epsilon)$      |
| C-C, Stoc, SS        | Duality Gap | $\Omega(\epsilon^{-2})$                    | $\checkmark$                  | (Stoc C SS min)                                             | [<d-cite key="juditsky2011solving"></d-cite>, Cor 1]      |
| C-C, Stoc, NS        | Duality Gap | $\Omega(\epsilon^{-2})$                    | $\checkmark$                  | (Stoc C NS min)                                             | [<d-cite key="nemirovski2009robust"></d-cite>, Lemma 3.1]      |
| SC-C, Fin-Sum        | Duality Gap | $\Omega\left(n + \sqrt{n L / \epsilon}\right)$ | $\checkmark$ ($\times$)   | (FS C min)                                                  | [<d-cite key="yang2020catalyst"></d-cite>, Sec 3.2] $\tilde{\mathcal{O}}(\sqrt{n L / \epsilon})$      |
| C-SC, FS bilinear    | Duality Gap | ?                                          | ?                             | ?                                                           | [<d-cite key="du2019linear"></d-cite>, Thm 4.1] $\mathcal{O}(n \log \frac{1}{\epsilon})$      |
| C-SC, FS general     | Duality Gap | $\Omega(n + L / \sqrt{\mu_y \epsilon})$    | ?                             | [<d-cite key="xie2020lower"></d-cite>, Thm 2]               | (implies from SC-C?) |
| SC-SC, Fin-Sum       | Duality Gap | $\Omega\left((n + \kappa) \log \frac{1}{\epsilon}\right)$ | $\checkmark$ ($\times$) | [<d-cite key="xie2020lower"></d-cite>, Thm 1]      | [<d-cite key="palaniappan2016stochastic"></d-cite>, Thm 1] $\mathcal{O}((n + \kappa) \log \frac{1}{\epsilon})$      |
| SC-SC, Stoc, SS      | Duality Gap | $\Omega(\epsilon^{-1})$                    | $\checkmark$                  | (Stoc SC SS min)                                            | [<d-cite key="hsieh2019convergence"></d-cite>, Thm 5, pt. dist.] $\mathcal{O}(\epsilon^{-1})$       |
| SC-SC, Stoc, NS      | Duality Gap | $\Omega(\epsilon^{-1})$                    | $\checkmark$                  | (Stoc SC NS min)                                            | [<d-cite key="yan2020optimal"></d-cite>, Thm 1, in prob.] $\mathcal{O}(\epsilon^{-1})$       |
|                      |         |                                             |                               |                                                             |
| **Note**             |         | UB SC-SC general: [<d-cite key="luo2019stochastic"></d-cite>], [<d-cite key="chavdarova2019reducing"></d-cite>, (cocoercive?)] | |

**Remark:**

1. content

### Case 2-3: NC-SC/NC-C Deterministic Minimax Optimization

**Remark:**

1. content

### Case 2-4: NC-SC/NC-C Finite-sum and Stochastic Minimax Optimization

**Remark:**

1. content

---

## To Have a Better Bound

- bilevel and other special structure
- Last-iterate?
- large stepsize
- Markovian noise
- DRO
- Application-driven: Mix the gap between practice and theory
- Interpolation condition in over-parametrized NN
- Beyond oracle model

---

## Conclusion

content
