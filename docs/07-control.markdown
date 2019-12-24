## 7. CONTROL FUNCTIONS

### 7.1. Categories of Control Functions

The following list groups the control functions defined in this Standard. This
grouping is intended solely to aid in understanding the Standard and does not
restrict the control functions to the indicated categories.

This list also indicates the form of the control function by the following
notations following the abbreviation:

| Notation | Meaning |
| -------- | ------- |
| No sign  | the control function is an element of the C1 set. |
| (n)      | control sequence with one numeric parameter. |
| (n;m)    | control sequence with two numeric parameters. |
| (s)      | control sequence with selective parameter. |
| (Fs)     | ESC Fs sequence. |

#### 7.1.1. Control string delimiters

* `APC` APPLICATION PROGRAM COMMAND
* `OSC` OPERATING SYSTEM COMMAND
* `PM` PRIVACY MESSAGE
* `ST` STRING TERMINATOR
* `DCS` DEVICE CONTROL STRING

#### 7.1.2. Introducers

* `CSI` CONTROL SEQUENCE INTRODUCER

#### 7.1.3. Shift functions

* `SS2` SINGLE SHIFT 2
* `SS3` SINGLE SHIFT 3

#### 7.1.4. Format effectors

* `HPA (n)` HORIZONTAL POSITION ABSOLUTE
* `HPR (n)` HORIZONTAL POSITION RELATIVE
* `HT J` HORIZONTAL TABULATION WITH JUSTIFICATION
* `HTS` HORIZONTAL TABULATION SET
* `HVP (n;m)` HORIZONTAL AND VERTICAL POSITION
* `IND` INDEX
* `NEL` NEXT LINE
* `PLD` PARTIAL LINE DOWN
* `PLU` PARTIAL LINE UP
* `RI` REVERSE INDEX
* `SGR (s)` SELECT GRAPHIC RENDITION
* `TBC (s)` TABULATION CLEAR
* `VPA (n)` VERTICAL POSITION ABSOLUTE
* `VPR (n)` VERTICAL POSITION RELATIVE
* `VTS` VERTICAL TABULATION SET

#### 7.1.5. Additional format effectors for text composition devices

* `FNT (n;m)` FONT SELECTION
* `GSM (n;m)` GRAPHIC SIZE MODIFICATION
* `GSS (n)` GRAPHIC SIZE SELECTION
* `JFY  (s)` JUSTIFY
* `QUAD (s)` QUAD
* `SPI (n;m)` SPACING INCREMENT
* `SSU (s)` SELECT SIZE UNIT
* `TSS (n)` THIN SPACE SPECIFICATION

#### 7.1.6. Editor functions for altering the visual display

* `DCH (n)` DELETE CHARACTER
* `DL (n)` DELETE LINE
* `EA (s)` ERASE IN AREA
* `ECH (n)` ERASE CHARACTER
* `ED (s)` ERASE IN DISPLAY
* `EF (s)` ERASE IN FIELD
* `BL (s)` ERASE IN LINE
* `ICH (n)` INSERT CHARACTER
* `IL (n)` INSERT LINE

#### 7.1.7. Editor functions for moving the active position

* `CBT (n)` CURSOR BACKWARD TABULATION
* `CHA (n)` CURSOR HORIZONTAL ABSOLUTE
* `CHT (n)` CURSOR HORIZONTAL TABULATION
* `CNL (n)` CURSOR NEXT LINE
* `CPL (n)` CURSOR PRECEDING LINE
* `CTC (s)` CURSOR TABULATION CONTROL
* `CUB (n)` CURSOR BACKWARD
* `CUD (n)` CURSOR DOWN
* `CUF (n)` CURSOR FORWARD
* `CUP (n;m)` CURSOR POSITION
* `CUU (n)` CURSOR UP
* `CVT (n)` CURSOR VERTICAL TABULATION
* `NP (n)` NEXT PAGE
* `PP (n)` PRECEDING PAGE
* `SD (n)` SCROLL DOWN
* `SL (n)` SCROLL LEFT
* `SR (n)` SCROLL RIGHT
* `SU (n)` SCROLL UP

#### 7.1.8. Form filling

* `DAQ (s)` DEFINE AREA QUALIFICATION
* `EPA` END OF PROTECTED AREA
* `ESA` END OF SELECTED AREA
* `SPA` START OF PROTECTED AREA
* `SSA` START OF SELECTED AREA

#### 7.1.9. Mode setting

* `RM (s)` RESET MODE
* `SM (s)` SET MODE

#### 7.1.10. Miscellaneous control functions

