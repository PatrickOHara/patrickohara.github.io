---
title: "Decision Making under the Exponential Family: Distributionally Robust Optimisation with Bayesian Ambiguity Sets"
collection: publications
permalink: /publication/2025-01-dro-bas-kl
excerpt: ''
date: 2025-01-29
venue: 'Under review at ICML'
paperurl: 'https://arxiv.org/abs/2411.16829'
citation: "Dellaporta*, C., O'Hara*, P., & Damoulas, T. (2024). Decision Making under the Exponential Family: Distributionally Robust Optimisation with Bayesian Ambiguity Sets. arXiv preprint arXiv:2411.16829."
---

**Abstract**: Distributionally Robust Optimisation (DRO) protects risk-averse decision-makers by considering the worst-case risk within an ambiguity set of distributions based on the empirical distribution or a model. To further guard against finite, noisy data, model-based approaches admit Bayesian formulations that propagate uncertainty from the posterior to the decision-making problem. However, when the model is misspecified, the decision maker must stretch the ambiguity set to contain the data-generating process (DGP), leading to overly conservative decisions. We address this challenge by introducing DRO with Robust, to model misspecification, Bayesian Ambiguity Sets (DRO-RoBAS). These are Maximum Mean Discrepancy ambiguity sets centred at a robust posterior predictive distribution that incorporates beliefs about the DGP. We show that the resulting optimisation problem obtains a dual formulation in the Reproducing Kernel Hilbert Space and we give probabilistic guarantees on the tolerance level of the ambiguity set. Our method outperforms other Bayesian and empirical DRO approaches in out-of-sample performance on the Newsvendor and Portfolio problems with various cases of model misspecification.