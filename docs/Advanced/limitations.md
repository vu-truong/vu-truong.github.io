---
share: true
title: Limitations
---

- Obviously, not all Obsidian plugins will work. Only Obsidian plugins that are provided with an API can be converted, such as Dataview (converted to simple markdown) for example.
- Mkdocs and Material Mkdocs do not support inline tags, and you will lose links in these tags. See [[snippets and tools#Custom tags attributes|Custom tags attributes]] for more information. You can move your tags in the frontmatter to keep them, using the plugin.
- Nested tags are not supported.
- File embed doesn't work without proper support in your blog solution. For Mkdocs, the template is provided with the plugin, but you need to search for other solutions for other blog solutions. See [[Per files settings]] for solution about embed links.