* `CCH` CANCEL CHARACTER
* `CPR (n;m)` CURSOR POSITION REPORT
* `DA (n)` DEVICE ATTRIBUTES
* `DMI (Fs)` DISABLE MANUAL INPUT
* `DSR (s)` DEVICE STATUS REPORT
* `EMI (Fs)` ENABLE MANUAL INPUT
* `INT (Fs)` INTERRUPT
* `MC (s)` MEDIA COPY
* `MW` MESSAGE WAITING
* `PU1` PRIVATE USE ONE
* `PU2` PRIVATE USE TWO
* `REP (n)` REPEAT
* `RIS (Fs)` RESET TO INITIAL STATE
* `SEE (s)` SELECT EDITING EXTENT
* `STS` SET TRANSMIT STATE

### 7.2. Definition of Control Functions

The symbol `n` used hereafter denotes the value of a numeric parameter. If
there are two numeric parameters, `n` denotes the value of the first parameter
and the symbol `m` that of the second parameter. In the absence of a numeric or
selective parameter, the default value applies. Unassigned selective parameter
values are reserved for future standardization.

#### 7.2.1. APC - APPLICATION PROGRAM COMMAND

Representation: Table 1

APC is the opening delimiter of a command string for an application program.
The command string consists of a sequence of bit combinations of columns 2 to 7
(except 7/15) and is closed by STRING TERMINATOR (ST) as a terminating
delimiter. The interpretation of the command string depends on the relevant
application program. This control function may need to be represented by a
graphic symbol.

#### 7.2.2. CBT - CURSOR BACKWARD TABULATION

Representation: Table 2 - one numeric parameter; default value: 1

The active position is moved to the character position corresponding to the
n-th preceding horizontal tabulation stop.

#### 7.2.3. CCH - CANCEL CHARACTER

Representation: Table 1

CCH indicates that the preceding graphic or control function of the data
stream, represented by a single bit combination, an escape sequence, a single
shift sequence or a control sequence, but not by a control string, is to be
ignored.

#### 7.2.4. CHA - CURSOR HORIZONTAL ABSOLUTE

Representation: Table 2 - one numeric parameter; default
Value: 1

The active position is moved to the n-th character position of the active line.

#### 7.2.5. CHT - CURSOR HORIZONTAL TABULATION

Representation: Table 2 - one numeric parameter; default value: 1

The active position is moved to the character position corresponding to the
n-th following horizontal tabulation stop.

#### 7.2.6. CNL - CURSOR NEXT LINE

Representation: Table 2 - one numeric parameter; default value: 1

The active position is moved to the first character position of the n-th
following line.

#### 7.2.7. CPL - CURSOR PRECEDING LINE

Representation: Table 2 - one numeric parameter: default value: 1

The active position is moved to the first character position of the n-th
preceding line.

#### 7.2.8. CPR - CURSOR POSITION REPORT

Representation: Table 2 - two numeric parameters; default values: 1;1

CPR reports the active position of the sending device as residing on the n-th
line at the m-th character position.

CPR may be solicited by a DSR or unsolicited.

#### 7.2.9. CSI - CONTROL SEQUENCE INTRODUCER

Representation: Table 1

CSI is the first character of a control sequence (see 4.3).

#### 7.2.10. CTC - CURSOR TABULATION CONTROL

Representation: Table 2 - selective parameter; default value: 0

CTC causes one or more tabulation stops to be set or cleared, depending on the
parameter value:

| value | meaning |
| ----- | ------- |
| 0     | set a horizontal tabulation stop at the active position |
| 1     | set a vertical tabulation stop at the active line |
| 2     | clear the horizontal tabulation stop at the active position |
| 3     | clear the vertical tabulation stop at the active line |
| 4     | clear all horizontal tabulation stops at the active line |
| 5     | clear all horizontal tabulation stops |
| 6     | clear all vertical tabulation stops |

In case of parameter values 0,2 or 4, when horizontal tabulation stops are set
or cleared, the number of lines affected depends on the setting of the
TABULATION STOP MODE.

#### 7.2.11. CUB - CURSOR BACKWARD

Representation: Table 2 - one numeric parameter; default value: 1

The active position is moved to the n-th preceding character position.

#### 7.2.12. CUD - CURSOR DOWN

Representation: Table 2 - one numeric parameter; default value: 1

The active position is moved to the corresponding character position of the
n-th following line.

#### 7.2.13. CUF - CURSOR FORWARD

Representation: Table 2 - one numeric parameter; default value: 1

The active position is moved to the n-th following character position.

#### 7.2.14. CUP - CURSOR POSITION

Representation: Table 2 - two numeric parameters; default values: 1;1

The active position is moved to the n-th line at the m-th character position.
(The default values define the so-called home position.)

#### 7.2.15. CUU - CURSOR UP

Representation: Table 2 - one numeric parameter; default value: 1

The active position is moved to the corresponding character position of the
n-th preceding line.

#### 7.2.16. CVT - CURSOR VERTICAL TABULATION

Representation: Table 2 - one numeric parameter; default value: 1

The active position is moved to the corresponding character position of the
line corresponding to the n-th following vertical tabulation stop.

