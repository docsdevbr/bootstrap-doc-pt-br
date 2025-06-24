---
# Copyright (c) 2011-2025 The Bootstrap Authors.

# Code licensed under the MIT License.
# Documentation licensed under the Creative Commons Attribution 3.0 Unported License.
# The original work was translated from English into Brazilian Portuguese.
# https://creativecommons.org/licenses/by/3.0/

layout: docs
title: Visually hidden
description: Use these helpers to visually hide elements but keep them accessible to assistive technologies.
group: helpers
aliases: "/docs/5.3/helpers/screen-readers/"
---

Visually hide an element while still allowing it to be exposed to assistive
technologies (such as screen readers) with `.visually-hidden`. Use
`.visually-hidden-focusable` to visually hide an element by default, but to
display it when it's focused (e.g. by a keyboard-only user).
`.visually-hidden-focusable` can also be applied to a container–thanks to
`:focus-within`, the container will be displayed when any child element of the
container receives focus.

{ {< example >} }
<h2 class="visually-hidden">Title for screen readers</h2>
<a class="visually-hidden-focusable" href="#content">Skip to main content</a>
<div class="visually-hidden-focusable">A container with a <a href="#">focusable element</a>.</div>
{ {< /example >} }

Both `visually-hidden` and `visually-hidden-focusable` can also be used as
mixins.

```scss
// Usage as a mixin

.visually-hidden-title {
  @include visually-hidden;
}

.skip-navigation {
  @include visually-hidden-focusable;
}
```
