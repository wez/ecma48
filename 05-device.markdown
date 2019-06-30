## 5. DEVICE CONCEPTS

The definitions of the control functions in this Standard are based on general
assumptions about the architecture of character- imaging devices. Examples of
devices conforming to these concepts are: an alpha-numeric display device, a
printer or a microfilm output device.

### 5.1. The Received Data Stream

The received data stream is considered to be a continuous stream. It may be
structured in messages, records and/or blocks, but this does not affect the
operation of the device at the abstract level of description in this Standard;
the logical or physical units of data are regarded as being concatenated to
form a continuous stream.

The device may contain a buffer in which the received data are temporarily
stored before they are used to produce the character image output, or in which
the received data are permanently stored and continuously used to produce the
character image output.

### 5.2. The Character Image Output

The character image output may consist of one or more pages of a pre-determined
size.

A page is composed of a pre-determined number of lines, each being composed of
a number of character positions.

The device may have the capability of varying the number of lines per page, the
number of character positions per line, and the character spacing during the
operation of the device.

If the character image output is not structured in pages, it is regarded as
consisting of a single page of an unlimited number of lines.

The lines constituting a page as well as the character positions constituting a
line are identified by the natural numbers 1, 2, 3,

Each character position either is erased or images SPACE or a graphic symbol. A
graphic symbol represents a graphic character or one of the control functions
for which a graphic representation is required.

The initial state of all character positions is "erased".

Depending on implementation, there may or may not be a distinction between an
erased character position and a character position imaging SPACE.

Depending on the characteristics of the device, a character position may be
capable of imaging a combination of two or more graphic symbols. This would
permit the use of BACKSPACE to generate accented letters or other composite
graphic symbols.

The width of a character position may be fixed or may depend on the character
being imaged.

In this Standard, the character image output is regarded as being produced in
the form of a continuous stream, but it may in actual fact be made available
character-by-character, line-by-line, or page-by-page.

The character positions are numbered relative to the character image (page)
output, not to the buffer (if any).

The character style and font design of the graphic symbols are not defined by
this Standard, but their shapes and relative positioning to accomodate overlay
of two or more symbols may be influenced by control functions in the received
data stream.

### 5.3. The Active Position

At any time, there is a unique character position which is called the "active
position".

The active position is the character position which is to image the graphic
symbol representing the next graphic character of the received data stream or
the next control function for which a graphic representation is required. The
active position is also the reference position against which certain format
effectors or editor functions are performed (see 5.4).

The line containing the active position is called the "active line".

#### Implicit movement

If the active position is not the last character position of a line, it is
moved to the following character position of the active line.

An implicit movement is performed when SPACE or a graphic character is received
or a control function, for which a graphic representation is required, is
executed.

#### Explicit movement

The active position is moved to a specified character position.

An explicit movement is performed when a control function is executed which
causes the active position to be moved to a specified position.

**NOTE 3**: In the case of an interactive display device it is common practice
to mark the active position by means of a special indicator which is called the
"cursor".

**NOTE 4**: In the following situations, the effect of an attempt to move the
active position is not defined by this Standard:

* an attempt to perform an implicit movement when the active position is the
  last character position of a line,
* an attempt to perform an explicit movement to a non-existing character
  position, e.g. beyond the last character position of a line, or beyond the
  last line of a page.

Depending on implementation, an attempt to perform such an active
position movement may:

- cause a wrap around movement,
- cause the active position to be blocked (a condition in which no graphic
  symbol can be entered until a valid explicit active position movement is
  performed),
- cause the active position to remain where it is but permit graphic symbols to
  be entered thereby replacing or overstriking the previously entered
  character,
- cause the cursor to disappear from the operator's view,
- cause the cursor to move to the opposite end of the display but one row or
  column offset,
- cause scrolling to occur,
- cause other implementation-dependent action.

### 5.4. Format Effectors and Editor Functions

Two classes of control functions have an action on the layout or positioning of
information in character-imaging devices.  They are format effectors and editor
functions. Format effectors are intended to be used on all classes of imaging
de- vices while editor functions are supplementary control functions required
only in circumstances for a certain class of devices where an action is to be
performed on previously entered data. The principal difference between editor
functions and format effectors is that the latter are sensitive to the FORMAT
EFFECTOR ACTION MODE, whereas the former are not (see Annex A).

#### 5.4.1. Format effectors

Format effectors belong to the data stream and shall be treated as data which
happen to have a format representation rather than a graphic representation.
Format effectors describe how the originator of the data stream wishes the
information to be formatted.

Therefore, if format effectors are not stored by the receiving device they
shall be regenerated by the device for subsequent transmission to additional
recipients in order to preserve data integrity.

Format effectors are processed as follows depending on the setting of the
FORMAT EFFECTOR ACTION MODE (6.2.4) of the device.

If the FORMAT EFFECTOR ACTION MODE is set to EXECUTE, the action specified by
the format effector (usually an active position movement) is immediately
performed. Depending on implementation a format effector may be stored in
addition to being performed.

