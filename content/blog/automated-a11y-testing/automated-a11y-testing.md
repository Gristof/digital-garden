---
title: Automated Accessiblity Testing
description: This is a post on automated accessibility testing with unit tests and GitHub actions.
date: 2024-05-20
draft: true
tags:
  - a11y
  - ci
  - testing
  - vitest
---

- multiple layers like layering cheese
- first layer: on IDE level like axe Accessibility Linter from Deque Systems or eslint plugins
- second layer: CI (e.g. GitHub actions) or integration tests (e.g. playwright)
- third layer: unit tests (e.g. vitest)
- fourth layer: manual testing
  - [axe devtools](https://chromewebstore.google.com/detail/axe-devtools-web-accessib/lhdoppojpmngadmnindnejefpokejbdd)
  - [WAVE evaluation tool](https://chromewebstore.google.com/detail/wave-evaluation-tool/jbbplnpkjmmeebjpijfedlgcdilocofh)
  - [IBM Equal Access](https://chromewebstore.google.com/detail/ibm-equal-access-accessib/lkcagbfjnkomcinoddgooolagloogehp)
  - [Accessibility Insights](https://chromewebstore.google.com/detail/accessibility-insights-fo/pbjjkligggfmakdaogkfomddhfmpjeni)
