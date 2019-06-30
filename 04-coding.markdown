## 4. CODED REPRESENTATIONS

### 4.1. General

The set of additional control functions in this Standard consists of more than
32 control functions which can be coded in a C1 set.

Each control function belongs to one of the following cate-
gories, depending on the method of representation:

* Control functions which are elements of the C1 set;
* Control functions represented by control sequences;
* Control functions represented by ESC Fs sequences.

This Standard also defines a method of representations of control functions by
means of control strings (see 4.6).

#### 4.1.1. Control functions which are elements of the C1 set

As in ECMA-35 such a control function is represented:

* in a 7-bit code by a 2-character escape sequence of the form ESC Fe, where Fe
  is a bit combination of column 4 or 53
* in an 8-bit code by a bit combination of column 08 or 09).

This method of representation permits coding of up to 32 control functions.
These bit combinations are defined in 4.2

#### 4.1.2. Control functions represented by control sequences

A control sequence consists of the coded representation of CONTROL SEQUENCE
INTRODUCER (CSI) followed by one or more bit combinations which identify the
control function and, if applicable, represent the parameters of the control
function. The control function CSI itself is an element of the C1 set.

The format of a control sequence is:

```
CSI P1 ... Pn I1 ... Im F
```

where:

* CSI is represented by ESC 5/11 in a 7-bit code and by 09/11 in an 8-bit code
  (see 4.2).
* `P1` ... `Pn` are bit combinations of column 3 representing the parameter
  values; these bit combinations shall be omitted if the control function has
  no parameter, and may be omitted if the default parameter value is to apply.
* `I1` ... `Im` are bit combinations of column 2 which, together with the final
  bit combination F, identify the control function; these bit combinations
  shall be omitted if the control function is identified by the final bit
  combination F alone;

NOTE 1: The number of intermediate bit combinations is not limited by this
Standard; in practice, at most one intermediate will be sufficient since over
one thousand control functions may be identified using not more than one
intermediate.

* `F` is a bit combination of column 4, 5, 6 or 7 (except 7/15) which
  terminates the control sequence and, together with the intermediate bit
  combinations I1 ... Im, if present, identifies the control function (see 9).

The occurrence of any bit combinations which do not conform to the above format
is an error condition for which recovery is not specified by this Standard.

The final bit combinations (either used alone or together with intermediates)
are classified in two categories:

* The control functions identified by final bit combinations of columns 4, 5
  and 6 are either standardized or reserved for future standardization;
* the control functions identified by final bit combinations of column 7
  (except 7/15) are not standardized and are available for private or
  experimental use.

There are two types of parameters; numeric and selective (see 4.4). A numeric
parameter represents a number; a selective parameter merely represents a
character string, the meaning of which depends on the control function.

The final bit combinations of columns 4, 5 and 6 and the intermediate bit
combinations are defined in 4.3.

#### 4.1.3. Control functions represented by ESC Fs sequences

As in ECMA-35 the coded representations of these control functions in 7-bit and
8-bit codes are 2-character escape sequences of the form ESC Fs, where Fs is a
bit combination from 6/0 to 7/14 (see 4.5). These control functions are not
part of the C1 set.

### 4.2. Elements of the C1 Set

The following 25 control functions are the elements of the C1 set:

| Abbreviation | Name |
| ------------ | ---- |
|APC | APPLICATION PROGRAM COMMAND |
|CCH | CANCEL CHARACTER |
|CSI | CONTROL SEQUENCE INTRODUCER |
|DES | DEVICE CONTROL STRING |
|EPA | END OF PROTECTED AREA |
|ESA | END OF SELECTED AREA |
|HTJ | HORIZONTAL TABULATION WITH JUSTIFICATION |
|HTS | HORIZONTAL TABULATION SET |
|IND | INDEX |
|MW  | MESSAGE WAITING |
|NEL | NEXT LINE |
|OSG | OPERATING SYSTEM COMMAND |
|PLD | PARTIAL LINE DOWN |
|PLU | PARTIAL LINE UP |
|PM  | PRIVACY MESSAGE |
|PU1 | PRIVATE USE 1 |
|PU2 | PRIVATE USE 2 |
|RI  | REVERSE INDEX |
|SPA | START OF PROTECTED AREA |
|SS2 | SINGLE SHIFT 2 |
|SS3 | SINGLE SHIFT 3 |
|SSA | START OF SELECTED AREA |
|ST  | STRING TERMINATOR |
|STS | SET TRANSMIT STATE |
|VTS | VERTICAL TABULATION SET |

