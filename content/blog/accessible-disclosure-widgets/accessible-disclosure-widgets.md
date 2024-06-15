---
title: Make disclosure widgets accessible
date: 2024-06-10
tags:
  - a11y
  - ui engineering
draft: true
---

## Preface

I was tempted to call this post something like _Make dropdowns accessible_,
but then I recalled a certain <a href="https://adrianroselli.com/2020/03/stop-using-drop-down.html" target="_blank">
article by Adrian Roselli</a> pointing out that the term _dropdown_ is too universal.
Instead what I want to describe is a <a href="https://adrianroselli.com/2019/06/link-disclosure-widget-navigation.html" target="_blank">Disclosure Widget</a>.

Obviously I could have just linked the aforementioned article for future reference and call it
a day, but I want a write-down for myself to solidify the topic.

## Example

So let's imagine we want to create a navigation bar, that contains a link to
another page, but also some hidden links underneath that we want to toggle.

Here is what that would look like:

```html
<header>
	<nav aria-label="primary">
		<ul>
			<li>
				<a href="/services" id="item1" aria-current="page">Services</a>
				<button
					aria-controls="subItem1"
					aria-expanded="false"
					aria-labelledby="item1"
					onclick="toggleSubNav()"
				>
					<span class="sr-only">Show</span>
					<svg>[…]</svg>
				</button>
				<ul id="subItem1" style="display:none;">
					[…]
				</ul>
			</li>
			[…]
		</ul>
	</nav>
</header>
```

## Behavior

In the example above we can use the link just like a regular link, that goes to a new page. If we want to open the submenu, we use the button next to it. In many cases websites put the action of opening a submenu on the link. In these cases the link becomes somewhat of a button-link. I think this is one reason why many people are confused about when to use links and when buttons. If you prefer a cleaner design or less tab stops, consider using a button and move the link into the submenu as the first entry.

## Explanation

The actual top level navigation link has the following attributes that are worth pointing out:

- `id` important for the button to create a reference to what it actually toggles
- `aria-current="page"` indicated the currently visited page

The button, which toggles the submenu:

- `id` optional, but can e useful for creating the JavaScript function
- `aria-controls` uses the `id` of the menu that is being toggled visible
- `aria-expanded` toggles `true` and `false` depending on the visibility of the submenu
- `aria-labelledby` uses the `id` of the link to enhance the label _Show_ or _Hide_ with what it actually toggles. E.g. _Show Services_

The submenu list element:

- `id` is used by the `aria-controls` attribute of the button
- `style` hides the submenu initially

### Some additional remarks

- The button has no visible text label, therefore it contains a `span` element which has the class `.sr-only` that hides it from the user but makes it accessible to assistive technology.
- The SVG inside of the button is rotated 180 degrees when the menu opens.
- The button label needs to change to _Hide_ when the menu is open.
- Both hitting "Escape" as well es clicking outside of the submenu should close it.
