## 8. RELATIONS BETWEEN MODES AND CONTROL FUNCTIONS

The relations between modes and control functions are summarized in Table 5.

The modes FORMAT EFFECTOR TRANSFER MODE, GUARDED AREA TRANSFER MODE, MULTIPLE
AREA TRANSFER MODE, SELECTED AREA TRANSFER MODE, STATUS REPORT TRANSFER MODE
and TRANSFER TERMINATION MODE do not affect the interpretation of control
functions. They have an effect on the format of the transmitted data stream and
on the format of the data transferred to an auxiliary input/output device:

In the case of the modes INSERTION REPLACEMENT MODE, KEYBOARD ACTION MODE and
SEND/RECEIVE MODE there is no interaction with specific control functions.
These modes have a uniform effect on all characters received.

The CONTROL REPRESENTATION MODE affects all control functions except RESET MODE
(RM).

Those modes which uniformly apply to format effectors defined in this Standard
also apply to the format effectors of the C0 set.

|     | EDITING BOUNDARY MODE | ERASURE MODE | FORMAT EFFECTOR ACTION MODE | HORIZONTAL EDITING MODE | POSITIONING UNIT MODE | TABULATION STOP MODE | VERTICAL EDITING MODE |
|---- | ----|----|-----|----|----|----|----|
| CTC |     |    |     |    |    | X  |    |
| DCH | X   |    |     | X  |    |    |    |
| DL  | X   |    |     |    |    | X  | X  |
| EA  | X   | X  |     |    |    |    |    |
| ECH | X   | X  |     |    |    |    |    |
| ED  | X   | X  |     |    |    |    |    |
| EF  | X   | X  |     |    |    |    |    |
| EL  | X   | X  |     |    |    |    |    |
| FNT |     |    | X   |    |    |    |    |
| GSM |     |    | X   |    |    |    |    |
| GSS |     |    | X   |    |    |    |    |
| HPA |     |    | X   |    | X  |    |    |
| HPR |     |    | X   |    | X  |    |    |
| HTJ |     |    | X   |    |    |    |    |
| HTS |     |    | X   |    |    | X  |    |
| HVP |     |    | X   |    | X  |    |    |
| ICH | X   |    |     | X  |    |    |    |
| IL  | X   |    |     |    |    | X  | X  |
| IND |     |    | X   |    |    |    |    |
| JFY |     |    | X   |    |    |    |    |
| NEL |     |    | X   |    |    |    |    |
| PLD |     |    | X   |    |    |    |    |
| PLU |     |    | X   |    |    |    |    |
| QUAD|     |    | X   |    |    |    |    |
| RI  |     |    | X   |    |    |    |    |
| SEE | X   |    |     |    |    |    |    |
| SGR |     |    | X   |    |    |    |    |
| SPI |     |    | X   |    |    |    |    |
| SSU |     |    | X   |    | X  |    |    |
| TBC |     |    | X   |    |    | X  |    |
| TSS |     |    | X   |    |    |    |    |
| VPA |     |    | X   |    | X  |    |    |
| VPR |     |    | X   |    | X  |    |    |
| VTS |     |    | X   |    |    |    |    |

Table 5: RELATIONS BETWEEN MODES AND CONTROL FUNCTIONS


