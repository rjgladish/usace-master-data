# Glossaries
The `glossaries` directory contains glossaries describing terms and definitions essential to business functions. The glossarries are organized by authoritative source within an organizing directory structure, such as `Civil Works`.
The **terms**, **definitions** and other glossary properties are derived directly from a single, authoritative source cited in the glossary **about** section.

Each source glossary is self-contained and individual glossaries are organized within a directory (folder) with one (1) YAML document corresponding to a single authoritative source of truth.

As new glossary sources are introduced into the digital model governance process, new glossary documents can be added to describe the source and enumerate glosssary terms and abbreviations extracted from the source document through external automated or manually-assisted means. Additional directories can be added to organize the glossaries. Great care should be taken to organize the directories and populate glossary documents using glossary identifiers i.e. namespace URI that will endure over time, as they serve a key role in modern, digital model governance and digital thread and Digital Engineering practices.

For example, `glossaries/CivilWorks`, contains man glossary documents concerning USACE Civil Works operations. 

One source, [**Code of Federal Regulations - Title 33, Chapter-II, Part 329, Section-329.4**](https://www.ecfr.gov/current/title-33/chapter-II/part-329/section-329.4) is shown below:
```yaml
about:
    namespace: https://usace-data.com/civil-works/glossary/CFR-33-329-4#
    prefix: CFR-33-329-4
    template: glossary
    title:  Code of Federal Regulations - Title 33, Chapter-II, Part 329, Section-329.4
    source:
        linkType: cfr
        sourceID: CFR-33-329-4
        authoritativeSource: 33 CFR 329.4 Definitions
        glossaryReferences: true
        url: https://www.ecfr.gov/current/title-33/chapter-II/part-329/section-329.4
terms:
- label: Navigable Waters
  definition: Navigable waters of the United States are those waters that are subject
    to the ebb and flow of the tide and/or are presently used, or have been used in
    the past, or may be susceptible for use to transport interstate or foreign commerce.
    A determination of navigability, once made, applies laterally over the entire
    surface of the waterbody, and is not extinguished by later actions or events which
    impede or destroy navigable capacity.
  anchor: '1'
  ```
## Property Names
Individual terms are defined, along with optional glossary metadata properties. All property names begin with lowercase letters, adding an uppercase letter to separate words in a word phrase, e.g. `word` versus `wordPhrase`.

## about
This section characterizes the source, providing essential governance metadata that supports the creation and propagation of digital threads in downstream information and engineering models.



### title
The **title** contains the fficial title of the glossary, usually the title of that authoritative source document., although it may be abbreviated or expanded as necessary. For example, well-known acronyms such as DoD may be substitueted for United States Deepartment of Defense. Conversely, obscure acronymns that appear in source
document titles may require expansion. 

### namespace
The **namespace** property is **__FOUNDATIONAL__** to Digital Engineering and Digital Threads. The **namespace** value establishes a globally unique identifier for downstream model and concept definitions that correspond to the glossary term.

### prefix
The **prefix** property is a convenient abbreviation of the namespace. For glossaries, the glossary **prefix** aligns with the **sourceID** described below. 

### publisher
The **publisher** is the owner or an executive proxy for the authoritative source. This is entity responsible for publishing the glossary. The publisher is responsible for faithfully extracting and encoding terms and definitians from the authoritative source in the glossary document.

### about.source
####authoritativeSource
- **source**: Details about the authoritative source of the glossary.
  - **authoritativeSource**: The source that holds the authority for the glossary content.
  - **sourceID**: A unique identifier for the source.
  - **description**: A brief description of the source.
  - **url**: The URL where the authoritative source can be accessed.
  - **anchor**: A digital link anchor for the source.
  - **linkType**: Specifies the type of digital page link (pdf, html).
  - **part**: Subdivision within the source.
  - **page**: Physical page range within the source.
  - **parentTopic**: Relationship to a parent topic.
  - **glossaryReferences**: Indicates if the source is referenced by the glossary (deprecated).
- **template**: The template used for generating the glossary pages.

#### terms
- **label**: The term's label.
- **definition**: The definition of the term.
- **acronym**: An acronym for the term.
- **abbreviation**: An abbreviation for the term.
- **altName**: Alternative names for the term.
- **url**: A specified URL related to the term.
- **sourceID**: A modifier for the source of the term.
- **anchor**: A digital link modifier for the term.
- **parentTopic**: The term's relationship to a parent topic.
- **page**: The physical page range where the term is found.
#### abbreviations
- **abbreviation**: The abbreviation's label.
- **definition**: The term, phrase, or acronym expansion of the abbreviation.
- **url**: A specified URL related to the abbreviation.
- **sourceID**: Term-specific modifier for the source of the abbreviation.
- **anchor**: A digital link modifier for the abbreviation.
- **parentTopic**: The abbreviation's relationship to a parent topic.
- **page**: The physical page range where the abbreviation is found.

Term and definition URI/IRI are automatically generated from the about, terms, and abbreviation properties.  
s of all URI/URI gener

## anchor, page, and linkType
Although all terms with the glossary share the same source authoritative reference document, each term definition may be localized using HTML anchors, PDF anchor, or physical document pages, by adding `anchor` or `page` properties respectively. Valid values for linkType are 'pdf', 'html', 'cfr', and 'physical'. Physical page numbers corrended to the page number 'embedded' or 'printed' in the document. An anchor can be an HTML tag, or a PDF digital page number. The page property and the anchor property can be used simultaneously to capture electronic address and physical 'page metadata.

### page and linkType = physical
**page** ALWAYS refers to a physical document page. Electronic office and scanned physical documents often incorporate page numbers into the source document; however, these page numbers do not always correspond to the digital page numbers used in PDF or Word. Glossary documents may cite physical pages using the **page** property.

**linktType**='physical' will cause anchors to be ignored.

### anchor and linkType = cfr
A special form of **automatic** link reference generation is supported for CFR sources.
Using **url** values that conform CFR HTML anchor protocol. In the `about.source` subsection, `linkType: cfr` enables this link generation. that

### anchor and linkType == html
An HTML anchor is a designated, web-addressable location within a document, such as a heading or table. HTML is always one 'page', so an HTML **anchor** property value refers to the section or table within a document where the term an definition is found.

### anchor and linkType = pdf
In PDF documents, an anchor refers to a secific part of the document or a page. For instance, if a PDF contains a bookmark or anchor named "Definitions," clicking on this bookmark when it appears in the document will take you straight to the "Definitions" section of the document.

Unklike HTML documents PDF documents have pages. These digital pages are web-addressable as anchors, so the **anchor** value in a PDF document refers to the digital page.

## Civil Works Glossaries:
- **Purpose**: Establish a reusable digital resource of officially sanctioned terms and definitions for USACE Civil Works glossaries, which are essential for effective communication within the organization, including definition citations that reference the authoritative source.
- **Tools**: The project provides tools for transforming glossary terms, organizing glossaries by authoritative sources, and supporting downstream knowledge engineering activities.
Looking at the example above, glossary property names are a word or a word phrase mashed together. Values are simple strings. Some symbols have special meaning in YAML, so exercise care when encorporatig symbols into glossary documents. Be especially diligent with cut-n-paste, as the can introduce characters that will cause problemns downstream.