Dump of Templates from random places online

[Forum Discussion](https://forum.obsidian.md/t/zotero-integration-import-templates/36310/66?page=6)

### Samples

```
{% persist "annotations" %}
{% set annotations = annotations | filterby("date", "dateafter", lastImportDate) -%}
{% if annotations.length > 0 %}
*Imported on {{importDate | format("YYYY-MM-DD HH:mm")}}*

{% for color, annotations in annotations | groupby("color") -%}

### {{heading(color)}} %% fold %%
{% for annotation in annotations -%}
{%- if annotation.imageRelativePath %}
> [!cite]+ Image [(p. {{annotation.pageLabel}})](zotero://open-pdf/library/items/{{annotation.attachment.itemKey}}?page={{annotation.pageLabel}}&annotation={{annotation.id}})
> ![[{{annotation.imageRelativePath}}]]{% if annotation.hashTags %}
> {{annotation.hashTags}}{% endif %}{%- if (annotation.comment or []).indexOf("todo ") !== -1 %}
> - [ ] **{{annotation.comment | replace("todo ", "")}}**{% else %}
> **{{annotation.comment}}**{%- endif -%}

{% elif (annotation.comment or []).indexOf("todo ") !== -1 %}
{% if not annotation.annotatedText %} [(p. {{annotation.pageLabel}})](zotero://open-pdf/library/items/{{annotation.attachment.itemKey}}?page={{annotation.pageLabel}}&annotation={{annotation.id}}){% else %}
- {{calloutCharacter(annotation.color)}} {{annotation.annotatedText | nl2br}} [(p. {{annotation.pageLabel}})](zotero://open-pdf/library/items/{{annotation.attachment.itemKey}}?page={{annotation.pageLabel}}&annotation={{annotation.id}}) {% if annotation.hashTags %}{{annotation.hashTags}}{% endif %}
	-  [ ] **{{annotation.comment | replace("todo ", "")}}**{% endif %}
{% elif annotation.comment %}
- {{calloutCharacter(annotation.color)}} {{annotation.annotatedText | nl2br}} [(p. {{annotation.pageLabel}})](zotero://open-pdf/library/items/{{annotation.attachment.itemKey}}?page={{annotation.pageLabel}}&annotation={{annotation.id}}) {% if annotation.hashTags %}{{annotation.hashTags}}{% endif %}
	- **{{annotation.comment}}** {% if not annotation.annotatedText %} [(p. {{annotation.pageLabel}})](zotero://open-pdf/library/items/{{annotation.attachment.itemKey}}?page={{annotation.pageLabel}}&annotation={{annotation.id}}){% else %}{% endif %}
{%- elif annotation.annotatedText %}
- {{calloutCharacter(annotation.color)}} {{annotation.annotatedText | nl2br}} [(p. {{annotation.pageLabel}})](zotero://open-pdf/library/items/{{annotation.attachment.itemKey}}?page={{annotation.pageLabel}}&annotation={{annotation.id}}) {% if annotation.hashTags %}{{annotation.hashTags}}{% endif %}
{%- endif -%}{%- endfor %}

{% endfor -%}
{% endif %}
{% endpersist %}
```

```
---
{% if title %}Title: "{{title}}"{% endif %}
Authors: {{authors}}{{directors}}
{% if publicationTitle %}Publication: "{{publicationTitle}}"{% endif %}
{% if date %}Date: {{date | format("YYYY-MM-DD")}}{% endif %}
citekey: {{citekey}}
tags: {{hashTags}}
---
## {{title}}
**Bibliographie :** {{bibliography}}

**Lien de la publication :** {{url}}

**Lien Zotero :** {{pdfZoteroLink}}

**Tags :** {{hashTags}} 

>[!abstract]+
>*« {{abstractNote}} »*

{% for annotation in annotations -%}
>[!Annotation|{{annotation.color}}]+ 
>{%- if annotation.annotatedText -%}*« {{annotation.annotatedText}} »*([{{annotation.page}}](zotero://open-pdf/library/items/{{annotation.attachment.itemKey}}?page={{annotation.page}}&annotation={{annotation.id}})){% endif %}{% if annotation.imageRelativePath %}![[{{annotation.imageRelativePath}}]]{% endif %}{% if annotation.comment %} 
>
>{{annotation.comment}}{%- endif %}

{% endfor %}
```

#### Image

![[Zotero Import Templates-img-2311081845.png]]


```yaml
last-reviewed:
---
## {{title}} 
> [!info] 
> - **Abstract:** {{abstractNote}} 
> - **Sources**: [online]({{uri}}) [local]({{desktopURI}}) {%- for attachment in attachments | filterby("path", "endswith",".pdf") %} [pdf](file:///{{attachment.path | replace(" ","%20")}}) {% if loop.last %}{% endif %}{%- endfor %}
> - **Bibliography**: {{bibliography}}
> - **Cite Key:** [[@{{citekey}}]] 
 {%- if hashTags %}
> - **Tags:** {{hashTags}} 
{%- endif %}

>[!Personal Summary] 

## Annotations 
{% for annotation in annotations -%}{%- if annotation.annotatedText -%}{% if 'Purple' in annotation.colorCategory %} 
##### {{annotation.annotatedText | escape }}{% else %} 
<mark class="customZot-{% if annotation.color %}{{annotation.colorCategory}} {% endif %}">{{annotation.annotatedText | escape }}</mark> ([{{annotation.page}}](zotero://open-pdf/library/items/{{annotation.attachment.itemKey}}?page={{annotation.page}}&annotation={{annotation.id}}))
{% endif %}{%- endif %} {% if annotation.imageRelativePath %} ![[{{annotation.imageRelativePath}}]] {% endif %}{% if annotation.comment %}
>*{{annotation.comment}}* 
{% endif %}{% endfor -%}
```

```
---
year: {{date | format ("YYYY")}}
tags: research
authors: {{authors}}

Abstract:  {{abstractNote}}
---

### {{title}}
{{pdfZoteroLink}}

### Notes
{% for annotation in annotations -%}{%- if annotation.annotatedText -%}{% if 'Red' in annotation.colorCategory %} 
##### {{annotation.annotatedText | escape }}{% else %}
<mark class="customZot-{% if annotation.color %}{{annotation.colorCategory}} {% endif %}">{{annotation.annotatedText | escape }}</mark> ([{{annotation.page}}](zotero://open-pdf/library/items/{{annotation.attachment.itemKey}}?page={{annotation.page}}&annotation={{annotation.id}}))

{% endif %}{%- endif %} {% if annotation.imageRelativePath %} ![[{{annotation.imageRelativePath}}]]{% endif %}{% if annotation.comment %} 
>{{annotation.comment}}
{% endif %}{% endfor -%}
```

```
> [!Cite] {{bibliography}}
> 
> [!Synthesize] **Contribution**::
> 
> [!Metadata] {%- for creator in creators %} {%- if creator.name == null %} **{{creator.creatorType | capitalize}}**:: {{creator.lastName}}, {{creator.firstName}}</br> {%- endif -%} {%- if creator.name %}**{{creator.creatorType | capitalize}}**:: {{creator.name}}</br> {%- endif -%} {%- endfor %} **Title**:: {{title}} **Year**:: {{date | format("YYYY")}} **Citekey**:: @{{citekey}} {%- if itemType %}**itemType**:: {{itemType}}{%- endif %} {%- if itemType == "journalArticle" %}**Journal**:: _{{publicationTitle}}_ {%- endif %} {%- if volume %}**Volume**:: {{volume}} {%- endif %} {%- if issue %}**Issue**:: {{issue}} {%- endif %} {%- if itemType == "bookSection" %}**Book**:: {{publicationTitle}} {%- endif %} {%- if publisher %}**Publisher**:: {{publisher}} {%- endif %} {%- if place %}**Location**:: {{place}} {%- endif %} {%- if pages %} **Pages**:: {{pages}} {%- endif %} {%- if DOI %}**DOI**:: {{DOI}} {%- endif %} {%- if ISBN %}**ISBN**:: {{ISBN}} {%- endif %}
> 
> [!LINK] {%- for attachment in attachments | filterby("path", "endswith", ".pdf") %} [{{attachment.title}}](file://{{attachment.path | replace(" ", "%20")}}) {%- endfor -%}.
> 
> [!Abstract] {%- if abstractNote %} {{abstractNote}}{%- endif %}
> 
> [!important] {%- set important = annotations | filterby("comment", "startswith", "important") -%}{%- if important.length > 0 %} {%- for annotation in important -%} {%- if annotation.annotatedText %} - {{annotation.annotatedText | nl2br}}{%- endif -%}
> 
> {%- if annotation.imageRelativePath %} - ![[{{annotation.imageRelativePath}}]]{%- endif %} [page {{annotation.page}}](file://{{annotation.attachment.path | replace(" ", "%20")}}) {%- endfor -%} {%- endif %}

{%- if annotations.length %}

## Annotations

{%- endif %}

{% persist "annotations" %} {%- macro calloutHeader(type, color) -%} {%- if type == "highlight" -%} <mark style="background-color: {{color}}">Highlight</mark> {%- endif -%} {%- if type == "text" -%}Note{%- endif -%} {%- endmacro -%}

{%- set annots = annotations | filterby("date", "dateafter", lastExportDate) -%} {%- if annots.length > 0 %}

### Exported: {{exportDate | format("YYYY-MM-DD HH:mm")}}

{% for annot in annots -%}

> [!Note] {{calloutHeader(annot.type, annot.color)}}</br></br> {%- if annot.annotatedText -%} {{annot.annotatedText | nl2br}}{%- endif -%} {%- if annot.imageRelativePath %} >![[{{annot.imageRelativePath}}]]{%- endif %} {%- if annot.comment %}
> 
> > - {{annot.comment | nl2br}}{%- endif %} [page {{annot.page}}](file://{{annot.attachment.path | replace(" ", "%20")}}) [[{{annot.date | format("YYYY-MM-DD HH:mm")}}]]

{% endfor -%} {% endif -%} {% endpersist %}
```


```
## {{title}}

### Formatted Bibliography

{{bibliography}}
{% if abstractNote %}

### Abstract

{{abstractNote}}
{% endif %}
```


```
{% for annotation in annotations %}
{% if annotation.annotatedText %}

> {{annotation.annotatedText}}
> {% endif %}
> {% if annotation.comment %}
> {{annotation.comment}}
{% endif %}
{% endfor %}
```

**for loop**

```
{% for annotation in annotations %}
...do something...
{% endfor %}
```

```
{% for a in annotations %}
{{a.annotatedText}}
{{a.color}}
{{a.colorCategory}}
{{a.page}}
...ect...
{% endfor %}
```

Prevent overriding when re-importing

```
## {{title}}

### Notes
{% persist "notes" %}
{% endpersist %}
```

Add only the annotations that are new from the last import

```
{% persist "annotations" %}
{% set newAnnotations = annotations | filterby("date", "dateafter", lastImportDate) %}
{% if newAnnotations.length > 0 %}

### Imported: {{importDate | format("YYYY-MM-DD h:mm a")}}

{% for a in newAnnotations %}
> {{a.annotatedText}}
{% endfor %}

{% endif %}
{% endpersist %}
```

Not sure how this works

![[Zotero Import Templates-img-2311081843.png]]

### Zotero Highlighting CSS

```css
.customZot-Yellow {
    background-color: rgba(255, 204, 0, 0.212) !important;
}

.customZot-Green {
    background-color: rgba(0, 255, 47, 0.215) !important;
}

.customZot-Blue {
    background-color: rgba(0, 0, 255, 0.187) !important;
}

.customZot-Purple {
    background-color: purple !important;
}
```

```css
/* Red */
.callout[data-callout-metadata="#ff6666"] {
    --callout-color: 205, 52, 92;
}

/* Green */
.callout[data-callout-metadata="#5fb236"] {
    --callout-color: 114, 162, 100;
}

/* Blue */
.callout[data-callout-metadata="#2ea8e5"] {
    --callout-color: 52, 82, 255;
}

/* Purple */
.callout[data-callout-metadata="#a28ae5"] {
    --callout-color: 157, 131, 242;
}

/* Orange */
.callout[data-callout-metadata="#f19837"] {
    --callout-color: 244, 164, 96;
}

/* Yellow */
.callout[data-callout-metadata="#ffd400"] {
    --callout-color: 255, 236, 0;
}

/* Magenta */
.callout[data-callout-metadata="#e56eee"] {
    --callout-color: 255, 33, 255;
}

/* Gray */
.callout[data-callout-metadata="#aaaaaa"] {
    --callout-color: 152, 152, 152;
}

.callout-icon {
    display: none;
}
```
