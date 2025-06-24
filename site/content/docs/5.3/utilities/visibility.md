---
# Copyright (c) 2011-2025 The Bootstrap Authors.

# Code licensed under the MIT License.
# Documentation licensed under the Creative Commons Attribution 3.0 Unported License.
# The original work was translated from English into Brazilian Portuguese.
# https://creativecommons.org/licenses/by/3.0/

layout: docs
title: Visibility
description: Control the visibility of elements, without modifying their display, with visibility utilities.
group: utilities
---

Set the `visibility` of elements with our visibility utilities. These utility
classes do not modify the `display` value at all and do not affect layout –
`.invisible` elements still take up space in the page.

{ { < callout warning }}
Elements with the `.invisible` class will be hidden *both* visually and for
assistive technology/screen reader users.
{ { < /callout }}

Apply `.visible` or `.invisible` as needed.

```html
<div class="visible">...</div>
<div class="invisible">...</div>
```

```scss
// Class
.visible {
  visibility: visible !important;
}
.invisible {
  visibility: hidden !important;
}
```

## CSS

### Sass utilities API

Visibility utilities are declared in our utilities API in
`scss/_utilities.scss`. [Learn how to use the utilities API.](api.md#using-the-api)

{ { < scss-docs name="utils-visibility" file="scss/_utilities.scss" }}
