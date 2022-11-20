{% assign childdirs = "" | split: "," %}
{% assign childpages = "" | split: "," %}
{% for cpage in site.pages %}{% if cpage.title != nil %}
    {% assign subpath = cpage.dir | prepend: "/" | split: "/" | pop | join: "/" %}
    {% if subpath == page.dir and cpage.name == "index.md" %}
        {% assign childdirs = childdirs | push: cpage %}
    {% elsif cpage.dir == page.dir and cpage.name != "index.md" %}
        {% assign childpages = childpages | push: cpage %}
    {% endif %}
{% endif %}{% endfor %}
{% for cpage in childdirs %}
* [{{ cpage.title }}/]({{ cpage.url }})
{%- endfor %}
{% for cpage in childpages -%}
* [{{ cpage.title }}]({{ cpage.url }})
{% endfor %}