Their coded representations are defined by Table 1.

The definitions of the control functions are specified in 7.2.

If a control function is represented by a 2-character escape sequence (in a
7-bit code), the table specifies the bit combination of the final character by
taking A=4 and B=5.

If a control function is represented by a single 8-bit combination the table
specifies this bit combination by taking A=08 and B=09.

The open positions in the table are reserved for future standardization. They
are not to be used for private or experimental codes.

| Row No | Column A | Column B |
| ------ | -------- | -------- |
|  0     |          | DCS      |
|  1     |          | PU1      |
|  2     |          | PU2      |
|  3     |          | STS      |
|  4     | IND      | CCH      |
|  5     | NEL      | MW       |
|  6     | SSA      | SPA      |
|  7     | ESA      | EPA      |
|  8     | HTS      |          |
|  9     | HTJ      |          |
| 10     | VTS      |          |
| 11     | PLD      | CSI      |
| 12     | PLU      | ST       |
| 13     | RI       | OSC      |
| 14     | SS2      | PM       |
| 15     | SS3      | APC      |

Table 1: ALLOCATION OF BIT COMBINATIONS TO THE CONTROL FUNCTIONS OF THE C1 SET.

The 3-character escape sequence designating this C1 set is ESC 2/2 F.

NOTE 2: The final character F of the designating 3-character escape sequence is
not known at this moment; it is subject to registration procedures in
accordance with International Standard ISO 2375.

### 4.3. Control Sequences

The 51 control functions listed below are represented by control sequences.

The definitions of the control functions are specified in 7.2. The final bit
combinations of the control sequences are defined by Tables 2 and 3.

#### 4.3.1. Control functions with numeric parameters

| Abbreviation | Name | Table |
| ------------ | ---- | ----- |
| CBT | CURSOR BACKWARD TABULATION | 2 |
| CHA | CURSOR HORIZONTAL ABSOLUTE | 2 |
| CHT | CURSOR HORIZONTAL TABULATION | 2 |
| CNL | CURSOR NEXT LINE | 2 |
| CPL | CURSOR PRECEDING LINE | 2 |
| CPR | CURSOR POSITION REPORT | 2 |
| CUB | CURSOR BACKWARD | 2 |
| CUD | CURSOR DOWN | 2 |
| CUF | CURSOR FORWARD | 2 |
| CUP | CURSOR POSITION | 2 |
| CUU | CURSOR UP | 2 | 
| CVT | CURSOR VERTICAL TABULATION | 2 |
| DA | DEVICE ATTRIBUTES | 2 |
| DCH | DELETE CHARACTER | 2 |
| DL | DELETE LINE | 2 |
| ECH | ERASE CHARACTER | 2 |
| FNT | FONT SELECTION | 3 |
| GSM | GRAPHIC SIZE MODIFICATION | 3 |
| GSS | GRAPHIC SIZE SELECTION | 3 |
| HPA | HORIZONTAL POSITION ABSOLUTE | 2 |
| HPR | HORIZONTAL POSITION RELATIVE | 2 |
| HVP | HORIZONTAL AND VERTICAL POSITION | 2 |
| ICH | INSERT CHARACTER | 2 |
| IL | INSERT LINE | 2 |
| NP | NEXT PAGE | 2 |
| PP | PRECEDING PAGE | 2 |
| REP | REPEAT | 2 |
| SD | SCROLL DOWN | 2 |
| SL | SCROLL LEFT | 3 |
| SPI | SPACING INCREMENT | 3 |
| SR | SCROLL RIGHT | 3 |
| SU | SCROLL UP | 2 |
| TSS | THIN SPACE SPECIFICATION | 3 |
| VPA | VERTICAL POSITION ABSOLUTE | 2 |
| VPR | VERTICAL POSITION RELATIVE | 2 |

#### 4.3.2. Control functions with selective parameters