#### 7.2.17. DA - DEVICE ATTRIBUTES

Representation: Table 2 - one numeric parameter; default value: 0

With a parameter value not equal to 0, DA identifies the sending device. The
parameter value is a device type identification code according to some register
which is to be established. If the parameter value is 0, DA is used to solicit
an identifying DA from the receiving device.

#### 7.2.18. DAQ - DEFINE AREA QUALIFICATION

Representation: Table 2 - selective parameter; default value: 0

DAQ indicates that the active position is the first character position of a
qualified area. The end of the qualified area is indicated by the beginning of
the following qualified area.

The parameter value designates the type of qualified area:

| value | meaning |
| ----- | ------- |
| 0     | unprotected |
| 1     | guarded (implies protected) |
| 2     | graphic character input |
| 3     | numeric input |
| 4     | alphabetic input |
| 5     | input to be justified to the right |
| 6     | fill with ZEROs |
| 7     | set horizontal tabulation stop at start of area |
| 8     | protected (unguarded) |
| 9     | fill with SPACEs |

This control function operates independently of the setting of the TABULATION
STOP MODE; the horizontal tabulation stop set by parameter value 7 applies to
the active line only.

#### 7.2.19. DCH - DELETE CHARACTER

Representation: Table 2 - one numeric parameter; default value: 1

The contents of the active position and the n-1 preceding or following
character positions are removed, depending on the setting of the HORIZONTAL
EDITING MODE. The contents of an adjacent string of character positions are
shifted towards the active position. At the other end of the shifted string n
character positions are erased.

The position and the extent of the string affected by the deletion depend on
the setting of the EDITING BOUNDARY MODE and of the HORIZONTAL EDITING MODE,
and on the extent established by SELECT EDITING EXTENT (SEE).

The effect of this control on the start or end of a selected area, start or end
of a qualified area, or a tabulation stop in the shifted string is not defined
by this Standard.

#### 7.2.20. DCS - DEVICE CONTROL STRING

Representation: Table 1

DCS is the opening delimiter of a device control string.  The device control
string consists of a sequence of bit combinations of columns 2 to 7 (except
7/15) and is closed by the terminating delimiter STRING TERMINATOR (ST).

The device control string represents either one or more control commands for
the receiving device, or one or more status reports from the sending device.
The interpretation of the device control string depends on the sending and/or
the receiving device. This control function may need to be representated by a
graphic symbol.

#### 7.2.21. DL - DELETE LINE

Representation: Table 2 - one numeric parameter; default value: 1

The contents of the active line and the n-1 preceding or following lines are
removed, depending on the setting of the VERTICAL EDITING MODE. The contents of
a number of preceding or following lines are shifted towards the active line.
At the other end of the shifted part n lines are erased. The extent of the data
affected by the deletion depends on the setting of the EDITING BOUNDARY MODE.

Any occurrences of the start or end of a selected area, the start or end of a
qualified area, or a tabulation stop in the shifted part are also shifted.

If the TABULATION STOP MODE is set to SINGLE, horizontal tabulation stops in
the erased lines are cleared.

The effect of DL on the active position is not defined by this Standard.

#### 7.2.22. DMI - DISABLE MANUAL INPUT

Representation: Table 4

A control function which causes all or part of the manual input facilities of
the receiving device to be disabled.

**NOTE 6**: This control function does not apply to those parts of the manual
input facilities which are disabled by the setting of the KEYBOARD ACTION MODE.

#### 7.2.23. DSR - DEVICE STATUS REPORT

Representation: Table 2 - selective parameter; default value: 0

DSR either reports the status of the sending device or requests a status report
from the receiving device, depending on the parameter value:

| value | meaning |
| ----- | ------- |
| 0     | ready, no malfunction detected |
| 1     | busy, another DSR must be requested later |
| 2     | busy, another DSR will be sent later |
| 3     | some malfunction detected, another DSR must be requested later |
| 4     | some malfunction detected, another DSR will be sent later |
| 5     | a DSR is requested |
| 6     | a report of the active position in the form of a CPR is requested. |

DSR with parameter value 0, 1, 2, 3 or 4 may be sent either unsolicited or as a
response to a request such as a DSR with a parameter value 5 or MESSAGE WAITING
(MW).

#### 7.2.24. EA - ERASE IN AREA

Representation: Table 2 - selective parameter; default value: 0

Some or all character positions of the active qualified area, i.e. the
qualified area in which the active position resides, are erased, depending on
the parameter value:

| value | meaning |
| ----- | ------- |
| 0     | the active position and the character positions up to the end of the qualified area are erased |
| 1     | the character positions from the beginning of the qualified area up to and including the active position are erased |
| 2     | all character positions of the qualified area are erased. |

The extent of the string affected by the erasure depends on the setting of the
EDITING BOUNDARY MODE. Whether protected areas are erased, or unprotected areas
only, depends on the setting of the ERASURE MODE.

