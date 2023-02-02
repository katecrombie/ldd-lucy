<!--
   README.md template

   In this template, values delimited by braces (e.g., "{value}") should be
   replaced by the appropriate values for your namespace. The braces
   should then be removed. Example values are provided as comments for
   potentially mysterious cases.
-->

# Lucy mission (lucy:) Local Dictionary
<!-- EXAMPLES
   Spectral (sp:) Discipline Dictionary
   DART Mission (dart:) Local Dictionary
-->

The Lucy mission dictionary provides classes and attributes for
describing [*Lucy*](http://lucy.swri.edu/) data products and associated information in PDS4.

### Steward
M. Katherine Crombie ([@katecrombie](https://github.com/katecrombie))
<!-- EXAMPLE
     Anne Raugh (@acraugh), Small Bodies Node (SBN)
-->

# Documentation

<!-- The following assumes the complete documentation set exists. If it
does not, edit the sentence and link accordingly. -->
The User's Guide and detailed documentation for using this dictionary in
label design and processing
are located at https://pds-data-dictionaries.github.io/ldd-lucy.
<!-- EXAMPLE
     are located at https://pds-data-dictionaries.github.io/ldd-template.
-->

# Latest Release

<!-- Note that the Dictionaries Page link below won't look right on the
     rendered page until you replace the braces and content with the
     dictionary prefix.

     EXAMPLE

     [PDS Data Dictionaries Page](https://pds.nasa.gov/datastandards/dictionaries/#sp)

     The GitHub link will exist once there is an official first release of
     the dictionary (typically part of a system build) for the namespace. The
     link is the same for all LDD repos and all builds.

     The change log file is usually in the root directory of the repo, but
     path information relative to root can be included if needed.

     EXAMPLES

       * Review the [Change Log] (ChangeLog.md)
       * Review the [Change Log] (src/CHANGELOG.md)
-->     
* Download dictionary files from the [PDS Data Dictionaries Page](https://pds.nasa.gov/datastandards/dictionaries/#lucy)
* On [GitHub](../../releases/latest)
* Review the [Change log](CHANGELOG.md)

# About This Repository
<!-- The top-level directory structure and names must not change, but if
you have more to say about any of these directories, edit away! -->
In this repo you will find...
* **[src/](src)** - The directory containing the managed *IngestLDD* file
 that defines this namespace. This is where changes to the namespace
 itself are made.
* **[build/](build)** - This directory holds the files generated by the
build processing, including the schema files used in designing and
validating labels, JSON for inclusion in code, and report files from the
LDDTool execution that created the files. There are separate
subdirectories for development versions and releases.
* **[test/](test)** - This directory contains regression tests (in the
  form of documented labels) for this namespace.
* **[logs/](logs)** - This directory contains the logs generated by the
 GitHub-automated build and test processes of LDDTool and Validate.
* **[examples/](examples)** - This directory contains label samples for
using this namespace.
* **[.github/](.github)** - This (possibly hidden) directory contains
internal files used to manage the automated build processes.


The `main` branch is where you should merge your final changes to documentation and LDD structure.
The `gh-pages` branch is auto-generated and used to run the documentation site. **DO NOT MAKE CHANGES HERE**.

# Contributing to this Dictionary

## Suggest a Feature or Report a Bug
<!-- replace "repo id" below with the "ldd-xxx" string from the
GitHub repo URL.-->

There is a common place to request enhancements and report problems for
any PDS-curated dictionary - the [PDS4 Issue Repo](https://github.com/pds-data-dictionaries/PDS4-LDD-Issue-Repo/issues/new/choose).
Search for the \[ldd-lucy\] update request block and click the green
"Get Started" button.

## Contribute Code or documentation
If you'd like to actively contribute to development, begin with the
feature/bug process described above. Then familiarize yourself with
the [LDD Update Process](https://pds-data-dictionaries.github.io/development/ldd-update.html)
and contact the dictionary steward to coordinate development, testing,
and release. And thanks!

# General Support for Dictionary Developers
See the [PDS Data Dictionaries pages](https://pds-data-dictionaries.github.io)
for documentation and tutorials describing the procedures
required to reserve a namespace,
establish a new repo, and build your dictionary.

<!-- NOTE

     PDS needs a better suggestion than the following, but I'm hesitant
     to point to my wiki and I don't see the information clearly
     identified elsewhere...
-->
If you need help creating your *IngestLDD* file, contact the [Dictionary Stewards Group](https://pds-data-dictionaries.github.io/teams/pds-dd-stewards.html). Documentation is in preparation.

# For Dictionary Stewards

See the [tutorial on updating and building an IngestLDD](https://pds-data-dictionaries.github.io/support/tutorials.html#ldd-update-and-build-tutorial) and the [LDD Update Process](https://pds-data-dictionaries.github.io/development/ldd-update.html) for documentation of those procedures.

## Building the dictionary

Each build is auto-generated using Github Actions, PDS4 LDDTool, and Validate Tool.

You can also download the *IngestLDD* file and build the dictionary locally.
You will need to install *[LDDTool]* (https://nasa-pds.github.io/pds4-information-model/model-lddtool/index.html) on your system. Once you do,
you can manually run [LDDTool](https://nasa-pds.github.io/pds4-information-model/model-lddtool/index.html) on the IngestLDD using the following command:

```
lddtool -lpsnJ PDS4_LUCY_IngestLDD.xml
```

# Generating Namespace Documentation
The documentation website is managed by GitHub Pages. When changes are made on the `main` branch, GitHub will process those changes and update the `gh-pages` branch, which drives the website on pds-data-dictionaries.github.io. 

If you would like to test your changes and generate the site on your own system:

1. Clone the repository
2. Install Python dependencies (preferably within a Python virtual environment[^1]) using this command:
```
pip install -r requirements.txt
```
3. Follow steps below

[^1]: [Python Virtual Environment How-To at docs.python.org](https://docs.python.org/3/library/venv.html)

## To Generate HTML

1. Build the HTML documents
```
cd docs
make clean html
```
   Note that in Windows environments you will need to run the "clean" and "html" operations as separate invocations of "make":
```
cd docs
make clean
make html
````

2. Preview the HTML in your browser
```
open build/html/index.html
```

## To Generate PDF

1. Install some additional dependencies:

   On a Mac:
   ```
   brew install texlive
   ```

   On Linux:
   ```
   apt-get install texlive-latex-recommended texlive-latex-extra texlive-fonts-recommended
   ```

2. Make the PDF
```
cd docs
make latexpdf
```

The output PDF will be written into the *docs/* directory.
The output file name will depend on the value for the ```project``` variable
in the *docs/source/conf.py* file.
