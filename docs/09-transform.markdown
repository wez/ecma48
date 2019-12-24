## 9. TRANSFORMATION BETWEEN 7-BIT AND 8-BIT CODED REPRESENTATIONS

The control functions defined in this Standard can be coded in a 7-bit code as
well as in an 8-bit code; both forms of coded representation are equivalent and
in accordance with ECMA-35.

However, when data containing these control functions are transformed from a
7-bit to an 8-bit coded representation or vice versa, the transformation
algorithm specified in ECMA-35 may produce results which are formally in
disagreement with this Standard.

In order to make allowance for such unintended but unavoidable deviations, the
format rules are extended in the manner described below.

In an 8-bit code, the bit combinations of columns 10 to 15 (except 10/0 and
15/15) are permitted to represent:

- parameters, intermediates and finals of a control sequence;
- the contents of a control string;
- the operand of a single-shift character.

In these situations, the bit combinations in the range 10/1 to 15/14 have the
same meanings as the corresponding bit combinations in the range 2/1 to 7/14.

In a 7-bit code, the control characters SHIFT-OUT (SO) and SHIFT-IN (SI) are
permitted to occur:

- between the CONTROL SEQUENCE INTRODUCER (CSI) and the final bit combination
  of a control sequence;
- between the opening delimiter of a control string and the STRING TERMINATOR (ST);
- between a single-shift character and its operand.

SHIFT-OUT and SHIFT-IN have no effect on the interpretation of a control
sequence, a control string or the operand of a single-shift character, but they
may indeed affect the meanings of bit combinations following in the data
stream.


