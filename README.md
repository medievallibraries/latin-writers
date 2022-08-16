# Sharpe's Latin Writers

A simple prototype for a digital edition of Richard Sharpe, *A Handlist of Latin Writers of Great Britain and Ireland Before 1540* (Turnhout: Brepols, 1997).

## Data format

Sharpe continued to update his files for *Latin Writers* following its 1997 publication; we discussed creating a digital version from this, but this was not a priority before his untimely death. He kept the dataset as a single TeX file.

In this digital form, each writer and work has a separate file (in the `_writers` and `_works` folders) in [YAML format](https://learnxinyminutes.com/docs/yaml/). They refer to one another using permanent identifiers, which have no meaning.

The data files are readable in any plain text editor. The data is structured in the following form:

### Writers

```yaml
---
identifier:    # unique identifier created using https://shortunique.id
title:         # writer's name
order:         # abbreviation for religious order (OSB, OSA, etc.)
type:          # 'published' for a person whose works circulated in the Middle Ages under their name, rendered in small caps
               # 'ghost' for bibliographical ghosts, rendered in quotes
not-british: true     # = for a writer mistakenly thought in the past to have British connections, marked †
british-career: true  # = for a writer not born in British Isles but active there, marked ‡
death:         # date of death
description:   # short label shown before references
repertories:   # structured short references to repertories, formatted using `layouts/writer.html
  - BaleIndex:         # https://archive.org/details/mmanecdotaoxonie09oxfouoft
  - BaleCatalogus:     # https://catalog.hathitrust.org/Record/010824840
  - CALMA:             # Compendium Auctorum Latinorum Medii Aevi
  - Kirkstead:         # Kirkstead’s *Catalogus* 
  - LelandScriptores:  # https://catalog.hathitrust.org/Record/001169077
  - Mirabile:          # authors in https://www.mirabileweb.it (based on CALMA)
  - ODNB:              # Oxford Dictionary of National Biography
  - Tanner:            # https://archive.org/details/BibliothecaBritannicoHibernicaTanner
  - Wikidata:          # https://www.wikidata.org
  - Wright1:           # https://archive.org/details/biographiabritan01wriguoft
  - Wright2:           # https://archive.org/details/biographiabritan02wriguoft
bibliography:   # free-form citations
  - "Citation 1"
  - "Citation 2"
  - "Citation 3"
notes:
  "Free text."
---
```

### Works

```yaml
---
identifier:          # unique identifier created using https://shortunique.id
writer:              # identifer for the attributed writer
title:               # work's name, assumed to be in Latin
title-description:   # for an English descriptive name, rendered without italics
type:                # 'attributed' for likely attributions to a writer, marked '(attrib.)'
                     # 'spurious' for disproven attributions to a writer, rendered in quotes
description:   # short label shown before references
date-published:      # date (not structured)
alternative-titles:  # other names by which the work is known
  - "Title 1"
  - "Title 2"
incipits:            # 'text' is mandatory and gives opening words; 'type' is optional, where there are multiple incipits
  - text: "Incipit 1"
    type: "prologue"
  - text: "Incipit 2"
    type: "exposition"
editions:           # free-form citations
  - "ed. 1"
  - "ed. 2"
bibliography:       # free-form citations
  - "Citation 1"
  - "Citation 2"
  - "Citation 3"
repertories:        # structured short references to repertories, formatted using `layouts/work.html
  - BHL:                # Bibliotheca hagiographica Latina
  - Chevalier:          # Chevalier, Repertorium hymnologicum
  - CPL:                # Clavis Patrum Latinorum
  - ICL:                # Initia carminum Latinorum
  - Mirabile:           # https://www.mirabileweb.it
  - ThorndikeKibre:     # http://cctr1.umkc.edu/cgi-bin/medievalacademy
  - WIC:                # Walther, Initia carminum
notes:
  "Free text."
sources:            # free-form citations
  - "Manuscript 1"
  - "Manuscript 2"
  - "Manuscript 3"
attested-copies:    # free-form citations
  - "Manuscript 1"
  - "Manuscript 2"
  - "Manuscript 3"
---
```

## Rendering

A static site generator, [Jekyll](https://jekyllrb.com), uses templates to present the data in a more readable form. It reads the YAML data files using its [Collections feature](https://jekyllrb.com/docs/collections/). The technique of using cross references between collections is based on a '[Jekyll Author Pages](https://jetholt.com/micro/jekyll-author-pages/)' tutorial.
