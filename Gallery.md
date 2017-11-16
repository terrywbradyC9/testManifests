## DSpace Integration 

![screenshot](screenshots/dgInteg.png)
![screenshot](screenshots/dgInteg2.png)

## Gallery of IIIF Manifest Prototypes

### Manuscript with Irregular Page Orientation Generated from PDF Source File

- [Manifest](burst1.json)

### Hierarchical Collection Generated from Archival EAD with Item Level Metadata

![screenshot](screenshots/ead.png)

- [Manifest](ead.json)
- Inputs 
  - EAD File with item level metadata
  - PDF docements exported as jpg
  - Image paths manually edited into the EAD file
- This manifest was generated from an Archivist Toolkit EAD file 
- Code 
  - [ead2Manifest.xsl](eadConv/ead2Manifest.xsl)

## Automated Manifest Generation from File System Resouces

The following [File Analyzer](https://github.com/Georgetown-University-Libraries/File-Analyzer/wiki) classes support the manifests described below.
- [CreateIIIFManifest.java](https://github.com/Georgetown-University-Libraries/File-Analyzer/blob/iiif/demo/src/main/edu/georgetown/library/fileAnalyzer/filetest/CreateIIIFManifest.java)
- [IIIFManifest.java](https://github.com/Georgetown-University-Libraries/File-Analyzer/blob/iiif/demo/src/main/edu/georgetown/library/fileAnalyzer/filetest/IIIFManifest.java)

### Hierarchical Collection Generated from File System (boxes/folders) and EAD with Minimal Metadata
![screenshot](screenshots/ead2.png)

- [Manifest](ead2.json)
- Inputs
  - 1500 jpg files organized into 4 boxes and approx 100 folders
  - EAD file describing the contents of specific boxes and folders
- This manifest was generated by walking a collection of directories of digitized access
  - Metadata is pulled from an EAD file
  - The contents were linked by box number and file number
- Code
  - [CreateIIIFManifestEAD.java](https://github.com/Georgetown-University-Libraries/File-Analyzer/blob/iiif/demo/src/main/edu/georgetown/library/fileAnalyzer/filetest/CreateIIIFManifestEAD.java)
  - [IIIFManifestEAD.java](https://github.com/Georgetown-University-Libraries/File-Analyzer/blob/iiif/demo/src/main/edu/georgetown/library/fileAnalyzer/filetest/IIIFManifestEAD.java)


### Photo Gallery Created from DSpace AIP Exports (Subject Index)
![screenshot](screenshots/ua_photos.png)

-  [Manifest](ua_photos.json)
- Inputs
  - 499 DSpace AIP Export folders each containing a Jpg file and item level metadata in mets.xml file
- Each folder is processed
  - A canvas is added to the overall sequence
  - Subject Indexing
    - A range is created for each unique subject term for the item (stored in a hash map by subject term)
    - A range is created for an individual canvas (we will call this the item range)
    - The item range is linked below the subject range.  This allows non-sequential items to be grouped together.

### Photo Gallery Created from DSpace AIP Exports with Subject and Date Indexes
![screenshot](screenshots/ua_photos2.png)

- [Manifest](ua_photos2.json)
- Inputs
  - 499 DSpace AIP Export folders each containing a Jpg file and item level metadata in mets.xml file
- Each folder is processed
  - A canvas is created and stored into a hash based on the item creation date
    - Canvas records are written to the sequence in creation date order  
  - Date indexing
    - A range is created for each decade associated with a creation date
    - Canvas references are linked to the appropriate decade range
    - Since items are added in date order, the images can be browsed by creation date
  - Subject Indexing
    - A range is created for each unique subject term for the item (stored in a hash map by subject term)
    - A range is created for an individual canvas (we will call this the item range)
    - The item range is linked below the subject range.  This allows non-sequential items to be grouped together.
- Code
  - [CreateIIIFManifestAIP.java](https://github.com/Georgetown-University-Libraries/File-Analyzer/blob/iiif/demo/src/main/edu/georgetown/library/fileAnalyzer/filetest/CreateIIIFManifestAIP.java)
  - [IIIFManifestAIP.java](https://github.com/Georgetown-University-Libraries/File-Analyzer/blob/iiif/demo/src/main/edu/georgetown/library/fileAnalyzer/filetest/IIIFManifestAIP.java) 

### Student Newspapaer Collection (Each Issue in its Own Manifest)
![screenshot](screenshots/hoya.png)

- [Manifest](hoyacoll.json)
- Inputs
  - 5 folders representing an individual issue of the paper each containing
    - 1 tif file per page
    - dublin_core.xml file exported from DSpace
- Each folder was processed individually generating a manifest file
  - Each manifest file was listed in a collection manifest file for the overall collection
- Code
  - [CreateIIIFManifestDC.java](https://github.com/Georgetown-University-Libraries/File-Analyzer/blob/iiif/demo/src/main/edu/georgetown/library/fileAnalyzer/filetest/CreateIIIFManifestDC.java)
  - [IIIFManifestDC.java](https://github.com/Georgetown-University-Libraries/File-Analyzer/blob/iiif/demo/src/main/edu/georgetown/library/fileAnalyzer/filetest/IIIFManifestDC.java) 

---
[![GitPitch](https://gitpitch.com/assets/badge.svg)](https://gitpitch.com/Georgetown-University-Libraries/testManifests)
  