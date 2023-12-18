
Readwise and Obsidian Sync

I want the same system as I can have with Zotero. I want to be able to add stuff to a Readwise folder per item. I don't want an auto sync. 
- I think I would only want that in Notion. 

## Readwise Templates

[Source](https://help.readwise.io/article/126-how-can-i-customize-the-readwise-to-obsidian-export#file-name)

Guide to what is possible in Readwise -> Obsidian Templates and how to do it. 

You can customize a variety of elements including:

- [YAML front matter](https://help.obsidian.md/Advanced+topics/YAML+front+matter)
- Page title
- Metadata (such as author, URL, category, title, cover image)
- Highlight header (inserted whenever new highlights are added)
- Highlights themselves (eg inclusion of links to original, tags, notes, etc)
- Sync notifications (a new entry in Obsidian each time the Readwise plugin runs)

At a high level, each component of the export has a "template" using the [[Jinja2]] templating language. The explanations below should illustrate how customization works, and give some useful examples.

To modify the title: 

```
# {{title}} (Highlights)
```

It is also possible to add properties but I am not interested in that right now. 


Highlight Header

A common use case in tools for thought such as Roam Research and Obsidian is to backlink the date in this header to your Daily Notes page. To make this work for yourself, you'll need to format the {{date}} variable to match your Daily Notes formatting and then double brackets to the template in Readwise.

- This is useful if I switch/start Daily Notes
	- [ ] start daily notes that you don't have to use till later

Highlights

The highlights themselves are formatted: 

```
- {{ highlight_text }}{% if highlight_location and highlight_location_url %} ([{{highlight_location}}]({{highlight_location_url}})){% elif highlight_location %} ({{highlight_location}}){% endif %}{% if highlight_tags %}
    - Tags: {% for tag in highlight_tags %}[[{{tag}}]] {% endfor %}{% endif %}{% if highlight_note %}
    - Note: {{ highlight_note }}{% endif %}
```


Links

How does the Readwise to Obsidian export integration work? - Readwise
https://help.readwise.io/article/125-how-does-the-readwise-to-obsidian-export-integration-work

Obsidian Export | Readwise
https://readwise.io/export/obsidian/preferences

How can I customize the Readwise to Obsidian Export? - Readwise
https://help.readwise.io/article/126-how-can-i-customize-the-readwise-to-obsidian-export#file-name

Moment.js | Docs
https://momentjs.com/docs/#/displaying/format/

