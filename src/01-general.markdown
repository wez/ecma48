## 1. GENERAL

### 1.1. Scope and Field of Application

This Standard defines additional control functions for use in an extended 7-bit
or 8-bit code structured in accordance with Standard ECMA-35. It comprises a C1
set, control functions derived therefrom and four single control functions.

These control functions are intended to be used, in combination with the CO set
defined in Standard ECMA-6, for data interchange with character-imaging
devices.

A character-imaging device is a device which is capable of re ceiving a data
stream that consists of coded control functions and graphics, and of producing
character image output, i.e.  output that can be read by a human being. The
character image output is, in general, produced in the form of one or more
rectangular arrays of characters which are called pages.

If the device is an input/output device rather than merely an output device, it
is also capable of transmitting a data stream that consists of coded control
functions and graphics; the transmitted data stream is, in general, composed of
a combination of data which have been sent to the device and data which have
been locally entered into the device, e.g. by an associated keyboard.

The control functions are defined by their effects on a character-imaging
input/output device. It is, therefore, necessary to make certain assumptions
about the device architecture.  These assumptions are as little restrictive as
possible; they are specified in 5, DEVICE CONCEPTS.

The intention of this Standard is to facilitate data interchange, not to
standardize equipment. The specifications of the architectural device concepts
are included only to delimit the field of application of the Standard. The
definitions of the control functions may not be applicable to devices which do
not conform to the specified concepts.

The structure of this Standard is open-ended, so that more control functions
can be included in future versions.

### 1.2. Conformance

Full conformance to a standard means that all its requirements are met. For
such conformance to be unique the standard must contain no options. This is
typically the case for hardware standards, for instance Standard ECMA-10 for
data interchange on punched tapes.

This Standard ECMA-48 is of a different nature and as a result, it is only
practicable to envisage limited conformance to it, as defined hereunder.

This Standard addresses a whole class of devices which can vary greatly from
each other depending on the application for which a device has been
specifically designed. Obviously, a product which implements all facilities
described in this standard - thus being in "full conformance" with it - whilst
theoretically possible, would be technically and economically unthinkable.

Under limited conformance the following is required:

1. The general architecture of the device shall be as described in Section 5S.
This section includes many features not all of which need be implemented. The
selection made in practice will depend on the applications envisaged.
2. The device may implement other modes than those described in the Standard,
but these shall not be incompatible with those described in the Standard.
3. The device shall implement control functions described in Section 7 with
the same definition and the same coding. It shall not implement other controls
which are incompatible with those definitions.
4. If in addition facilities not provided by the Standard are required they
shall be implemented only by means of private use codes, they may not be coded
elsewhere. Facilities provided by the Standard may not be implemented by means
of such private use codes.
5. Where a default value of a parameter is specified in the Standard for a
given control function a conforming implementation of this control function has
to be capable of meeting the default situation.

It is recognized that limited conformance does not ensure necessarily that two
devices can always communicate with each other without problems. Any product
claiming conformance is required to list the facilities of the Standard which
it provides. Until such time that a list of parameter values for the control
function DEVICE ATTRIBUTES (7.2.17) is set up internationally, sender and
recipient of the data must check whether or not their own device can cope with
the other's implementation.

In spite of these limitations which are inherent to its nature and to the aim
of fostering data interchange without standardizing equipment, it is believed
that this Standard gives strong guidance to device designers, avoiding the
development of incompatible hardware and helping to foster standardization.

