Preface
 - disclaimer: not erasing or superseding TEI Guidelines; for beginners, those just want to experiment, those who feel like their research project matches the goals here; for those who want to be a part of portals like Sources Online
 - target audience:
   - researchers needing a starting point to extend
   - focus on European historical materials
   - newcomers to TEI encoding seeking a reduced, recommended ODD as basis
   - users who plan to publish an edition with TEI Publisher and expect a good out of the box rendition
   - institutions hosting large, heterogenous corpora and looking for a way to make them available

## A Short Example

Point to example editions which demonstrate the features.
Discuss a simplified, self-contained example, e.g. KB letter with entities defined in the header.

## The Structure of a TEI Vanilla Document 
   - metadata
     - lists of entities
     - publication info
     - editors...
   - edited text: 
     - transcription, 
     - translation(s), 
     - commentaries (notes)
   - all content should be contained in a div (change ODD to only allow div in front/back/body)
   - publisher does not treat front/back specially (but you may assign a @rend or @type for visual separation)

    ```xml
    <front>
      <div type="introduction"></div>
    </front>
    ```

   - abstract/regest/summary may go into profileDesc
  
## Structure of the text
  * Text Division Elements
    * logical
      * use nested divs to determine structure, concentrate on logical structure: volume/chapter/section...
      * Headings: some divisions may have their own "title" which would be the first element in a division
    * physical: pages, lines, columns
      * Page and Line Numbers
      * break attribute on lb
      * ?handling multi-witness texts
  * Textual Components
    - Verse: make clear the distinction between l - logical verse unit and lb - physical line
    - Other Kinds of Text Block: seg, ab
  
  ## Phrase level 
  * Marking Highlighted Phrases
    - Changes of Typeface, etc.
    - Quotations and Related Features
    - Foreign Words or Expressions

  ## Notes
    - a. inline notes
    - b. linked notes in back
    
  ## Cross References and Links
    - Bibliographic Citations
    - Simple Cross References
    - Pointing to other documents
    - Special Kinds of Linking
## Editorial Interventions
  * Correction and Normalization
  * Omissions, Deletions, and Additions
  * Abbreviation and their Expansion
## Names, Codes, and Numbers
  * Names and Referring Strings
  * Formulae, Codes, and Special Characters
  * Dates and Times
  * Numbers and Measurements
   
## Graphics and Facsimiles
  * @facs only
  * `<facsimile>` and zones
  * absolute vs relative facsimile urls

## Text alignment
  - translation/original
  - text collations
  


## Metadata
  * The File Description
    - Titles: full and short; series....
    - The Publication Statement
      - how to encode different roles: editor/funder... since only a subset of elements is available
    - Series
    - The Source Description
      - ... how to do it for archival materials
      - idno, 
      - examples for
        - printed
        - ms
          - archival source (short identification)
          - library (rich content)
    - language information
    - revisions
  
  ## Shared resources / Project Introductions / Authority files

  discuss factoring it out for the project, not presenting in each document

    - Taxonomies
    - Prefixes (e.g. for facsimiles or refs)
    - people/places...
     
  

##  The TEI Vanilla schema
  - how to assign a schema in oxygen/vscode and validate
  - link to the document and tracker for bug reports / feature requests

## TEI Publisher integration --- for the future
   
