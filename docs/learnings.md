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

# Proper input encoding for special characters and digraphs
Flag to recognize utf-8 symbols like umlauts (äüö) and greek letters (µ):
```
groff -K utf-8 ...
```
NOTE: On macOS Mojave the preinstalled version of groff (1.19.2?) does not recognize the `-K` option 
and will throw an error. The only way around it is to install a newer version using *homebrew*
```
brew install groff gs
```
(Not sure if the `gs` for *ghostscript* is required or not...)

ALSO: The utf-8 encoding will not work properly when you source separate files 
into your groff file like `.so chapter-one.txt`.
There is, however, a workaround for that case, too:
```
preconv chapter-one.txt > new-chapter-one.txt
```
Here, `preconv` does the (duh!) preconversion of the text file into something that 
groff can understand. Then by sourcing `.so new-chapter-one.txt` in the groff file,
everything will be *fiiiine*.


# MS macro needs on instance of .PP to make title page work properly.
Uh. Ok, I guess? If you want to make use of the title page functionality that comes 
with using the `-ms` macro package, make sure you have an indented paragraph (`.PP`) 
in your document. I'm not even sure anymore when I put this here, but right now I would
assume that this works with unindented paragraphs (or: leading paragraphs, `.LP`) as well.

# Proper listing of items with nice indentation when using MS macros
```
.RS
.IP \[bu] 2n
Item 1, bu for bulletin icon instead of -
.IP \[bu]
Item 2, 2n to adjust indentation after bulletin
.RE
```
Pretty straight forward.
In general, `.RS` stands for "right shift" - an thus shifts everything enclosed up until `.RE`
to the right. The second thing here is the `.IP` which is the general macro for any indented paragraph.
The bulletin might also be replaced by "1)" if you want to list a bunch of exercise problems for example.

# Sans Serif / Helvetica font in your document
(entire document):
```
.fp 1 H
```
(next line only)
```
.fam H
```

# Include EPS file
```
.PSPIC header.eps
```
compile with 
```
groff -m me -Tps file > out.ps && ps2pdf out.ps nice.pdf
```
- needs -Tps option

# Define short handles for proper formatting of results with units and spacing

```
.EQ
define mm '^ roman "mm"'
.EN
```

# Have letters show place and date right justified, then return to normal justification:
```
.ad r
Any City, March 22 2019
.br
.ad b
```

# Turn on line numbering
```
.nm a b
```
Here, `a` is the starting number and `b` is the increment.
Turn off line numbering with `.nm` without any arguments.