#### 7.2.25. ECH - ERASE CHARACTER

Representation: Table 2 - one numeric parameter; default value; 1

The active position and the n-1 following character positions are erased. The
extent of the string affected by the erasure depends on the setting of the
EDITING BOUNDARY MODE,

Whether protected areas are erased, or unprotected areas only, depends on the
setting of the ERASURE MODE.

#### 7.2.26. ED - ERASE IN DISPLAY

Representation: Table 2 - selective parameter; default value: 0

Some or all character positions of the active page, i.e.  the page in which the
active position resides, are erased, depending on the parameter value:

| value | meaning |
| ----- | ------- |
| 0     | the active position and the character positions up to the end of the page are erased |
| 1     | the character positions from the beginning of the page up to and including the active position are erased |
| 2     | all character positions of the page are erased. |

The extent of the string affected by the erasure depends on the setting of the
EDITING BOUNDARY MODE.

Whether protected areas are erased, or unprotected areas only, depends on the
setting of the ERASURE MODE.

#### 7.2.27. EF - ERASE IN FIELD

Representation: Table 2 - selective parameter, default value: 0

Some or all character positions of the active field, i.e.  the field in which
the active position resides, are erased, depending on the parameter value:

| value | meaning |
| ----- | ------- |
| 0     | the active position and the character positions up to the end of the field are erased |
| 1     | the character positions from the beginning of the field up to and including the active positions are erased |
| 2     | all character positions of the field are erased. |

The extent of the string affected by the erasure depends on the setting of the
EDITING BOUNDARY MODE.

Whether protected areas are erased, or unprotected areas only, depends on the
setting of the ERASURE MODE.

#### 7.2.28. EL - ERASE IN LINE

Representation: Table 2 - selective parameter; default value: 0

Some or all character positions of the active line are
erased, depending on the parameter value:

| value | meaning |
| ----- | ------- |
| 0     | the active position and the character positions up to the end of the line are erased |
| 1     | the character positions from the beginning of the line up to and including the active positions are erased |
| 2     | all character positions of the line are erased. |

The extent of the string affected by the erasure depends on the setting of the
EDITING BOUNDARY MODE.

Whether protected areas are erased, or unprotected areas only, depends on the
setting of the ERASURE MODE.

#### 7.2.29. EMI - ENABLE MANUAL INPUT

Representation: Table 4

EMI enables the manual input facilities of the receiving device to be used.

**NOTE 7**: This control function does not apply to those parts of the manual
input facilities which are disabled by the setting of the KEYBOARD ACTION MODE.

#### 7.2.30. EPA - END OF PROTECTED AREA

Representation: Table 1

EPA indicates that the active position is the end of a string of character
positions, the contents of which are protected against manual alteration and
are guarded against transmission. The beginning of this string is indicated by
START OF PROTECTED AREA (SPA).

#### 7.2.31. ESA - END OF SELECTED AREA

Representation: Table 1

ESA indicates that the active position is the end of a string of character
positions, the contents of which are eligible to be transmitted in the form of
a data stream or transferred to an auxiliary input/output device. The beginning
of this string is indicated by START OF SELECTED AREA (SSA).

#### 7.2.32. FNT - FONT SELECTION

Representation: Table 3 - two numeric parameters; default values: 0;0.

FNT is a format effector which designates the character font invoked as primary
or alternative font by SELECT GRAPHIC RENDITION (SGR). n specifies the primary
or alternative font concerned:

| value | meaning |
| ----- | ------- |
| 0     | primary font |
| 1     | first alternative font |
| 2     | second alternative font |
| ..    |         |
| 9     | ninth alternative font |

`m` identifies the character font to be designated according to some register
which is to be established.

#### 7.2.33. GSM - GRAPHIC SIZE MODIFICATION

Representation: Table 3 - two numeric parameters; default values: 100;100

GSM is a format effector which causes the height and/or the width of all
designated primary and alternative fonts, as established by GRAPHIC SIZE
SELECTION (GSS), to be modified, until the following occurrence of either GSM
or GSS in the data stream.

`n` specifies the percentage by which the height is to be multiplied.

`m` specifies the percentage by which the width is to be multiplied.

GSM affects only those characters which follow it in the data stream, not those
previously received.

#### 7.2.34. GSS - GRAPHIC SIZE SELECTION

Representation: Table 3 - one numeric parameter; no default value.

GSS is a format effector which causes the height and the width of all
designated primary and alternative fonts to be established, until the following
occurrence of GSS in the data stream. Where n specifies the height; the width
is implicitly defined by the height. The unit in which n is expressed is that
established by SELECT SIZE UNIT (SSU).  GSS affects only those characters which
follow it in the data stream, not those previously received.

#### 7.2.35. HPA - HORIZONTAL POSITION ABSOLUTE

Representation: Table 2 - one numeric parameter; default value: 1

