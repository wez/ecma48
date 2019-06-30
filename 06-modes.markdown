## 6. MODES

### 6.1. The Concept of Modes

This Standard is intended to be applicable to a very large range of devices.
Within that broad range it is recognized that variations exist. Some of these
variations have been formalized in this Standard in the form of modes. They
deal with the way in which a device transmits, receives, processes, or images
data. Each mode is defined as having two states. The initial state of each mode
is defined by the implementation.

The modes may be established explicitly within the data stream or by agreement
between sender and recipient. In an implementation, some or all of the modes
may have a fixed state incapable of being altered.

### 6.2. Definition of Modes

The modes listed below are defined in this Standard. They are set and reset by
the control functions SET MODE (SM) and RESET MODE (RM). The parameter of SM or
RM specifies the mode which is affected. In each of the mode definitions below,
the first state is caused by RM, the second one by SM.

#### 6.2.1. CONTROL REPRESENTATION MODE

CONTROL:

All control functions are performed as defined, subject to the FORMAT EFFECTOR
ACTION MODE in so far as format effectors are concerned, see 6.3.2. In addition
to being performed some control functions may have a graphic representation.

GRAPHIC:

All control functions, except RESET MODE (RM), are treated as graphics.

#### 6.2.2. EDITING BOUNDARY MODE

DISPLAY:

The effects of the editing control functions are limited to the displayed
portion of a multiple-page buffer.

ALL:

The editing control functions may affect character positions outside the
displayed portion of a multiple-page buffer.

#### 6.2.3. ERASURE MODE

PROTECT:

Only unprotected data are affected by an erasure control function.

ALL:

Protected as well as unprotected data are affected by an erasure control
function.

#### 6.2.4. FORMAT EFFECTOR ACTION MODE

EXECUTE:

A format effector causes the specified action to be performed immediately.
Implementations may store format effectors in a buffer in addition to
performing them.

STORE:

A format effector is treated as a graphic.

This mode is significant only if the CONTROL REPRESENTATION MODE is set to
CONTROL.

#### 6.2.5. FORMAT EFFECTOR TRANSFER MODE

INSERT:

Format effectors are inserted in a transmitted data stream
or in any data transferred to any auxiliary input/output
device:

- the format effectors CARRIAGE RETURN (CR) and LINE FEED (LF), or NEXT LINE
  (NEL), are inserted in the data stream to separate successive lines;
- other format effectors may be inserted as appropriate, e.g. HORIZONTAL
  TABULATION (HT) to represent a string of erased character positions preceding
  a tabulation stop.

EXCLUDE:

No format effectors other than those received while the FORMAT EFFECTOR ACTION
MODE is set to STORE are included in a transmitted data stream or in data
transferred to any auxiliary input/output device.

#### 6.2.6. GUARDED AREA TRANSFER MODE

GUARD:
Only unguarded data in an eligible area are transmitted.

ALL:
Guarded as well as unguarded data in an eligible area are transmitted.

#### 6.2.7. HORIZONTAL EDITING MODE

FOLLOWING:

A character insertion causes a string of following data beginning with the
contents of the active position to be shifted forward; a character deletion
causes a string of data following the active position to be shifted backward.

PRECEDING:

A character insertion causes a string of preceding data ending with the
contents of the active position to be shifted backward; a character deletion
causes a string of data preceding the active position to be shifted forward.

#### 6.2.8. INSERTION REPLACEMENT MODE

REPLACE:

The receipt of a graphic character or a control function for which a graphic
representation is required causes the appropriate graphic symbol to replace
(or, depending on implementation, to be combined with) the graphic symbol
currently imaged at the active position.

INSERT:

The receipt of a graphic character or a control function for which a graphic
representation is required causes the appropriate graphic symbol to be inserted
at the active position.

The operation of inserting a character is performed as described in 5.5

#### 6.2.9. KEYBOARD ACTION MODE

ENABLED:
All manual input facilities are enabled to be used.

DISABLED:
All or part of the manual input facilities are disabled.

#### 6.2.10. MULTIPLE AREA TRANSFER MODE

SINGLE:
Only the selected area which contains the active position is eligible to be
transmitted.

MULTIPLE:
All selected areas are eligible to be transmitted.

This mode is significant only if the SELECTED AREA TRANSFER MODE is set to
SELECT.

#### 6.2.11. POSITIONING UNIT MODE

CHARACTER:
The unit for numeric parameters of the positioning format effectors is one
character position.

SIZE:
The unit for numeric parameters of the positioning format effectors is that
established by SELECT SIZE UNIT (SSU).

#### 6.2.12. SELECTED AREA TRANSFER MODE

SELECT:
Only selected areas are eligible to be transmitted.

ALL:
All data, irrespective of any explicitly defined selected areas, are eligible
to be transmitted.

#### 6.2.13. SEND/RECEIVE MODE

MONITOR:
Data which are locally entered are immediately imaged.

SIMULTANEOUS:

Local input facilities are logically disconnected from the output mechanism;
only data which are sent to the device are imaged.