| Abbreviation | Name | Table |
| ------------ | ---- | ----- |
| CTC | CURSOR TABULATION CONTROL | 2 |
| DAQ | DEFINE AREA QUALIFICATION | 2 |
| DSR | DEVICE STATUS REPORT | 2 |
| EA | ERASE IN AREA | 2 |
| ED | ERASE IN DISPLAY | 2 |
| EF | ERASE IN FIELD | 2 |
| EL | ERASE IN LINE | 2 |
| JFY | JUSTIFY | 3 |
| MC | MEDIA COPY | 2 |
| QUAD | QUAD | 3 |
| RM | RESET MODE | 2 |
| SEE | SELECT EDITING EXTENT | 2 |
| SGR | SELECT GRAPHIC RENDITION | 2 |
| SM | SET MODE | 2 |
| SSU | SELECT SIZE UNIT | 3 |
| TBC | TABULATION CLEAR | 2 |

Table 2 specifies the final bit combinations of the control sequences without
intermediates.

Table 3 specifies the final bit combinations of the control sequences which
contain bit combination 2/0 as the single intermediate.

The open positions in the tables, as well as all final bit combinations of
columns 4, 5 and 6 which are used with other intermediates than one 2/0 only,
are reserved for future standardization. All final bit combinations of column 7
except 7/15 (with or without intermediates) are available as final bit
combinations for private or experimental use.

| Row No. | Column #4 | Column #5 | Column #6 |
| ------- | --------- | ----------| --------- |
|  0      | ICH       | DCH       | HPA       |
|  1      | CUU       | SEE       | HPR       |
|  2      | CUD       | CPR       | REP       |
|  3      | CUF       | SU        | DA        |
|  4      | CUB       | SD        | VPA       |
|  5      | CNL       | NP        | VPR       |
|  6      | CPL       | PP        | HVP       |
|  7      | CHA       | CTC       | TBC       |
|  8      | CUP       | ECH       | SM        |
|  9      | CHT       | CVT       | MC        |
| 10      | ED        | CBT       |           |
| 11      | EL        |           |           |
| 12      | IL        |           | RM        |
| 13      | DL        |           | SGR       |
| 14      | EF        |           | DSR       |
| 15      | EA        |           | DAQ       |

Table 2: ALLOCATION OF FINAL BIT COMBINATIONS TO CONTROL SEQUENCES WITHOUT INTERMEDIATES.


| Row No. | Column #4 | Column #5 | Column #6 |
| ------- | --------- | ----------| --------- |
|  0      | SL        |           |           |
|  1      | SR        |           |           |
|  2      | GSM       |           |           |
|  3      | GSS       |           |           |
|  4      | FNT       |           |           |
|  5      | TSS       |           |           |
|  6      | JFY       |           |           |
|  7      | SPI       |           |           |
|  8      | QUAD      |           |           |
|  9      | SSU       |           |           |
| 10      |           |           |           |
| 11      |           |           |           |
| 12      |           |           |           |
| 13      |           |           |           |
| 14      |           |           |           |
| 15      |           |           |           |

Table 3: ALLOCATION OF FINAL BIT COMBINATIONS TO CONTROL SEQUENCES WITH 2/0 AS A SINGLE INTERMEDIATE.

### 4.4. Parameter Representations

A control sequence may contain a string of bit combinations
`P1 ... Pn` representing one or more parameters to complete the
specification of the control function.

The string of bit combinations `P1 ... Pn` contained in a control sequence is
called the parameter string. It consists of bit combinations of column 3 and is
interpreted as follows:

* If the first bit combination of the parameter string is in the range 3/0 to
  3/11, the parameter string is interpreted according to the format described
  below.
* If the first bit combination of the parameter string is in the range 3/12 to
  3/15, the parameter string is available for private or experimental use. Its
  format and meaning are not specified in this Standard.

#### 4.4.1. Parameter string format

* A parameter string consists of one or more parameter substrings, each of
  which represents a parameter value.
* Each parameter sub-string consists of one or more bit combinations from 3/0
  to 3/9, representing the decimal digits ZERO to NINE.
* Parameter sub-strings are separated by one bit combination 3/11.
* Bit combination 3/10 is reserved for future standardization as an additional
  parameter separator.