HPA is a format effector which causes the active position to be moved to the
n-th horizontal position of the active line.

The unit in which n is expressed depends on the setting of the POSITIONING UNIT
MODE.

#### 7.2.36. HPR - HORIZONTAL POSITION RELATIVE

Representation: Table 2 - one numeric parameter; default value: 1

HPR is a format effector which causes the active position to be moved to the
n-th following horizontal position.

The unit in which n is expressed depends on the setting of the POSITIONING UNIT
MODE.

#### 7.2.37. HTJ - HORIZONTAL TABULATION WITH JUSTIFICATION

Representation: Table 1

HTJ is a format effector which causes the contents of the string of character
positions between the preceding horizontal tabulation stop and the active
position to be shifted forward to the following horizontal tabulation stop.

The active position is also moved to the following horizontal tabulation stop.
The character positions between the preceding horizontal tabulation stop and
the beginning of the shifted string are erased.

#### 7.2.38. HTS - HORIZONTAL TABULATION SET
Representation: Table 1

HTS is a format effector which causes a horizontal tabulation stop to be set at
the active position.

The number of lines affected depends on the setting of the TABULATION STOP
MODE.

#### 7.2.39. HVP - HORIZONTAL AND VERTICAL POSITION

Representation: Table 2 - two numeric parameters; default values: 1;1

HVP is a format effector which causes the active position to be moved to the
n-th vertical position at the m-th horizontal position. The unit in which n and
m are expressed depends on the setting of the POSITIONING UNIT MODE.

#### 7.2.40. ICH - INSERT CHARACTER

Representation: Table 2 - one numeric parameter; default value: 1

`n` erased character positions are inserted at the active position. The
previous contents of the active position and an adjacent string of character
positions are shifted away from the active position. The contents of n
character positions at the other end of the shifted string are removed.

The position and the extent of the string affected by the insertion depend on
the setting of the EDITING BOUNDARY MODE and of the HORIZONTAL EDITING MODE,
and on the extent established by SELECT EDITING EXTENT (SEE). The effect of
this control function on the start or end of a selected area, the start or end
of a qualified area, or a tabulation stop in the shifted string is not defined
by this Standard.

#### 7.2.41. IL - INSERT LINE

Representation: Table 2 - one numeric parameter; default value: 1

`n` erased lines are inserted at the active line. The previous contents of the
active line and a number of preceding or following lines are shifted away from
the active line, depending on the setting of the VERTICAL EDITING MODE. The
extent of the part affected by the insertion depends on the setting of the
EDITING BOUNDARY MODE. The contents of n lines at the end of the shifted part
are removed.

Any occurrences of the start or end of a selected area, the start or end of.a
qualified area, or a tabulation stop in the shifted part are also shifted.

If the TABULATION STOP MODE is set to SINGLE, horizontal tabulation stops in
the erased lines are cleared.

The effect of this control function on the active position is not defined by
this Standard.

#### 7.2.42. IND - INDEX
Representation: Table 1

IND is a format effector which causes the active position to be moved to the
corresponding character position of the following line.

#### 7.2.43. INT - INTERRUPT
Representation: Table 4

INT indicates to the receiving device that the current process is to be
interrupted and an agreed procedure is to be initiated. This control function
is applicable to either direction of transmission.

#### 7.2.44. JFY - JUSTIFY

Representation: Table 3 - selective parameter, default value: 0

JFY is a format effector which indicates the beginning of a string of character
positions, the contents of which are to be justified according to the layout
specified by the parameter value (see Annex C)

| value | meaning |
| ------| ------- |
| 0     | end of justification |
| 1     | word fill |
| 2     | interword space |
| 3     | letter space |
| 4     | hyphenation |
| 5     | flush to left margin |
| 6     | centre between margins |
| 7     | flush to right margin |
| 8     | Italian hyphenation |

JFY affects only those characters which follow it in the data stream, not those
previously received. The end of the string to be justified is indicated by the
next occurrence of JFY in the data stream.

#### 7.2.45. MC - MEDIA COPY

Representation: Table 2 - selective parameter; default value: 0

MC controls the transfer of data from or to an auxiliary input/output device.
It either indicates a transfer of data from or to an auxiliary input/output
device or enables or disables the received data stream to be relayed to an
auxiliary input/output device depending on the parameter value:

| value | meaning |
| ----- | ------  |
| 0     | initiate transfer to primary auxiliary device |
| 1     | initiate transfer from primary auxiliary device |
| 2     | initiate transfer to secondary auxiliary device |
| 3     | initiate transfer from secondary auxiliary device |
| 4     | stop relay to primary auxiliary device |
| 5     | start relay to primary auxiliary device |
| 6     | stop relay to secondary auxiliary device |
| 7     | start relay to secondary auxiliary device |

This control function is not intended to switch on and off an auxiliary device.

#### 7.2.46. MW - MESSAGE WAITING

