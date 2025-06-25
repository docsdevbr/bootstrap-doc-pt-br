---
# Copyright (c) 2011-2025 The Bootstrap Authors.

# Documentation licensed under the Creative Commons Attribution 3.0 Unported
# License.
# The original work was translated from English into Brazilian Portuguese.
# https://creativecommons.org/licenses/by/3.0/

layout: docs
title: Translations
description: Links to community-translated Bootstrap documentation sites.
group: about
---

Community members have translated Bootstrap's documentation into various
languages. None are officially supported and they may not always be up-to-date.

{ {< translations.inline >} }
<ul>
{ { range .Site.Data.translations -} }
  <li><a href="{ { .url } }" hreflang="{ { .code } }">{ { .description } } ({ { .name } })</a></li>
{ { end -} }
</ul>
{ {< /translations.inline >} }

**We don't help organize or host translations, we just link to them.**

Finished a new or better translation? Open a pull request to add it to our list.
