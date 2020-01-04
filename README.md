# File Formats used by Molecular Materials Informatics

The cheminformatics industry has its own custom file formats for representing molecular structures of various kinds, and various types of derived aggregations like collections, reactions, mixtures, etc. The various software tools produced by [Molecular Materials Informatics](http://molmatinf.com) use two main file formats as their native datastructures: *SketchEl Molecule* and *XML DataSheet*.

## SketchEl Molecule

Originally developed for the open source [SketchEl](http://sketchel.sf.net) drawing tool, it is intended primarily for capturing 2D structure drawings created using an editing tool. In terms of its use case range, it is roughly equivalent to the industry standard *Molfile* format (which has been sequentially owned by MDL, Symyx, Accelrys and now Biovia). It has several key advantages over the *Molfile* format, such as being designed for minimalistic simplicity, backward-compatible extensibility, and with a diverse range of chemistry in mind that includes inorganic and organometallic compounds.

* Specific [description of the format](sketchel/README.md)

## XML DataSheet

The *datasheet* format is a tabular collection of data that is usually visually expressed as a typed spreadsheet, i.e. the columns are heavily regulated and have well defined limitations on what content can be included in them. Being chemically aware, it has a dedicated datatype for *molecules*, which uses the *SketchEl Molecule* format mentioned above.

The datastructure itself is typically serialised as XML, though it is trivial to use other contained formats like JSON.

In its basic form, the format is roughly equivalent to the industry standard *SDfile* format, which is the collection version of the *Molfile* format. It avoids many (or perhaps most) of the limitations of the *SDfile* format, which is a very long list.

The *XML datasheet* format defines a header extension mechanism which allows the specification of *Aspects*, which are essentionally optional meta-instructions about how to compose the row/column content that makes up the datasheet. This is a mechanism to add functionality for describing more complex concepts, such as reactions, scaffolding patterns, measurement units, assay information, and anything else that is worth implementing. The extension pattern is implemented in a backward-compatible way such that tools that do not understand the extensions can still be used to view and edit the content without necessarily causing problems.

* Specific [description of the format](datasheet/README.md)
* Detailed [description of aspect extensions](aspect/README.md)