Representation: Table 1

MW causes a message waiting indicator to be set in the receiving device. An
appropriate acknowledgement to the receipt of MW may be given by DEVICE STATUS
REPORT (DSR).

#### 7.2.47. NEL - NEXT LINE

Representation: Table 1

NEL is a format effector which causes the active position to be moved to the
first character position of the following line.

#### 7.2.48. NP - NEXT PAGE

Representation: Table 2 - one numeric parameter; default value: 1

The n-th following page of a multiple-page buffer is displayed. The effect of
this control function on the active position is not defined by this Standard.

#### 7.2.49. OSC - OPERATING SYSTEM COMMAND

Representation: Table 1

OSC is the opening delimiter of a command string for an operating system. The
command string consists of a sequence of bit combinations of column 2 to 7
(except 7/15) and is closed by the terminating delimiter STRING TERMINATOR
(ST).  The interpretation of the command string depends on the relevant
operating system.

This control function may need to be represented by a graphic symbol.

#### 7.2.50. PLD - PARTIAL LINE DOWN
Representation: Table 1

PLD is a format effector which causes the active position to be moved to the
corresponding character position of an imaginary line with a partial vertical
offset. This offset should be sufficient either to image following characters
as subscripts until the first following occurrence of PARTIAL LINE UP (PLU) in
the data stream, or, if the immediately preceding character is imaged as a
superscript to restore subsequent imaging of characters to the active line.

Any interactions between PLD and vertical format effectors other than PLU are
not defined by this Standard.

#### 7.2.51. PLU - PARTIAL LINE UP
Representation: Table 1

PLU is a format effector which causes the active position to be moved to the
corresponding character position of an imaginary line with a partial vertical
offset. This offset should be sufficient either to image following characters
as superscripts until the first following occurrence of PARTIAL LINE DOWN (PLD)
in the data stream, or, if the immediately preceding character is imaged as a
subscript, to restore subsequent imaging of characters to the active Line.

Any interactions between PLU and vertical format effectors other than PLD are
not defined by this Standard.

#### 7.2.52. PM - PRIVACY MESSAGE
Representation: Table 1

PM is the opening delimiter of a privacy message. The privacy message consists
of a sequence of bit combinations of columns 2 to 7 (except 7/15) and is closed
by the terminating delimiter STRING TERMINATOR (ST). The interpretation of the
privacy message depends on the relevant privacy discipline.

This control function may need to be represented by a graphic symbol.

#### 7.2.53. PP - PRECEDING PAGE

Representation: Table 2 - one numeric parameter; default value: 1

The n-th preceding page of a multiple-page buffer is displayed.

The effect of this control function on the active position is not defined by
this Standard.

#### 7.2.54. PU1 - PRIVATE USE 1
Representation: Table 1

PU1 is reserved for a function without standardized meaning for private use as
required, subject to the prior agreement of the sender and the recipient of the
data.

#### 7.2.55. PU2 - PRIVATE USE 2
Representation: Table 1

PU2 is reserved for a function without standardized meaning for private use as
required, subject to the prior agreement of the sender and the recipient of the
data.

#### 7.2.56. QUAD - QUAD

Representation: Table 3 - selective parameter; default value: 0

QUAD is a format effector which indicates the end of a string of character
positions in the data stream, the contents of which are to be positioned on a
single line according to the layout specified by the parameter value (see Annex
C):

| value | meaning |
| ------| ------- |
| 0     | flush to left margin |
| 1     | flush to left margin and fill with leader |
| 2     | centre between margins |
| 3     | centre between margins and fill with leader |
| 4     | flush to right margin |
| 5     | flush to right margin and fill with leader |

The beginning of the string to be positioned is indicated by the preceding
occurrence of either QUAD or one of the following vertical format effectors:
FF, HVP, IND, LF, NEL, RI, VPA, VPR or VT in the data stream.

#### 7.2.57. REP - REPEAT

Representation: Table 2 - one numeric parameter; default value: 1

The preceding graphic or the effect of the preceding control function in the
data stream (if this control function is represented by a single bit
combination, an escape sequence, a single shift sequence or a control sequence,
but not by a control string) is repeated n times.

#### 7.2.58. RI - REVERSE INDEX
Representation: Table 1

RI is a format effector which causes the active position to be moved to the
corresponding character position of the preceding line.

#### 7.2.59. RIS - RESET TO INITIAL STATE

Representation: Table 4

RIS resets a device to its initial state, i.e. the state it has after it is
switched on. This may imply, if applicable: remove tabulation stops, remove
qualified areas, reset graphic rendition, erase all positions, move active
position to first character position of first line.

#### 7.2.60. RM - RESET MODE

Representation: Table 2 - selective parameter, no default value

RM. resets the modes of the receiving device specified by the parameter value
(see SET MODE, SM).

#### 7.2.61. SD - SCROLL DOWN

