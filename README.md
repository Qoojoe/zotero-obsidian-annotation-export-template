# zotero-obsidian-annotation-export
Templates for exporting annotations from Zotero into Obsidian via [Zotero integration](https://github.com/obsidian-community/obsidian-zotero-integration). Tested with PDF and EPUB.
Formatting is focused on callouts, to make embedding in other files in Obsidian easier. Some influence was taken from [Albialy's template](https://forum.obsidian.md/t/my-zotero-annotation-template-that-works/51662) (Thank you!). No AI was used.
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
- Ready to copy citation in the style of your choosing
- Headers for
	- Linking to other concepts or similar in Vault
	- Summary
	- Criticism
### Attached notes
- Notes, if available, that have been attached to a work as whole in Zotero will be imported with formatting intact
	- Sorted by creation date (Earliest to latest) 
### Annotations
- Formatted into callouts
	- Colours correspond to colour selection in Zotero (RGB values sampled from Zotero with colour picker)
	- Differing symbols based on annotation type (Lucide icons: "highlighter", "underline", and "image")
	- Extraction of images supported
		- Automatically centered (CSS snippet taken from [gautamneeraj](https://forum.obsidian.md/t/align-image/78050))
  	- Formatting error with line breaks in EPUB annotation gets automatically corrected
- **Page numbers are functioning links that will open the corresponding section in Zotero**
	- Omitted automatically if the annotations were made in an EPUB (due to lack of static pages)
- Comments, if available
	- Formatted as nested callout (Default is collapsed, which can be opened by clicking on the ">" symbol 
- Annotation tags, if available
### Related works
- Works that are marked as related in Zotero are automatically listed at the end of the exported file
	- Corresponding Zotero link is automatically generated
	- Corresponding Obsidian link is generated
		- Will be generated, even if the linked to work is not yet exported into Obsidian (as unresolved link)
# Customization options
- Colours of the callouts
	- Open the CSS file and there at the top you will find how the colours are defined (in RGB) for the rest of the CSS style.
- Collapsible comment options
- Tag deactivation
	- Don't want tags on annotations being recognized by Obsidian? Simply add a backtick "\`" before `#{{annotation.allTags}}` and the tags will be visible, but not recognized by Obsidian.
# FAQ
- What do I do with these files?
  1. Make sure that "Zotero Integration" is installed in Obsidian and ["Better BibTeX for Zotero"](https://github.com/retorquere/zotero-better-bibtex) in Zotero. And that both programs are open at the same time!
  2. Add the CSS snippet under "Appearance>CSS snippets" by clicking on the "File" symbol and copying the .css into the newly opened file explorer window.
  3. Copy the .md file somewhere in your Vault (preferably into a dedicated Templates folder)
  4. Open the options page for Zotero Integration and click on "Add Import Format"
  5. Give the Import Format a recognizable name like "Export of all annotations"
  6. Set the output path (preferably to a dedicated Zotero import folder in your Vault) and make sure that it ends in "{{citekey}}.md"
  7. Select the template file (Type in the name and it should suggest it to you)
  8. Choose a bibliography style of your liking (or pick "American Psychological Association 7th edition", if you are not sure)
  9. Open the command palette and look for "Zotero Integration" and then the format name you chose
- What is the programming language/template engine?
  - Jinja. Search for "Jinja loops" or similar to learn more about how the looping and if statements are formatted.
- Can I change the colours of the callouts?
  - Yes. The colours are defined at the beginning of the CSS. Simply change them there and all the types of annotation of the same colour will change too.
-  Why are the "headers" of the callouts under the main text?
  - It is closer to the usual structure of citing text in academia. If you wish to disable it, simply delete or comment out the sections in the CSS that have the headers "Paratext under..."
- What kind of citation style is used in the header of the callouts?
	- It's not a real citation style, and instead a mostly improvised solution that contains enough information (authors, title, year and page number) to understand at a glance the origin of the excerpt, when removed from its original context, for example as an embed.
