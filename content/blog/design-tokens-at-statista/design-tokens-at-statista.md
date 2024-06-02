---
title: How we work with Design Tokens at Statista
description: This is a post on how we work with Design Tokens at Statista.
date: 2024-05-20
draft: true
tags:
  - design tokens
  - design systems
  - design engineering
---

## Preface

[Read this article from Nathan Curtis](https://medium.com/eightshapes-llc/naming-tokens-in-design-systems-9e86c7444676) and understand:

- What are Design Tokens?
- How can they be composed and categorized?
- Every use case is different and there is no silver bullet.

## Establish token system for your company's use case

Start with _generic/primitive_ tokens then create _semantic/system/alias_ tokens and _component/scoped_ tokens if necessary

Raw values: `#0666e5`

Primitive/generic: `blue-500`

Semantic/system/alias: `color-primary`

Component/scoped: `color-button-text-primary`

## Namespace matrix

<div class="table-wrapper">

| Context | Category           | Sub-Category   | Component   | Role          | State         | Surface  |
| :------ | :----------------- | :------------- | :---------- | :------------ | :------------ | :------- |
| theme   | color              | background     | button      | default       | active        | on-light |
| brand   | typography/font \* | text           | form        | base          | hover         | on-dark  |
| system  | \| font-size       | border         | \| input    | primary       | focus         | raised   |
| product | \| font-weight     | letter-spacing | \| checkbox | secondary     | disabled      | lowered  |
|         | \| font-family     | size           | \| select   | info          | pressed       |          |
|         | \| line-height     | fill           | card        | danger        | visited       |          |
|         | \| letter-spacing  | weight         | tooltip     | success       | selected      |          |
|         | spacing/space      | width          | modal       | progress      | checked       |          |
|         | sizing/size        | style          | message     | warning       | unchecked     |          |
|         | z-index/elevation  |                |             | decorative    | indeterminate |          |
|         | border \*          |                |             | subtle        |               |          |
|         | \| color           |                |             | neutral       |               |          |
|         | \| width           |                |             | weak          |               |          |
|         | \| style           |                |             | highlight     |               |          |
|         | border-radius      |                |             | high-contrast |               |          |
|         | shadow \*          |                |             |               |               |          |
|         | \| color           |                |             |               |               |          |
|         | \| blur            |                |             |               |               |          |
|         | \| spread          |                |             |               |               |          |
|         | \| direction       |                |             |               |               |          |
|         | motion             |                |             |               |               |          |
|         | timing/time        |                |             |               |               |          |

\* Composite tokens are a combination of multiple values, also known as sub-values.

</div>

## Token types

_color_, _dimension_, _font-family_, _font-weight_, _duration_, _cubic-bézier_, _number_, additional types tbd. (_font-style_, _percentage/ratio_, _file_)

## Do's and Don'ts

Do: use alias tokens `size-100` --> `space-padding-xs` --> `spacing-desktop.small`

Don't: use exact values `font-size-12`

- These values could change and are not flexible
- Font-size 12 is not true anymore if a user increases their default font-size

## Think about a namespace that suits your system and users

If designers and developers are used to terms like _muted_ for text that stands back, then choose that instead of other terms like _neutral_ or _weak_.

Try to figure out if you can use a scaling system for sizing or typography, this minimizes complexity and maintenance and enables you to re-use generic/alias tokens

Decide how you want work work with scales:

- T-Shirt sizes are more well-known but also limited (you probably don't want to work with 3xs or 5xl)
- Numbers are more flexible but less descriptive
- Emphasis like _low_, _medium_ or _high_ are very descriptive but also very limited
  - _dropdown_, _modal_, _sticky_ is even more descriptive
- For timing e.g. _instant_, _slow_, _medium_ or _fast_

## Put tokens into json format

According to [DTCG](https://design-tokens.github.io/community-group/format/)
you can try to use tools such as:

- Figma variables
- Tokens Studio (Figma plugin)
- Zeroheight
- Supernova
- Knapsack

## Tooling

Use [style dictionary](https://amzn.github.io/style-dictionary/#/) to convert json into output format of choice

- JS for CSS-in-JS or Tailwind CSS
- CSS custom-props
- SCSS