#### 6.2.14. STATUS REPORT TRANSFER MODE

NORMAL:
No device status reports are generated automatically.

DIAGNOSTIC:
A device status report in the form of a device control string is automatically
included in every transmitted data stream.

#### 6.2.15. TABULATION STOP MODE

MULTIPLE:
A horizontal tabulation stop applies to the corresponding character positions
of all lines.

SINGLE:
A horizontal tabulation stop applies only to the line in which it is set.

**NOTE 5**: This mode is effective only when setting and clearing horizontal
tabulation stops.

#### 6.2.16. TRANSFER TERMINATION MODE

CURSOR:
Only data preceding the active position are eligible to be transmitted.

ALL:
Data preceding, following and at the active position are eligible to be
transmitted.

#### 6.2.17. VERTICAL EDITING MODE

FOLLOWING:

A line insertion causes the contents of the active line and of following lines
to be shifted down; a line deletion causes the contents of following lines to
be shifted up.

PRECEDING:

A line insertion causes the contents of the active line and of preceding lines
to be shifted up. A line deletion causes the contents of preceding lines to be
shifted down.

### 6.3. Interaction Between Modes

Three groups of modes are specified below. Each group contain
two or more modes which interact with one another.

#### 6.3.1. GUARDED AREA TRANSFER MODE, MULTIPLE AREA TRANSFER MODE, SELECTED AREA TRANSFER MODE and TRANSFER TERMINATION MODE

These modes have a combined effect on the format of a transmitted data stream
or of a data stream transferred to an auxiliary input/output device, as
described hereafter.

The term "active selected area'' is used to denote the selected area containing
the active position. The term "eligible" is used to denote any area which may
be considered for transmitting or transferring.

- If the TRANSFER TERMINATION MODE is set to CURSOR, the SELECTED AREA TRANSFER
  MODE to SELECT, and the MULTIPLE AREA TRANSFER MODE to SINGLE, then the
  contents of the active selected area, up to but excluding the active
  position, are eligible.

- If the TRANSFER TERMINATION MODE is set to CURSOR, the SELECTED AREA TRANSFER
  MODE to SELECT, and the MULTIPLE AREA TRANSFER MODE to MULTIPLE, then the
  contents of any selected areas, up to but excluding the active position, are
  eligible.

- If the TRANSFER TERMINATION MODE is set to CURSOR and the SELECTED AREA
  TRANSFER MODE to ALL, then the contents of the buffer up to but excluding the
  active position, are eligible.

- If the TRANSFER TERMINATION MODE is set to ALL, the SELECTED AREA TRANSFER
  MODE to SELECT, and the MULTIPLE AREA TRANSFER MODE to SINGLE, then the
  complete contents of the active selected area are eligible.

- If the TRANSFER TERMINATION MODE is set to ALL, the SELECTED AREA TRANSFER
  MODE to SELECT, and the MULTIPLE AREA TRANSFER MODE to MULTIPLE, then the
  contents of all selected areas are eligible.

- If the TRANSFER TERMINATION MODE and the SELECTED AREA TRANSFER MODE are both
  set to ALL, then the complete contents of the buffer are eligible.

- If the GUARDED AREA TRANSFER MODE is set to GUARD, all of the eligible area
  or areas are transmitted or transferred, except for guarded areas which are
  completely contained within the eligible area. Those guarded areas which are
  only partly contained in eligible areas may be transmitted or not, depending
  on implementation. Exercise of such an option permits the repeated
  transmission of a constant part of a field using the control functions START
  OF PROTECTED AREA (SPA) and END OF PROTECTED AREA (EPA) while preventing it
  from being changed by the operator.  More sophisticated devices may obtain
  the same effect with the control function DEFINE AREA QUALIFICATION (DAQ).

- If the GUARDED AREA TRANSFER MODE is set to ALL, guarded as well as unguarded
  data in an eligible area are transmitted.

If the active position is not within a selected area, the format of the data
stream in the first and fourth case above is not defined by this Standard.

#### 6.3.2. CONTROL REPRESENTATION MODE and FORMAT EFFECTOR ACTION MODE

- If the CONTROL REPRESENTATION MODE is set to GRAPHIC, it overrides the
  setting of the FORMAT EFFECTOR ACTION MODE.

- If the CONTROL REPRESENTATION MODE is set to CONTROL, the way format
  effectors are processed depends on the setting of the FORMAT EFFECTOR ACTION
  MODE.

#### 6.3.3. HORIZONTAL EDITING MODE and INSERTION REPLACEMENT MODE

- If the INSERTION REPLACEMENT MODE is set to REPLACE, the HORIZONTAL EDITING
  MODE influences the control functions DELETE CHARACTER and INSERT CHARACTER
  only.

- If the INSERTION REPLACEMENT MODE is set to INSERT then, in addition, the
  effect of the receipt of a graphic character or a control function for which
  a graphic representation is required depends on the setting of the HORIZONTAL
  EDITING MODE.


