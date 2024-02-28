---
date: 2023-05-25
comments: true
tags: [Template]
title: "[SYNC TEMPLATE v2.1.0]: CSS Class"
description: "Adding CSS class to the template with a new Jinja Template called css_class.html"
authors:
    - lisandra-dev
categories:
    - Template
---

Hello everyone!

I'm excited to share an idea I had and implemented a way to use `cssClass` (similar to Obsidian) on the website!

To achieve this, I have created a new template called [`css_class.html`](https://github.com/ObsidianPublisher/sync_template/blob/main/overrides/partials/css_class.html).

```html
{% if page.meta %}
    {% if page.meta["cssClass"] and page.meta["cssClass"]|length > 0 %}
        {% if page.meta["cssClass"] is iterable %}
            {% for cssClass in page.meta["cssClass"] %}
                <script>
                    document.body.classList.add('{{ cssClass }}');
                    console.log('Added class {{ cssClass }} to body on page {{ page.title }}');
                </script>
            {% endfor %}
        {% else %}
            <script>
                document.body.classList.add('{{ page.meta["cssClass"] }}');
                console.log('Added class {{ page.meta["cssClass"] }} to body on page {{ page.title }}');
            </script>
        {% endif %}
    {% endif %}
{% endif %}
```

I have made an update to the [`main.html`](https://github.com/ObsidianPublisher/sync_template/blob/14d60ec803e2670b0494d2c4cd122446be9517c3/overrides/main.html#L25) file by adding the following:

```html
{% include "partials/css_class.html" %}
```

The new template will now check the metadata key `cssClass` and add the corresponding CSS class to the body of the page.

> [!note]
> The `cssClass` value can be either an array or a simple string.

Please make sure to synchronize your template with the latest release of [sync_template](https://github.com/ObsidianPublisher/sync_template) (`v2.1.0` for this update!).