# Polyglot for Zotero 
Zotero plugin for multi-lingual citations

# WORK IN PROGRESS

This planned plugin will allow you to provide as many translations as you like for any Zotero text field you like. 
A citation will then include the translation into the target language of the document you are making. 
You thus have the support to write articles, papers, theses etc. in more than one language.  

## Features

### Successor to _Jurism_
Polyglot  is designed to be a successor to _Jurism_ 
- _Jurism_ provided just one translation for any Zotero field.
    - _Polyglot for Zotero_ allows as many as you like, so you can use the Zotero data for citations in documents in multiple target languages.  
- _Jurism_ is a Zotero fork that is no longer supported. It has not been upgraded to Zotero 9 and is not stable with some modern environments such as Apple Silicon.
    - _Polyglot for Zotero_ is a plugin made to current official Zotero standards, so should be easier to maintain.
- If you want to **migrate** from an existing _Jurism 6_ environment to a new Zotero 9 or later environment, use my Jurism_to_Zotero_extractor. It will generate all the _Polyglot_ custom tags in Extra that you need to get started. 

### Complements native Zotero translation 
- Native _Zotero 9_ provides for translation of Titles only, and requires a manually-encoded tag in the Extra field to achieve that.
    - _Polyglot for Zotero_ provides for translation of any text field (including Title), and does it via a friendly UI.
 
### Complements the _Cite Non-English_ (CNE) plugin 
- _Cite Non-English_ provides translations for Title and Container Title only, and only into one language (always called "english").
    - _Polyglot for Zotero_ provides for translation of any field (including Title and Container Title).
- Note: _Polyglot for Zotero_ does NOT provide romanisation features, but will work alongside CNE for that purpose.

### Automatic translation assistance 
- If you provide your DeepL or Google credentials, _Polyglot for Zotero_ will pre-fill the translation field in the language you choose. You can still edit it yourself if you wish.

### Citation style independence 
- _Cite Non-English_ requires special CNE style templates, so will only work with styles for which someone has created a CNE template.
    - _Polyglot for Zotero_ does not require special style templates, so will work with any native Zotero style choice. 
- To avoid style hacks, _Polyglot for Zotero_ offers the user a simple direct choice.
    - (a) Format the translation to match the style of the original field (Recommended for APA).
        - Example (Book title): _Original [Translation]_
    - (b) Force translation text to be unitalicised, even when the main field is italicised (Recommended for MHRA, Chicago, MLA, etc.).
        - Example (Book title): _Original_ [Translation]
- _Polyglot for Zotero_ always puts the translation in square brackets; this is common to all styles, indicating something added by the author/editor of the current work.
    - Use round brackets in the original name field to indicate translations or alternate titles that are in the original document.
- Note: _Polyglot for Zotero_ assumes that if you provide a translation you want to use it. Not all academics and citations styles recommend this for all fields. For example, if the Publisher is 'Springer Verlag' (German), there is probably no need to translate this into English as 'Springer Publishing', or Portuguese as 'Editora Springer'.
    - _Polyglot for Zotero_ **lets** you translate anything, but it is up to you whether you actually do it!  

## Under the hood 
- The _Polyglot_ plugin comprises
    - A UI panel to create the translations
    - A background process that adds translations to the citation details before passing them to the standard citation style    
- In common with other plugins, _Polyglot_ uses the Zotero 'Extra' field to pass information between the two parts. Polyglot tags (the key in the key-value pair) have three parts 
    - Prefix: `pgl-`: To avoid clashes with Zotero (now or in the future), or with other plugins such as CNE, all _Polyglot_ tags have the unique prefix `pgl-`.
    - Body: The standard Zotero name of the field translated, e.g. `title`, `publisher`, `place`.
        - Any _text_ field can be translated, but of course number fields (like Page), date-time fields (like Accessed), and fields with specific formats, such as URL and ISBN, are not subject to translation.   
    - Suffix: The translation language as a standard ISO two-letter code, e.g. `-en` (English), `-de` (German), `-es` (Spanish), `-nl` (Dutch)     

- Example PGL tags:  
    - Example 1, for a book called _Der Tod im Werk von Joseph Beuys_
        - `pgl-title-en: Death in the Work of Joseph Beuys`
        - `pgl-title-pt: A morte na obra de Joseph Beuys`
        - `pgl-title-fr: La mort dans l'œuvre de Joseph Beuys`
    - Example 2, for a paper in a German archive called ZADIK (Zentralarchiv für deutsche und internationale Kunstmarktforschung)
        - `pgl-archive-en: Central Archive for German and International Art Market Research`
        - `pgl-archive-nl: Centraal archief voor Duits en internationaal kunstmarktonderzoek`
        - `pgl-archive-es: Archivo Central para la Investigación del Mercado del Arte Alemán e Internacional`
- Capitalisation: I recommend you use the norm for the language in question (as in the examples); but note that some styles might change this to the norm for the target language. Unfortunately, there is not much I can do about that :-( 