If the FORMAT EFFECTOR ACTION MODE is set to STORE, the format effector is
treated as a graphic and stored in the buffer. In this case, the specified
action is intended to be performed by an auxiliary input/output device when the
associated data are transferred.

#### 5.4.2. Composite characters

Composite characters not already available shall be obtained using the format
effector BACKSPACE rather than editor functions (see Annex A.3). For example
small letter e with accent may be obtained as follows:

**Wez's note: this section is intended to show the use of BS to implement what
we refer to today as combining character display by printing accent characters
and then backspacing and printing latin characters, but it didn't translate
though the OCR.  This section needs fixing up**

| Data stream | Displayed |
| ----------- | --------- |
| ~ BS e      |           |
| “~ BS e     | é         |
| “ BS ~ BS e | é         |

#### 5.4.3. Editor functions

The main purpose of editor functions is to edit, alter, or transpose the visual
arrangement of data.

In most cases, editor functions will be perfomed immediately by the first
receiver and then removed from the data stream.

Typical use of editor functions are:

- Coding of local functions for example encoding keyboard functions when the
  keyboard is logically uncoupled from the output imaging mechanism of a
  device.
- Transposing intended representation to an alternate representation in those
  cases where the receiving device is unable to display the intended image.

### 5.5. Editing Operations

This section is applicable primarily to buffered input/output devices. Editing
operations (erasure, deletion, and insertion) are performed either in execution
of control functions in the received data stream, or under control of a
keyboard or another manual entry device.

#### 5.5.1. Erasure

The state of one or more character positions is changed to "erased". Other
character positions remain unaffected.

#### 5.5.2. Deletion

The data contained in one or more character positions are removed by shifting
the contents of an adjacent string of character positions so that the data to
be removed are overwritten. As a result a string of character positions, equal
in length to the deleted string, is erased at the beginning or the end of the
shifted part.

#### 5.5.3. Insertion

One or more erased positions are inserted by shifting the contents of a string
of character positions adjacent to the position where the insertion is to be
made. As a result a string of data, equal in length to the inserted string, is
removed at the beginning or the end of the shifted part.

#### 5.5.4. Editing modes and insertion/deletion

In case of a deletion or insertion, the string which is shifted either precedes
or follows the position where the deletion or insertion is made, depending on
the setting of the HORIZONTAL EDITING MODE (6.2.7) and of the VERTICAL EDITING
MODE (6.2.17).

### 5.6. Selected and Qualified Areas

This section is applicable primarily to buffered input/output devices. It may
be also applicable to unbuffered input/output devices when the SEND/RECEIVE
MODE (6.2.13) is set to SIMULTANEOUS.

#### 5.6.1. Selected areas

A selected area is a string of character positions, the
contents of which may be eligible (see 6.3) to be transmitted in the form of a
data stream or to be transferred to an auxiliary input/output device (see 5.7).

The beginning of a selected area is established by START OF SELECTED AREA
(SSA). The character position which is the active position after receipt of SSA
is the first character position of the selected area.

The end of a selected area is established by END OF SELECTED AREA (ESA). The
character position which is the active position before receipt of ESA is the
last character position of the selected area.

#### 5.6.2. Qualified areas

A qualified area is a string of character positions with which certain
characteristics are associated, such as one or a combination of the following:

- the contents of the character positions are protected against manual
  alteration;
- the set of characters which are permitted to be entered is restricted (e.g.
  to numeric or alphabetic characters only);
- the character positions are protected against erasure;
- a tabulation stop is associated with the first character position;
- the character positions are to be excluded, i.e. guarded (see 5.6.2.2) from
  transmission of a data stream, or from transfer to an auxiliary input/output
  device (see 5.7).

The beginning of a qualified area is established by DEFINE AREA QUALIFICATION
(DAQ). The character position which is the active position after receipt of DAQ
is the first character position of the qualified area. The type of area
qualification is specified by the parameter of DAQ. The end of a qualified area
is established by the beginning of the following qualified area.

##### 5.6.2.1. Protected area

A protected area is a special case of a qualified area.  It is a string of
character positions, the contents of which are protected against manual
alteration. A protected area may, in general, be either guarded or unguarded.

##### 5.6.2.2. Guarded area

A guarded area is a special case of a qualified area. It is a protected area
which is to be excluded from transmission of a data stream and from transfer to
an auxiliary input/output device.

An alternative way to establish the beginning and end of a guarded protected
area is by means of START OF PROTECTED AREA (SPA) and END OF PROTECTED AREA
(EPA).

### 5.7. Auxiliary Input/Output Devices

This section is applicable primarily to buffered input/output devices. It may
be also applicable to unbuffered input/output devices when the SEND/RECEIVE
MODE is set to SIMULTANEOUS.

Data transfer from or to an auxiliary input/output device is initiated either
by the operation of an appropriate button on a keyboard or by the control
function MEDIA COPY (MC) appearing in the received data stream.

If there are more than one auxiliary input/output devices, the relevant device
is specified by the parameter of MC.

An input data stream which is received from an auxiliary device is processed in
the same way as any other received data stream. The method of terminating the
input from the auxiliary device depends on implementation.


