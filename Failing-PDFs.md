This is a list of files that are reported to be broken.

The following tags are used to specify why they break:

* ???: Not specified yet (help!)
* FONT: breaking due to not fully supported fonts
* RENDERING: breaking due to not jet implemented rendering spec
* THROW: throws an error while doing the rendering
* INVALID: invalid PDF structure

From issue [#560](https://github.com/andreasgal/pdf.js/issues/560):

* FONT: http://pdfkit.org/example.pdf

From issue [#577](https://github.com/andreasgal/pdf.js/issues/577):

* <del>FONT(no spaces): https://docs.rice.edu/confluence/download/attachments/4588376/unix01.pdf?version=1</del>
* INVALID(RGBT content command instead of 'RG BT'): www-csag.ucsd.edu/~jburke/Vesta/Vesta_Overview.pdf
* <del>FONT(no spaces): http://www.csb.yale.edu/userguides/graphics/rasmol/rasmol.pdf</del>
* FONT(Type3 [#502](https://github.com/andreasgal/pdf.js/issues/502)): people.csail.mit.edu/ledlie/papers/tr-03-02.pdf
* RENDERING(JPX [#286](https://github.com/andreasgal/pdf.js/issues/286)): www.nsa.gov/ia/_files/app/pdf_risks.pdf
* INVALID: www.mit.edu/~6.033/writing-samples/usmanm_dp1.pdf