# Scrivener for Scientific Writing - setup

Below please find my final setup for writing a scientific paper/book. Although my requirements seemed to be clear&simple, it took me app. 40 hours to put everything together. And here it is: my final set-up ready :)



# My needs

I want my system to support me in:

1. Managing scientific sources and citations
2. Insert and enumerate simple equations
3. Export the final document to MS Word docx format, keeping all Styles (like headings).



# Tools

1. Storing all documents and drafts: **Google Drive**
2. Managing scientific sources: **Zotero** (https://www.zotero.org/)
3. Making notes and structuring content: **MindManager** (https://www.mindjet.com/mindmanager/)
4. Writing: **Scrivener** (https://www.literatureandlatte.com/scrivener/overview)
5. Exporting: **Pandoc** (https://pandoc.org/).



# Workflow

1. Initiate the project:
   1. set-up a Google Drive folder and create subfolders:
      1. *{book title}*
         1. *... {book chapters}*...
      2. *Setup*
   2. set-up a Zotero folder for all needed resources {book title}
      1. export this folder to *Setup* Google Drive folder in a BibTex format using Better Bibtex plugin (how to can be found in points 1-5 [here](https://raphaelkabo.com/blog/posts/markdown-to-word/)) > *mylibrary.bib*
   3. in the *Setup* Google Drive folder store:
      1. a docx template for Your book (with all proper styles)
      2. *mylibrary.bib*
      3. Your preferred citation style: choose sth from https://www.zotero.org/styles, eg. https://www.zotero.org/styles/chicago-author-date-16th-edition
2. Scientific sources
   1. Gather all necessary knowledge resources (books, papers, websites, reports etc.) using:
      1. Zotero web plugin
      2. Zotero ISBN search
      3. Just drag&drop files from Your folders
   2. Organize them using TAGS
   3. Make notes:
      1. annotate PDFs and then export notes to Zotero using *ZotFile*
      2. integrate key notes into MindManager
   4. Make draft structure (paragraph-detail level) in MindManager
3. Writing:
   1. organize all the writing in Scrivener using folders
   2. control targets and writing progress with meta-tags
   3. compile to docx via MultiMarkdown and Pandoc (see *compile presets* below).



# Install

## Zotero

1. Install Zotero (from www.zotero.org)
2. Install useful plugins:
   1. Better Bibtex plugin (see installation instructions [here](https://github.com/retorquere/zotero-better-bibtex/wiki/Installation)) > to export Your reference library as a BibTex file
   2. [ZotFile](http://zotfile.com/) > for efficient PDF management, especially exporting annotations from PDF to Zotero
3. [Zotpick-applescript](https://github.com/davepwsmith/zotpick-applescript) > for a possibility of calling Zotero citation during writing with a single click
   1. Mac-OS only: Create a dedicated app with Workflow Manager (see installation instructions [https://raphaelkabo.com/blog/posts/markdown-to-word/](https://raphaelkabo.com/blog/posts/markdown-to-word/))



## Scrivener

I suggest to purchase it driectly from https://www.literatureandlatte.com/scrivener/overview - an AppStore version has some limitations.



## Pandoc

For markdown to docx conversion.

1. from terminal with 

   ```
   brew install pandoc
   ```

2. from [this page](https://github.com/jgm/pandoc/releases/tag/2.1.1).

3. Additionally, install the following pandoc extensions:

   1. pandoc-citeproc: for managing citation. Installation instructions [here](https://github.com/tomduck/pandoc-eqnos#installation), or:
      
      ```
      brew install pandoc-citeproc
      ```
      
      
      
   2. pandoc-eqnos: for enumarating equations. Installation instructions  [here](https://github.com/tomduck/pandoc-eqnos#installation), or:
   
      ```
      pip install pandoc-fignos
      ```
   
      

# Setup

The only, **and the most difficult to**, setup you need is Scrivener.

1. (suggested, but not required): import my Scrivener **preferences** and **theme** settings from *scrivener settings* github folder

2. Compile presets. **This is the most important - magic happens here!**

   1. **from *scrivener settings* import *My Markdown.scrformat*.** 

      1. click *File > Compile*
      2. drag and drop *My Markdown.scrformat* into the *Formats* panel on the right. Choose "My Formats" option

   2. To see it's presets: *right-click > Edit*

      1. I made a lot of changes to *Styles*, basing mostly on *Scrivomatic* MarkDown exports (see: https://github.com/iandol/scrivomatic)

      2. **The most important settings are in *Processing* script**. It took me app 30 hours to get there :). When you click *Processing > Edit Script* you will see sth like that:

         ![image-20191217193249892](/Users/Andy/Library/Application Support/typora-user-images/image-20191217193249892.png)

      3. The script itself is below (for Your Copy-Paste convenience - some fine tuning will be necessary):

         ```
         fullfilename=$1
         filename=$(basename "$fullfilename")
         fname="${filename%.*}"
         
         pandoc --filter pandoc-citeproc --filter /Applications/Anaconda/anaconda/bin/pandoc-eqnos --bibliography '/Users/Andy/Dysk Google/Scrivener/setup/! final setup/github/setup/mylibrary.bib' --csl '/Users/Andy/Dysk Google/Scrivener/setup/! final setup/github/setup/ee.csl' $filename -f markdown-auto_identifiers+tex_math_dollars --reference-doc '/Users/Andy/Dysk Google/Scrivener/setup/! final setup/github/setup/MS Word - Cambria.docx' -o $fname.docx
         ```

   3. **IMPORTANT**: update paths to Your local settings:

      1. */Applications/Anaconda/anaconda/bin/pandoc-eqnos* <<< Your pandas-eqnos installation. Attention: I don't know why, but even if *pandoc-eqnos* works perfect from Your terminal, here the full path is needed...
      2. */Users/Andy/Dysk Google/Scrivener/setup/! final setup/github/setup/mylibrary.bib* - this is a path to Your *Google Drive/.../setup/mylibrary.bib* file.
      3. */Users/Andy/Dysk Google/Scrivener/setup/! final setup/github/setup/ee.csl* - this is a path to Your *Google Drive/.../setup/{preferred style sheet}* file.
      4. */Users/Andy/Dysk Google/Scrivener/setup/! final setup/github/setup/MS Word - Cambria.docx* - this is a path to Your *Google Drive/.../setup/{preferred docx style}* file.

      **That's it!** It should work, although it maybe very cumbersome...

# Usage

1. Create a New Scrivener Project
2. Write sth
3. Compile:
   1. Compile for: MultiMarkdown
   2. Presets: *My Markdown*



# My Example

1. Open *draft* project from main girhub folder
2. Compile
3. And check the output. I put my sample in the *output* folder.



# Useful resources

1. My inspirations:
   1. https://raphaelkabo.com/blog/posts/markdown-to-word/
   2. http://davepwsmith.github.io/academic-scrivener-howto/
   3. https://www.simondcoll.com/references-markdown-zotero/
2. Zotero, Markdown and Pandoc:
   1. All videos on Zotero, Markdown and Pandoc from Nicholas Cifuentes-Goodbody, starting from https://www.youtube.com/watch?v=Gm2MbYB3k4o&list=PLXt-tu7G1H3vlRXLmGyOzeAp7ZKDK0pty&index=1. Great!
3. Scrivener has their own really great tutorials [here](https://www.literatureandlatte.com/learn-and-support/video-tutorials?os=macOS).



# My Github project with all the files

https://github.com/wodecki/writing



**Happy writing :)**

