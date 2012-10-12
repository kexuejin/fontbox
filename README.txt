
Apache FontBox separated from PdfBox for independent application.

The Apache FontBox library is an open source Java tool for working
with fonts.  Originally, FontBox is from http://pdfbox.apache.org/.

See src/org/apache/fontbox/ttf/Glyph2D.java (and
src/org/apache/fontbox/ttf/GlyfSimpleDescript.java) for the core of
this TTF glyph reader.

Unfortunately, this will not work for many TTF files.

The "TTF problem" is that the TTF writers employed by font authors are
not clear on the composition of glyph path data.  As a result, TTF
readers need to guess at the intention of the author and writer
through a convoluted series of heuristics.  Naturally, the most common
TTF readers' heuristics have become canonical.  The "ground zero" of
this issue was the Adobe TTF Font Rendering library, which adopted
heuristics rather than support the format.  Many others have since
reverse engineered this state of affairs.

A demonstration would pick Glyphs from TTF files found in the wild and
display their outlines.  This is trivial as the java.awt.Graphics2D
class will (scale and) draw the (Glyph2D) outline directly.

The search should not take too long before a broken glyph outline is
discovered.
