## APPENDIX C TEXT COMPOSITION DEVICE CONCEPTS

Display devices and systems involving text composition may utilize the control
functions JUSTIFY and QUAD. When working in the field of text composition
several words are used with quite specialized meaning. Those words have been
used in this Standard with the meaning from the terminology of the printing and
publishing industry.  Explanation is provided in this Annex in terms compatible
with coded information interchange and the concepts of character-imaging
devices.

Both QUAD and JUSTIFY deal with the positioning of text (printed graphics and
free spaces) between "margins". Margins are areas protected against display at
the boundaries of which lines of text may start and terminate. In the general
case of a display device with a multiple-page buffer (capable of the QUAD or
JUSTIFY functions) the margin(s) would be set at arbitrary absolute horizontal
positions. No control functions are provided in this Standard to set margins
(left, right, intermediate). The QUAD function deals with single lines of text
from the data stream, while the JUSTIFY function may deal with more than one
line. In both cases it is possible to "flush" text. When text is flush, it
starts or ends, as applicable, against a marginal boundary. Flush to left
margin means start text at the left margin (or first margin to the left in
columnar texts). Similarly, flush to right margin means end text at the right
margin. In the process of making text flush, open spaces may be generated.

The action to "fill" open spaces involves a concept particular to the JUSTIFY
and QUAD functions. The open spaces may be filled with a "leader" in the QUAD
function. A leader is a pattern (most often a repeated string of graphic
characters) which is inserted into the open area. In the use of the JUSTIFY
function the fill operation is far more complicated and will be described
below.

Having considered margins and flush text it is necessary to consider text which
is not intended to be flush to the margins. Text which meets this criterion
falls into two categories. They are centred text and ragged text. This Standard
deals explicitly with centred text and implicitly with ragged text. Centred
text is arranged between margins such that the open space to the left and right
margin are as equal as possible. Ragged is the term applied when text is
neither centred nor flush to a margin.

The process utilizing the JUSTIFY function involves the arrangement of text
between margins either being flush (explicitly) or ragged (implicitly). In
order to accomplish flush left and right, fill may be required. The fill may
consist of SPACEs, Thin Spaces, words, or part of words. For the purposes of
this description a word is considered as including the graphic characters of
the word itself and the punctuation or space terminating the word. The rules
regarding a specific justification process depend on the combination of the
parameter values used. A line which is to be justified left and right with word
fill will first be adjusted in length by the addition or removal of text in the
form of words until the remaining words fit between the established margins.
Words added to a line by such a process will be obtained from the data stream
from its following line(s). Words removed from the line will be returned to the
data stream in its following line(s). Subsequent to having sufficient words to
fit between margins the open space (between words) may be adjusted to
accomplish the combined flush-to-left-margin and flush to-right-margin action.
This ‘spacing is adjusted by the intervals, or variable-size spaces according
to the implementation. When the interword space parameter value has been used,
the spacing adjustment is applicable between words. When the letter space
parameter value has been used the spacing adjustment is applicable between
adjacent graphic characters. When either or both interword space and letter
space parameter values have been used the strategy for selecting which
positions are to be widened is implementation-dependent.  Special cases of the
above involve the use of partial words in the full process. In these cases a
hyphenation process is used. If the hyphenation parameter value is used, words
may be subdivided according to an implementation strategy at language intervals
often corresponding to syllables. If the Italian hyphenation parameter value is
used the first word which will not fit between the margins is truncated, the
last character of the line is underlined and the remainder of the word is
inserted in the data stream for use in the next line.