* Bit combinations 3/12 to 3/15 shall not be used.
* In each parameter sub-string, leading bit combinations 3/0 are not
  significant and may be omitted.
* If the parameter string starts with the bit combination 3/11, an empty
  parameter sub-string is assumed preceding `|` the separator; if the parameter
  string terminates with the bit combination 3/11, an empty parameter
  sub-string is assumed following the separator; if the parameter string
  contains successive bit combinations 3/11, empty parameter sub-strings are
  assumed between the separators.
* An empty parameter sub-string or a parameter sub-string which consists of bit
  combinations 3/0 only represents a default value which depends on the control
  function.

#### 4.4.2. Types of parameters

There are two types of parameters: numeric parameters and selective parameters.

##### 4.4.2.1. Numeric parameters

In a control sequence representing a control function with numeric parameters,
each parameter sub-string corresponds to one parameter.

The number of parameters is fixed and depends on the control function. If the
control function has more than one numeric parameter, and some (but not all)
parameter sub-strings are omitted, the separators (bit combination 3/11) must
still be present. Only if all parameter sub-strings are omitted, are the
separators not required.

Each numeric parameter sub-string which contains at least one bit combination
from 3/1 to 3/9 represents a number in decimal notation.

##### 4.4.2.2. Selective parameters

In a control sequence representing a control function with a selective
parameter, each parameter sub-string represents one value of the selective
parameter. These values, whilst expressed by digits, are not quantitative. Each
corresponds to one of the actions the control function can perform. Neither the
maximum number of values nor the order in which the corresponding actions are
performed are prescribed by this Standard. The effect of a sequence of values
corresponding to conflicting actions depends on implementation.

A particular parameter value may have the same meaning as a combination of two
or more separate values.

### 4.5. ESC Fs Sequences

The following four control functions are represented by
ESC Fs sequences:

| Abbreviation | Name |
| ------------ | ---- |
| DMI | DISABLE MANUAL INPUT |
| EMI | ENABLE MANUAL INPUT |
| INT | INTERRUPT |
| RIS | RESET TO INITIAL STATE |

The definitions of these control functions are specified in 7.2.

The coded representations are defined by Table 4 which specifies the final bit
combinations of the 2-character escape sequences representing these control
functions.

The open positions in the table are reserved for standardion of other control
functions.

| Row # | Column #6 | Column #7 |
| ----- | --------- | --------- |
|  0    | DMI       |           |
|  1    | INT       |           |
|  2    | EMI       |           |
|  3    | RIS       |           |
|  4    |           |           |
|  5    |           |           |
|  6    |           |           |
|  7    |           |           |
|  8    |           |           |
|  9    |           |           |
| 10    |           |           |
| 11    |           |           |
| 12    |           |           |
| 13    |           |           |
| 14    |           |           |
| 15    |           |           |

Table 4: ALLOCATION OF FINAL BIT COMBINATIONS TO ESC Fs SEQUENCES.

### 4.6. Control Strings

A control string is a delimited string of characters which may occur in the
data stream as a logical entity for control purposes. A control string consists
of an opening delimiter, followed by a string of graphic characters and SPACEs
(bit combinations 2/0 to 7/14 inclusive) and terminated by STRING TERMINATOR
(ST). The occurrence of other bit combinations within a control string is an
error condition for which recovery is not specified by this Standard (see 9).

The opening delimiter indicates the class of the component of the system which
is the sender or recipient of the control string. The interpretation of the
contents of the control string is not specified by this Standard, but instead
requires prior agreement between the sender and the recipient of the data.

The classes of system components which can be specified by the appropriate
opening delimiter are the device, the operating system control program, the
privacy discipline, and the application program. The corresponding opening
delimiters are:

* DEVICE CONTROL STRING (DCS)
* OPERATING SYSTEM COMMAND (OSC)
* PRIVACY MESSAGE (PM)
* APPLICATION PROGRAM COMMAND (APC)

Examples of applications of device control strings are:

* program loading
* configuration control
* mode control
* diagnostics

An example of the use of application program command string is the interjection
of application program commands in a data stream or file being processed by the
application program as data.


