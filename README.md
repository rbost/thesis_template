# A LaTeX template for (PhD) theses

A customizable template for theses written in LaTeX. It is mainly oriented towards cryptography/computer science theses, but can be used for any other topic.

Uses KOMA script's book class as the document class, and a bunch of other packages such as [microtype](https://www.ctan.org/pkg/microtype) (for microtypography), [biblatex](https://ctan.org/pkg/biblatex) (for advanced bibliography management), or [lettrine](https://ctan.org/pkg/lettrine) ...

How To Use the Template
-----------------------

To use this template, you can just clone this repo, or fork it.
 
## Structure

```
./
├── master.tex                                 * root LaTeX file
├── master.pdf                                 * link to the compiled document
├── biblio_aux.bib                             * additional bibliography
├── README.md
├── LICENSE
├──aux/                                        * configuration files
|   ├── algorithms.tex                         * configuration of the algorithmicx package
|   ├── chapter_toggles.tex                    * declaration of toggles to enable-disable chapters
|   ├── (chapter_toggles.conf)                 * override the default values declared in 
|	│                                            chapter_toggles.tex (not tracked by git)
|   ├── chapterthumb.sty                       * package providing printed chapter bookmarks
|   ├── fonts.tex                              * font definition
|   ├── layout.tex                             * configuration of the thesis layout
|   ├── macros.tex                             * useful generic math/crypto macros
|   ├── packages.tex                           * commonly used, and useful packages 
│   └── topic_macros.tex                       * your own macros for the thesis
|
├── content/                                   * document's content source
|   ├── resume_fr/                             * summary in french
|	│   ├── resume_fr_master.tex               * master file
|	│   ├── intro_se_fr.tex                    * introduction in french
|	│   └── contributions.tex                  * contributions in french
|	│
│   ├── introduction/                          * introduction chapter
|	|	├── introduction_master.tex            * master file
|	│   |
|	│   ...
|	│
│   ├── definitions/                           * definitions chapter
|	|	├── definitions_master.tex             * master file
|	│   |
|	│   ...
|	│
│   └── conclusion/                            * conclusion
|	    ├── conclusion_master.tex              * master file
|	    ├── summary.tex                        
|	    └── open_problems.tex                  
│
├── cover/                                     * cover page
|	├── front.tex                              * source for the cover page
|	└── front.pdf                              * compiled cover
│
└── build/                                     * built sources
	├── master.pdf                             * compiled document
	├── master.aux                             * TeX aux file
	├── master.log                             * Compilation log
	|
	...

```

Configuration Flags
-------------------

This template has several configurations flags.

* `draft`: activates the draft mode. Disables microtype and chapterthumb  
* `chapterthumb`: activates chapter thumbs (gray blocks on the right of odd pages with the chapter number)
* `showoverflow`: activates an overfull hbox indicator (very useful for to locate them)
* `allowtodo`: allows the `\todo` command. Otherwise, the compilation will fail if you have some todos in your document. Turn off this option to make sure you did not forget any todo.
* `showtodo`: displays the todos in the document.
* `inlinetodo`: when turned on, this option makes the todos appear inlined in red in the document. Otherwise, they are displayed in the margins.
* `printversion`: disable colored links for the print version
* `biblatex`: use biblatex instead of bibtex for bibliography management
* `chapter_bib`: display a bibliography at the end of each chapter listing all the citation within this chapter
* `chap_minitoc`: display a table of content at the beginning of each chapter 
* `lettrine`: enables the lettrines, using the `\lettrine` command. If this option is turned off, the lettrine will be displayed as normal text.
* `enluminure`: enables the `\enluminure` command, a lettrine with a special font. If this option is disabled, and `lettrine` is enabled, the `\lettrine` command will be used instead. If both options are disabled, the enluminure will be displayed as normal text.

These flag can be set (resp. unset) by using `\toggletrue{flag}` (resp. `\togglefalse{flag}`)


For Cryptographers
------------------

If you are writing a crypto thesis, you will be interested in the [cryptocode](https://ctan.org/pkg/cryptocode) package. It defines many macros that are useful when writing cryptography.

Also, I advise to use the amazing [CryptoBib](https://cryptobib.di.ens.fr) repo for the bibliography. It regroups all the publications in the major crypto/security conferences in a single .bib file, with standardized cite keys (*e.g.* PKC:CPPT14 for the article by Canetti, Paneth, Papadopoulos, and Triandopoulos published at PKC in 2014). The references are also normalized (all the papers from the same conference/journal are referenced the same way), which IMHO is great.

To get CryptoBib, create a submodule:
```sh
git submodule add https://github.com/cryptobib/export cryptobib
```
To update the CryptoBib submodule, do:
```sh
( cd cryptobib && git pull origin master )
```
Finally, to retrieve the submodule after a `git clone`, or a `git pull`:
```sh
git submodule update --init
```

License
-------
This work is licensed under a [Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License](http://creativecommons.org/licenses/by-nc-sa/4.0/).
[![Creative Commons License](https://i.creativecommons.org/l/by-nc-sa/4.0/88x31.png)](http://creativecommons.org/licenses/by-nc-sa/4.0/)