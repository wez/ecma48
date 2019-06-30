## APPENDIX A: EDITOR FUNCTIONS AND FORMAT EFFECTORS

### A.1 Correspondence between editor functions and format effectors

Table 6 shows on the same line editor functions and format effectors with
similar functions. The notation (s), (n) or (n;m) following an abbreviation
indicates that the control function is represented by a control sequence with a
selective parameter, one numeric parameter, or two numeric parameters.  An
abbreviation without such a notation indicates that the control function is an
element of the CO or C1 set. Format effectors from Standard ECMA-6 are also
included. Where there is only one entry on a single line, there is no control
function corresponding to the one shown.

| Editor Function | Format Effector |
| --------------- | --------------- |
| CBT (n)         |                 |
| CHA (n)         | CR, HPA (n)     |
| CHT (n)         | HT              |
| CNL (n)         | NEL, NL         |
| CPL (n)         |                 |
| CTC (s)         | HTS, TBC (s), VTS |
| CUB (n)         | BS                |
| CUD (n)         | IND, LF, VPR (n)  |
| CUF (n)         | HPR (n), SP       |
| CUP (n;m)       | HVP (n;m)         |
| CUU (n)         | RI                |
| CVT (n)         | VT                |
| DCH (n)         |                   |
| DL (n)          |                   |
| EA (s)          |                   |
| ECH (n)         |                   |
| ED (s)          |                   |
| EF (s)          |                   |
| EL (s)          |                   |
|                 | FNT (n;m)         |
|                 | GSM (n;m)         |
|                 | GSS (n)           |
|                 | HTJ               |
|ICH (n)          |                   |
| IL (n)          |                   |
|                 | JFY (s)           |
| NP (n)          | FF                |
|                 | PLD               |
|                 | PLU               |
|PP (n)           |                   |
|                 | QUAD (s)          |
|                 | SGR (s)           |
|                 | SPI (n;m)         |
| SD (n)          |                   |
| SL (n)          |                   |
| SR (n)          |                   |
|                 | SSU (s)           |
| SU (n)          |                   |
|                 | TSS (n)           |
|                 | VPA (n)           |

TABLE 6: CORRESPONDENCE BETWEEN EDITOR FUNCTIONS AND FORMAT EFFECTORS

### A.2 Differences between editor functions and format effectors

The contrast between editor functions and format effectors, together with their
interaction with certain modes, is illustrated by the following example of the
use of the control functions CURSOR NEXT LINE (CNL) and NEXT LINE (NEL).

In the example it is assumed that the string of capital letters:

```
A B C D E F
```

has been entered or received, and that the active position has been moved back
to the letter `D`, e.g. by-means of CURSOR BACKWARDS (CUB). Starting from this
situation, the following cases are considered.

**Case 1**: A CURSOR NEXT LINE (CNL) is received. In this case, the active
position is moved to the beginning of the next line without affecting the
previously received data.

**Case 2**: The FORMAT EFFECTOR ACTION MODE being set to EXECUTE, a NEXT LINE
(NEL) is received. This has the same effect as in case 1).

**Case 3**: The FORMAT EFFECTOR ACTION MODE being set to STORE and the
INSERTION REPLACEMENT MODE to REPLACE, a NEXT LINE (NEL) is received. In this
case, the letter D is replaced by NEL.  If the data is subsequently forwarded
to another device operating with the FORMAT EFFECTOR ACTION MODE being set to
EXECUTE, the effect is:

```
A B C
E F
```

**Case 4**: The FORMAT EFFECTOR ACTION MODE being set to STORE and the
INSERTION REPLACEMENT MODE to INSERT, a NEXT LINE (NEL) is received. In this
case, the NEL is inserted between the letters C and D. If the data is
subsequently forwarded to another device operating with the FORMAT EFFECTOR
ACTION MODE being set to EXECUTE, the effect is:

```
A B C
D E F
```

Format effectors which have been received while the FORMAT
EFFECTOR ACTION MODE is set to STORE can be operated upon with
editing functions.

For example, the NEL which has been inserted between A B C and
D E F in case 4) can be deleted using DELETE CHARACTER
(DCH), resulting in the initial situation being restored.

### A.3 Composite graphic characters

Because the format effectors can be stored in a receiving device, as opposed to
the editor functions which are immediately performed, format effectors rather
than editor functions should be used for the construction of composite
graphics.

For example, if the symbol <tt>&ne;</tt> is to be composed using `=` (EQUALS SIGN) and `/`
(SOLIDUS), the sequence:

```
= CUB /
```

does not produce the desired effect if received by a device which has no
overstrike capability. Such a device may, however, process the sequence:

```
= BS /
```

in such a way that it is preserved and can be forwarded to a device which can
indeed produce the intended composite symbol.


