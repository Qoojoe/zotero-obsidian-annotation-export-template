# zotero-obsidian-annotation-export
Templates for exporting annotations from Zotero into Obsidian via [Zotero integration](https://github.com/obsidian-community/obsidian-zotero-integration).
Formatting is focused on callouts, to make embedding in other files in Obsidian easier. No AI was used.
# Overview
Exported file will contain the following:
## Properties
Extracts:
- Tags
- Title (becomes searchable in Vault via automatic alias)
- Author(s)
  - Listed as items in property
- Publish date
- Citekey (as filename and property)
- Web source, if available
- ISBN, if available
- DOI, if available
- Local link with which Zotero is opened on entry
- Language
- Related works as Obsidian links
## Text
- Link to entry in Zotero
- Abstract (optional)
- Headers for
	- Linking to other concepts or similar in Vault
	- Summary
	- Criticism
### Annotations
- Formatted into callouts
	- Colours correspond to colour selection in Zotero (RGB values sampled from Zotero with colour picker)
	- Differing symbols based on annotation type (Lucide icons: "highlighter", "underline", and "image")
	- Extraction of images supported
		- Automatically centered (CSS snippet taken from [gautamneeraj](https://forum.obsidian.md/t/align-image/78050))
- Comments, if available
- Annotation tags, if available
	- "Blocked" via code formatting (backtick character) from becoming recognized tags in Obsidian (can be easily unblocked by removing backticks in template)
### Related works
- Works that are marked as related in Zotero are automatically listed at the end of the exported file
	- Corresponding Zotero link is automatically generated
	- Corresponding Obsidian link is generated
		- Will be generated, even if the linked to work is not yet exported into Obsidian (as unresolved link)
# FAQ
- What do I do with these files?
  1. Add the CSS snippet under "Appearance>CSS snippets" by clicking on the "File" symbol and copying the .css in there
  2. Copy the .md files somewhere in your Vault (preferably into a dedicated Templates) folder
  3. Open the options page for Zotero integration and click on "Add Import Format"
  4. Give the Import Format a recognizable name like "Full PDF"
  5. Set the output path (preferably to a dedicated Zotero import folder) and make sure that it ends in "{{citekey}}.md"
  6. Select the template file (Type in the name and it should suggest it to you)
  7. Choose a bibliography style of your liking (or pick "American Psychological Association 7th edition", if you are not sure)
  8. Open the command palette and look for "Zotero Integration" and then the format name you chose
- What is the programming language/template engine?
  - Jinja. Search for "Jinja loops" or similar to learn more about how the looping and if statements are formatted.
- Can I change the colours of the callouts?
  - Yes. The colours are defined at the beginning of the CSS. Simply change them there and all the types of annotation of the same colour will change too.
-  Why are the "headers" of the callouts under the main text?
  - It is closer to the usual structure of citing text in academia. If you wish to disable it, simply delete or comment out the sections in the CSS that have the headers "Paratext under..."
