# Syntax for defining easier math
If you are a physicist using `groff`, you will inevitebly at some point use the 
"bra/ket" notation to describe wavefunctions in quantum mechanics.
There is a neat way to make things much more pleasant to type in the math environment.
```
.EQ
define > `\(ra`
.EN
```
Now it's very easy to make a ket-vector look nice, as `| psi >` now gives *|𝜓⟩*.
Note that this will get you in trouble, once you *actually* want to put a ">" (greater than)
anywhere in your equation. In that case, the definition needs to be temporarily disabled...
I have to check how that one goes.


# Bibliography for refer uses the same formatting as Endnote. 
Download citations from journals accordingly!
If you want your citations included by using `refer` along with `groff` there is a syntax 
that the bibliography files need to adhere to. Luckily the format used by *EndNote* is identical, 
and since most sources for scientific papers offer you to download citations for *EndNote*, you
can just use those and wont have to change anything.
You might want to add a memorable handle to your references though.



Flag to recognize utf-8 symbols like umlauts (äüö) and greek letters (µ):
	groff -K utf-8 ...

MS macro needs on instance of .PP to make title page work properly.

Proper listing of items with nice indentation when using MS macros
	.RS
	.IP \[bu] 2n
	Item 1, bu for bulletin icon instead of -
	.IP \[bu]
	Item 2, 2n to adjust indentation after bulletin
	.RE

Sans Serif / Helvetica font laden 
(gesamtes Dokument)
	.fp 1 H
(nur nächste Zeile)
	.fam H

Include EPS file
	.PSPIC header.eps
compile with 
	groff -m me -Tps file > out.ps && ps2pdf out.ps nice.pdf

needs -Tps option

Define short handles for proper formatting of results with units and spacing
	.EQ
	define mm '^ roman "mm"'
	.EN


Have letters show place and date right justified, then return to normal justification:
	.ad r
	Berlin, 22. März 2019
	.br
	.ad b

Turn on line numbering
	.nm a b
where a is the starting number and b is the increment
turn off line numbering with .nm without any arguments
