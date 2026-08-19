---
tags:
  - zotero-import{% for tag in tags -%}{% if tag.tag %}
  - {{tag.tag|replace(" ", "_")}}{% endif %}{% endfor %}
aliases:
  - "{{title}}"
author:
{% for creator in creators %}- "{{creator.lastName}}, {{creator.firstName}}"
{% endfor -%}
title: "{{title}}"
released: {{date | format("YYYY-MM-DD")}}
citekey: {{citekey}}
relevant: {% for relation in relations %}
- "[[{{relation.citekey}}|{{relation.title}}]]"{% endfor %}{% if DOI %}
doi: "https://doi.org/{{DOI}}"{% endif %}
{% if ISBN -%}
isbn: "{{ISBN}}"{% endif %}
source: "{{url}}"
local-link: "{{desktopURI}}"
language: "{{language}}"
status: "Read"
---
## [{{title}}]({{desktopURI}})

{% if abstractNote %}> [!abstract]- 
> {{abstractNote|replace("\n", "\n >")}}

{% endif %}> [!Cite] Citation
> {{bibliography}}
# Linked to
- 
# Major take-aways
- 
# Criticism
- 
{% if markdownNotes %}# Notes
{%- for note in notes |sort(attribute="dateAdded") %}
> [!note] **[Note]({{note.desktopURI}}) for:**  {{authors}}: "{{title}}" ({{date | format("YYYY")}})
> {{note.note|replace("\n", "\n> ")}}
{% endfor %}
{%- endif -%}
# Excerpts
{% for annotation in annotations -%}
{%- if annotation.annotatedText -%}
> [!{{annotation.type}}-{{annotation.colorCategory}}] {{authors}}: "{{title}}" ({{date | format("YYYY")}})
{%- if annotation.pageLabel -%}
, p. [{{annotation.pageLabel}}](zotero://open-pdf/library/items/{{annotation.attachment.itemKey}}?page={{annotation.page}}&annotation={{annotation.id}}) {% endif %}
> {% if annotation.color %}{{annotation.annotatedText|safe|replace("\n", "\n >")}} {% else %}{{annotation.type | capitalize}} {% endif %}{%- endif %}{%- if annotation.imageRelativePath %}> [!pic-{{annotation.colorCategory}}] **Image from:** {{authors}}: "{{title}}" ({{date | format("YYYY")}}), p. [{{annotation.pageLabel}}](zotero://open-pdf/library/items/{{annotation.attachment.itemKey}}?page={{annotation.page}}&annotation={{annotation.id}})
>![[{{annotation.imageRelativePath}}|center]]{%- endif %}{% if annotation.comment %}
- **Comment:** *{{annotation.comment}}*{% endif %}
{% if annotation.hashTags %}- **Tags:** {{annotation.hashTags|replace(" ", "_")|replace(",_", " ")}}
{% endif %}
{% endfor -%}
# Related works
- {% for relation in relations | selectattr("bibliography") %}{{relation.bibliography}}
   - *[Open in Zotero]({{relation.select}})
   - **[[{{relation.citekey}}|Obsidian link]]**{% if not loop.last %}
- {% endif%}{% endfor %}

%% Version 1.0 - Bulleted %%