Representation: Table 2 - one numeric parameter, default value: 1

The displayed portion of a multiple-page buffer is moved by n lines such that
the displayed data appear to move down.

The effect of this control function on the active position is not defined by
this Standard.

#### 7.2.62. SEE - SELECT EDITING EXTENT

Representation: Table 2 - selective parameter; default
value: 0

SEE establishes the editing extent for character insertion
or deletion, depending on the parameter value:

| value | meaning |
| ----- | --------|
| 0     | The affected string consists of the entire buffer, or the displayed portion, depending on the setting of the EDITING BOUNDARY MODE |
| 1     | The affected string consists of the active line |
| 2     | The affected string consists of the data between the preceding and the following horizontal tabulation stop |
| 3     | The affected string consists of the qualified area containing the active position |

#### 7.2.63. SGR - SELECT GRAPHIC RENDITION

Representation: Table 2 - selective parameter; default value: 0

SGR is a format effector which indicates the beginning of a string of character
positions in the data stream, the contents of which are to be rendered in a
discernable, uniformly different way. The end of this string is indicated by
the following occurrence of SGR in the data stream. The graphic rendition is
specified by a parameter value:

| value | meaning |
| ----- | ------- |
| 0     | default rendition (implementation-defined) |
| 1     | bold or increased intensity |
| 2     | faint, decreased intensity or second color |
| 3     | italics |
| 4     | underlined |
| 5     | slowly blinking (less than 150 per minute) |
| 6     | rapidly blinking (150 per minute or more) |
| 7     | negative image |
| 8     | concealed data |
| 9     | (reserved for future standardization) |
| 10    | primary font |
| 11    | first alternative font |
| ..    | |
| 19    | ninth alternative font |
| 20    | fraktur |
| 21 to 29 | (reserved for future standardization) |
| 30    | black display |
| 31    | red display |
| 32    | green display |
| 33    | yellow display |
| 34    | blue display |
| 35    | magenta display |
| 36    | cyan display |
| 37    | white display |
| 38    | (reserved for future standardization) |
| 39    | (reserved for future standardization) |
| 40    | black background |
| 41    | red background |
| 42    | green background |
| 43    | yellow background |
| 44    | blue background |
| 45    | magenta background |
| 46    | cyan background |
| 47    | white background |

##### 7.2.64. SL - SCROLL LEFT

Representation: Table 3 - one numeric parameter; default value: 1

The displayed portion of a multiple-page buffer is moved by n character
positions such that the displayed data appear to move to the left.

The effect of this control on the active position is not defined by this
Standard.

#### 7.2.65. SM - SET MODE

Representation: Table 2 - selective parameter; no default value

SM sets the modes of the receiving device specified by the parameter value:

| value | meaning |
| ----- | ------- |
| 1     | GUARDED AREA TRANSFER MODE  |
| 2     | KEYBOARD ACTION MODE |
| 3     | CONTROL REPRESENTATION MODE |
| 4     | INSERTION - REPLACEMENT MODE |
| 5     | STATUS REPORT TRANSFER MODE |
| 6     | ERASURE MODE |
| 7     | VERTICAL EDITING MODE |
| 8     | (reserved for future standardization) |
| 9     | (reserved for future standardization) |
| 10    | HORIZONTAL EDITING MODE |
| 11    | POSITIONING UNIT MODE |
| 12    | SEND/RECEIVE MODE |
| 13    | FORMAT EFFECTOR ACTION MODE |
| 14    | FORMAT EFFECTOR TRANSFER MODE |
| 15    | MULTIPLE AREA TRANSFER MODE |
| 16    | TRANSFER TERMINATION MODE |
| 17    | SELECTED AREA TRANSFER MODE |
| 18    | TABULATION STOP MODE |
| 19    | EDITING BOUNDARY MODE |

#### 7.2.66. SPA - START OF PROTECTED AREA

Representation: Table 1

SPA indicates that the active position is the first of a string of character
positions, the contents of which are protected against manual alteration and
are guarded against transmission. The end of this string is indicated by END OF
PROTECTED AREA (EPA).

#### 7.2.67. SPI - SPACING INCREMENT

Representation: Table 3 - two numeric parameters; no default values

SPI is a format effector which causes the interline spacing and the width of a
horizontal space to be established, for characters following in the data
stream, until the next occurrence of SPI in the data stream.

`n` specifies the interline spacing; `m` specifies the width of a fixed
horizontal space.

The unit in which n and m are expressed is that established by SELECT SIZE UNIT
(SSU).

#### 7.2.68. SR - SCROLL RIGHT

Representation: Table 3 - one numeric parameter; default Value: 1

The displayed portion of a multiple-page buffer is moved by n character
positions such that the displayed data appear to move to the right.

The effect of this control function on the active position is not defined by
this Standard.

#### 7.2.69. SS2 - SINGLE SHIFT 2

