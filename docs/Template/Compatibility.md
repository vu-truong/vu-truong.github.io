---
title: Compatibility of publishing solution
---


# Netlify

> [!success] Pros
> - No need to use a `gh-pages` branch

> [!missing] Cons
> - Limited to 300/min/build per month
> - Limited to python 3.8 (in EOL in the end of the year)
> - Doesn't allow private repo (except with a paid plan)
> - Limited options

> [!warning] Python 3.8
> `obsidiantools` package, allowing to create the [[customization#Graph view|graph]], ended support with this version.
> In conclusion, the graph created won't be accurate.
> Moreover, some plugins can end the support with it.

---

# GitHub Pages

> [!success] Pros
> - Support all python version
> - A lot of options (as you can create your own workflow)

> [!missing] Cons
> - Doesn't allow private repo
> - Complicated to use & understand.

---

# Vercel

> [!warning]
> For the moment, Vercel is not supported : Python is compiled without `sqlite3`, and the graph generation use a tool that use it.
> This absence concludes to a build fail.
> You can use it if you don't use the graph view with setting the obsidian graph generation to `false` in the `mkdocs.yml` file.

> [!info] Check [[advanced_workflow|advanced]] for more information on how to setup a better workflow within these two website.


