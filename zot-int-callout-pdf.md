---
tags:
  - zotero-import{% for tag in tags -%}{% if tag.tag %}
  - {{tag.tag}}{% endif %}{% endfor %}
aliases:
  - "{{title}}"
author:
{% for creator in creators %}- "{{creator.lastName}}, {{creator.firstName}}"
{% endfor -%}
title: "{{title}}"
Released: {{date | format("YYYY-MM-DD")}}
Citekey: {{citekey}}
relevant: {% for relation in relations %}
- "[[{{relation.citekey}}|{{relation.title}}]]"{% endfor %}{% if DOI %}
DOI: "https://doi.org/{{DOI}}"{% endif %}
{% if ISBN -%}
ISBN: "{{ISBN}}"{% endif %}
source: "{{url}}"
Local link: "{{desktopURI}}"
language: "{{language}}"
Status: "Read"
---
## [{{title}}]({{desktopURI}})

{% if abstractNote %}> [!abstract]- 
> {{abstractNote}}

{% endif %}> [!Cite] Citation
> {{bibliography}}
# Linked to
- 
# Major take-aways
- 
# Criticism
- 
# Notes & excerpts
{% for annotation in annotations -%}
{%- if annotation.annotatedText -%}
> [!{{annotation.type}}-{{annotation.colorCategory}}] {{authors}}: "{{title}}" ({{date | format("YYYY")}}), p. [{{annotation.pageLabel}}](zotero://open-pdf/library/items/{{annotation.attachment.itemKey}}?page={{annotation.page}}&annotation={{annotation.id}})
> {% if annotation.color %}{{annotation.annotatedText | safe}} {% else %}{{annotation.type | capitalize}} {% endif %}{%- endif %}{%- if annotation.imageRelativePath %}> [!pic-{{annotation.colorCategory}}] **Image from:** {{authors}}: "{{title}}" ({{date | format("YYYY")}}), p. [{{annotation.pageLabel}}](zotero://open-pdf/library/items/{{annotation.attachment.itemKey}}?page={{annotation.page}}&annotation={{annotation.id}})
>![[{{annotation.imageRelativePath}}|center]]{%- endif %}{% if annotation.comment %}
- **Comment:** *{{annotation.comment}}*{% endif %}
{% if annotation.allTags %}- **Tags:** `#{{annotation.allTags}}`
{% endif %}
{% endfor -%}
# Related works
- {% for relation in relations | selectattr("bibliography") %}{{relation.bibliography}}
   - *[Open in Zotero]({{relation.select}})
   - **[[{{relation.citekey}}|Obsidian link]]**{% if not loop.last %}
- {% endif%}{% endfor %}