Representation: Table 1

SS2 alters the meaning of the single bit combination following it. That bit
combination must be one of those from columns 2 to 7 except 2/0 and 7/15
(however, see 9). The meaning of the bit combination concerned is derived from
an appropriately designated G2 graphic set.

#### 7.2.70. SS3 - SINGLE SHIFT 3
Representation: Table 1

SS3 alters the meaning of the single bit combination following it. That bit
combination must be one of those from columns 2 to 7 except 2/0 and 7/15
(however, see 9). The meaning of the bit combination concerned is derived from
an appropriately designated G3 graphic set.

#### 7.2.71. SSA - START OF SELECTED AREA
Representation: Table 1

SSA indicates that the active position is the first of a string of character
positions, the contents of which are eligible to be transmitted in the form of
a data stream or transferred to an auxiliary input/output device. The end of
this string is indicated by END OF SELECTED AREA (ESA). The string of
characters actually transmitted or transferred depends on the setting of the
GUARDED AREA TRANSFER MODE and on any guarded areas established by START OF
PROTECTED AREA (SPA) or DEFINE AREA QUALIFICATION (DAQ). (See 6.3).

#### 7.2.72. SSU - SELECT SIZE UNIT

Representation: Table 3 - selective parameter; no default value

SSU is a format effector which establishes the unit in which the numeric
parameters of the positioning format effectors are expressed when the
POSITIONING UNIT MODE is set to SIZE. SSU also establishes the unit for GSS,
SPI and TSS. The unit established remains effective until the occurrence of
another SSU in the data stream. The parameter values are:

| value | meaning |
| ------|---------|
| 1     | INTERNATIONAL TYPOGRAPHIC STANDARD - (This unit is not yet standardized) |
| 2     | DECIPOINT - 0,0353 mm (1/720 inch) |
| 3     | DIDOT - 0,0376 mm |
| 4     | MIL - 0,0254 mm (1/1000 inch) |
| 5     | METRIC - 0,01 mm |

#### 7.2.73. ST - STRING TERMINATOR

Representation: Table 1

ST is the closing delimiter of a string opened by APPLICATION PROGRAM COMMAND
(APC), DEVICE CONTROL STRING (DCS), OPERATING SYSTEM COMMAND (OSC), or PRIVACY
MESSAGE (PM).

This control function may need to be represented by a graphic symbol.

#### 7.2.74. STS - SET TRANSMIT STATE
Representation: Table 1

STS causes the transmit state to be established in the receiving device. In
this state the transmission of data from the device is possible.

The actual initiation of transmission of data is performed by a data
communication or input/output interface control procedure which is outside the
scope of this Standard.

The transmit state is established either by the operation of an appropriate
button on a keyboard or by SET TRANSMIT STATE (STS) appearing in the received
data stream.

#### 7.2.75. SU - SCROLL UP

Representation: Table 2 - one numeric parameter, default value: 1

The displayed portion of a multiple-page buffer is moved by n lines such that
the displayed data appear to move up.

The effect of this control function on the active position is not defined by
this Standard.

#### 7.2.76. TBC - TABULATION CLEAR

Representation: Table 2 - selective parameter, default value: 0

TBC is a format effector which causes one or more tabulation stops to be
cleared, depending on the parameter value:

| value | meaning |
| ----- | ------- |
| 0     | clear the horizontal tabulation stop at the active position |
| 1     | clear the vertical tabulation stop at the active line |
| 2     | clear all horizontal tabulation stops at the active line |
| 3     | clear all horizontal tabulation stops |
| 4     | clear all vertical tabulation stops |

In the case of parameter values 0 or 2, when horizontal tabulation stops are
cleared, the number of lines affected depends on the setting of the TABULATION
STOP MODE.

#### 7.2.77. TSS - THIN SPACE SPECIFICATION

Representation: Table 3 - one numeric parameter; no default value

TSS is a format effector which establishes the width of thin spaces following
in the data stream, until the next occurrence of TSS (see Annex C).

`n` specifies the width in units as established by SELECT SIZE UNIT (SSU).

#### 7.2.78. VPA - VERTICAL POSITION ABSOLUTE

Representation: Table 2 - one numeric parameter; default value: 1

VPA is a format effector which causes the active position to be moved to the
corresponding horizontal position at vertical position n. The unit in which n
is expressed depends on the setting of the POSITIONING UNIT MODE.

#### 7.2.79. VPR - VERTICAL POSITION RELATIVE

Representation: Table 2 - one numeric parameter; default value: 1

VPR is a format effector which causes the active position to be moved to the
corresponding horizontal position at the n-th following vertical position. The
unit in which `n` is expressed depends on the setting of the POSITIONING UNIT
MODE.

#### 7.2.80. VTS - VERTICAL TABULATION SET
Representation: Table 1

VTS is a format effector which causes a vertical tabulation stop to be set at
the active line.


