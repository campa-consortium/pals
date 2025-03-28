(c:ele.types)=
# Element Types

Note: `name`, `Length`, and `s_position` parameters stand alone and not part of any parameter group.

%---------------------------------------------------------------------------------------------------
(s:ackicker)=
## ACKicker Element

Time varying kicker element

Under Construction...

Element parameter groups associated with this element type are:
- [**ACKickerP**](#s:ackicker.params): AC kicker parameters.
- [**ApertureP**](#s:aperture.params): Aperture parameters.
- [**BodyShiftP**](#s:bodyshift.params): Orientation of element with respect to its nominal position.
- [**FloorP**](#s:floor.params): Floor position and orientation.
- [**MetaP**](#s:meta.params): Meta parameters.
- [**ReferenceP**](#s:ref.params): Reference parameters.
- [**ReferenceChangeP**](#s:refchange.params): Reference energy change and/or reference time correction.
- [**TrackingP**](#s:tracking.params): Tracking parameters.

%---------------------------------------------------------------------------------------------------
(s:beambeam)=
## BeamBeam Element

Element for simulating colliding beams.

Under Construction...

Element parameter groups associated with this element type are:
- [**ApertureP**](#s:aperture.params): Aperture parameters.
- [**BeamBeamP**](#s:beambeam.params): Beam-beam interaction parameters.
- [**BodyShiftP**](#s:bodyshift.params): Orientation of element with respect to its nominal position.
- [**FloorP**](#s:floor.params): Floor position and orientation.
- [**MetaP**](#s:meta.params): Meta parameters.
- [**ReferenceP**](#s:ref.params): Reference parameters.
- [**ReferenceChangeP**](#s:refchange.params): Reference energy change and/or reference time correction.
- [**TrackingP**](#s:tracking.params): Tracking parameters.

The length of this element is considered to be zero so if `Length` is specified, it must be zero.

%---------------------------------------------------------------------------------------------------
(s:beginningele)=
## BeginningEle Element

Initial element at start of a branch.

Under Construction...

Element parameter groups associated with this element type are:
- [**ApertureP**](#s:aperture.params): Aperture parameters.
- [**BodyShiftP**](#s:bodyshift.params): Orientation of element with respect to its nominal position.
- [**FloorP**](#s:floor.params): Floor position and orientation.
- [**MetaP**](#s:meta.params): Meta parameters.
- [**ReferenceP**](#s:ref.params): Reference parameters.
- [**TrackingP**](#s:tracking.params): Tracking parameters.

The length of this element is considered to be zero so if `Length` is specified, it must be zero.

%---------------------------------------------------------------------------------------------------
(s:bend)=
##  Bend Element

Dipole bend.

Under Construction...

Element parameter groups associated with this element type are:
- [**ApertureP**](#s:aperture.params): Aperture parameters.
- [**BodyShiftP**](#s:bodyshift.params): Orientation of element with respect to its nominal position.
- [**ElectricMultipoleP**](#s:elec.mult.params): Electric multipoles
- [**FloorP**](#s:floor.params): Floor position and orientation.
- [**MagneticMultipoleP**](#s:mag.mult.params): Magnetic multipoles.
- [**MetaP**](#s:meta.params): Meta parameters.
- [**ReferenceP**](#s:ref.params): Reference parameters.
- [**ReferenceChangeP**](#s:refchange.params): Reference energy change and/or reference time correction.
- [**TrackingP**](#s:tracking.params): Tracking parameters.

%---------------------------------------------------------------------------------------------------
(s:converter)=
## Converter Element

Target to produce new species. EG: Positron converter.

Under Construction...

Element parameter groups associated with this element type are:
- [**ApertureP**](#s:aperture.params): Aperture parameters.
- [**BodyShiftP**](#s:bodyshift.params): Orientation of element with respect to its nominal position.
- [**ElectricMultipoleP**](#s:elec.mult.params): Electric multipoles
- [**FloorP**](#s:floor.params): Floor position and orientation.
- [**MagneticMultipoleP**](#s:mag.mult.params): Magnetic multipoles.
- [**MetaP**](#s:meta.params): Meta parameters.
- [**ReferenceP**](#s:ref.params): Reference parameters.
- [**ReferenceChangeP**](#s:refchange.params): Reference energy change and/or reference time correction.
- [**TrackingP**](#s:tracking.params): Tracking parameters.

The length of this element is considered to be zero so if `Length` is specified, it must be zero.

%---------------------------------------------------------------------------------------------------
(s:crabcavity)=
## CrabCavity Element

RF crab cavity

Under Construction...

Element parameter groups associated with this element type are:
- [**ApertureP**](#s:aperture.params): Aperture parameters.
- [**BodyShiftP**](#s:bodyshift.params): Orientation of element with respect to its nominal position.
- [**ElectricMultipoleP**](#s:elec.mult.params): Electric multipoles
- [**FloorP**](#s:floor.params): Floor position and orientation.
- [**MagneticMultipoleP**](#s:mag.mult.params): Magnetic multipoles.
- [**MetaP**](#s:meta.params): Meta parameters.
- [**ReferenceP**](#s:ref.params): Reference parameters.
- [**ReferenceChangeP**](#s:refchange.params): Reference energy change and/or reference time correction.
- [**TrackingP**](#s:tracking.params): Tracking parameters.

%---------------------------------------------------------------------------------------------------
(s:drift)=
## Drift Element

Field free region.

Under Construction...

Element parameter groups associated with this element type are:
- [**ApertureP**](#s:aperture.params): Aperture parameters.
- [**BodyShiftP**](#s:bodyshift.params): Orientation of element with respect to its nominal position.
- [**FloorP**](#s:floor.params): Floor position and orientation.
- [**MetaP**](#s:meta.params): Meta parameters.
- [**ReferenceP**](#s:ref.params): Reference parameters.
- [**ReferenceChangeP**](#s:refchange.params): Reference energy change and/or reference time correction.
- [**TrackingP**](#s:tracking.params): Tracking parameters.

%---------------------------------------------------------------------------------------------------
(s:egun)=
## EGun Element

Electron gun.

Under Construction...

Element parameter groups associated with this element type are:
- [**ApertureP**](#s:aperture.params): Aperture parameters.
- [**BodyShiftP**](#s:bodyshift.params): Orientation of element with respect to its nominal position.
- [**ElectricMultipoleP**](#s:elec.mult.params): Electric multipoles
- [**FloorP**](#s:floor.params): Floor position and orientation.
- [**MagneticMultipoleP**](#s:mag.mult.params): Magnetic multipoles.
- [**MetaP**](#s:meta.params): Meta parameters.
- [**ReferenceP**](#s:ref.params): Reference parameters.
- [**ReferenceChangeP**](#s:refchange.params): Reference energy change and/or reference time correction.
- [**TrackingP**](#s:tracking.params): Tracking parameters.

%---------------------------------------------------------------------------------------------------
(s:feedback)=
## Feedback Circuit 

Element used to simulate a feedback circuit.

Under Construction...

Note: This element does not have a `Length` nor an `s_position`.

%---------------------------------------------------------------------------------------------------
(s:fiducial)=
## Fiducial Element

Global coordinate system fiducial point.

Under Construction...

The length of this element is considered to be zero so if `Length` is specified, it must be zero.

%---------------------------------------------------------------------------------------------------
(s:floorshift)=
## FloorShift Element

Global coordinates shift.

Under Construction...

Element parameter groups associated with this element type are:
- [**MetaP**](#s:meta.params): Meta parameters.
- [**ReferenceP**](#s:ref.params): Reference parameters.

%---------------------------------------------------------------------------------------------------
(s:foil)=
## Foil Element

Material that can strip electrons from a particle.
Will also cause energy loss and diffusion.

Under Construction...

Element parameter groups associated with this element type are:
- [**ApertureP**](#s:aperture.params): Aperture parameters.
- [**BodyShiftP**](#s:bodyshift.params): Orientation of element with respect to its nominal position.
- [**FloorP**](#s:floor.params): Floor position and orientation.
- [**MetaP**](#s:meta.params): Meta parameters.
- [**ReferenceP**](#s:ref.params): Reference parameters.
- [**ReferenceChangeP**](#s:refchange.params): Reference energy change and/or reference time correction.
- [**TrackingP**](#s:tracking.params): Tracking parameters.

The length of this element is considered to be zero so if `Length` is specified, it must be zero.

%---------------------------------------------------------------------------------------------------
(s:fork)=
## Fork Element

Element used to connect lattice branches together.

Under Construction...

Element parameter groups associated with this element type are:
- [**ApertureP**](#s:aperture.params): Aperture parameters.
- [**BodyShiftP**](#s:bodyshift.params): Orientation of element with respect to its nominal position.
- [**FloorP**](#s:floor.params): Floor position and orientation.
- [**MetaP**](#s:meta.params): Meta parameters.
- [**ReferenceP**](#s:ref.params): Reference parameters.
- [**ReferenceChangeP**](#s:refchange.params): Reference energy change and/or reference time correction.
- [**TrackingP**](#s:tracking.params): Tracking parameters.

The length of this element is considered to be zero so if `Length` is specified, it must be zero.

%---------------------------------------------------------------------------------------------------
(s:girder)=
## Girder Element

Element to support in space a group of other elements.

Under Construction...

Note: This element does not have a `Length` nor an `s_position`.

%---------------------------------------------------------------------------------------------------
(s:instrument)=
## Instrument Element

Measurement element.

Under Construction...

Element parameter groups associated with this element type are:
- [**ApertureP**](#s:aperture.params): Aperture parameters.
- [**BodyShiftP**](#s:bodyshift.params): Orientation of element with respect to its nominal position.
- [**ElectricMultipoleP**](#s:elec.mult.params): Electric multipoles
- [**FloorP**](#s:floor.params): Floor position and orientation.
- [**MagneticMultipoleP**](#s:mag.mult.params): Magnetic multipoles.
- [**MetaP**](#s:meta.params): Meta parameters.
- [**ReferenceP**](#s:ref.params): Reference parameters.
- [**ReferenceChangeP**](#s:refchange.params): Reference energy change and/or reference time correction.
- [**TrackingP**](#s:tracking.params): Tracking parameters.

%---------------------------------------------------------------------------------------------------
(s:kicker)=
## Kicker Element

Particle kicker element.

Under Construction...

Element parameter groups associated with this element type are:
- [**ApertureP**](#s:aperture.params): Aperture parameters.
- [**BodyShiftP**](#s:bodyshift.params): Orientation of element with respect to its nominal position.
- [**ElectricMultipoleP**](#s:elec.mult.params): Electric multipoles
- [**FloorP**](#s:floor.params): Floor position and orientation.
- [**MagneticMultipoleP**](#s:mag.mult.params): Magnetic multipoles.
- [**MetaP**](#s:meta.params): Meta parameters.
- [**ReferenceP**](#s:ref.params): Reference parameters.
- [**ReferenceChangeP**](#s:refchange.params): Reference energy change and/or reference time correction.
- [**TrackingP**](#s:tracking.params): Tracking parameters.

%---------------------------------------------------------------------------------------------------
(s:marker)=
## Marker Element

Zero length element to mark a particular position.

Under Construction...

Element parameter groups associated with this element type are:
- [**ApertureP**](#s:aperture.params): Aperture parameters.
- [**BodyShiftP**](#s:bodyshift.params): Orientation of element with respect to its nominal position.
- [**FloorP**](#s:floor.params): Floor position and orientation.
- [**MetaP**](#s:meta.params): Meta parameters.
- [**ReferenceP**](#s:ref.params): Reference parameters.
- [**ReferenceChangeP**](#s:refchange.params): Reference energy change and/or reference time correction.
- [**TrackingP**](#s:tracking.params): Tracking parameters.

The length of this element is considered to be zero so if `Length` is specified, it must be zero.

%---------------------------------------------------------------------------------------------------
(s:mask)=
## Mask Element

Collimation element.

Under Construction...

Element parameter groups associated with this element type are:
- [**ApertureP**](#s:aperture.params): Aperture parameters.
- [**BodyShiftP**](#s:bodyshift.params): Orientation of element with respect to its nominal position.
- [**ElectricMultipoleP**](#s:elec.mult.params): Electric multipoles
- [**FloorP**](#s:floor.params): Floor position and orientation.
- [**MagneticMultipoleP**](#s:mag.mult.params): Magnetic multipoles.
- [**MetaP**](#s:meta.params): Meta parameters.
- [**ReferenceP**](#s:ref.params): Reference parameters.
- [**ReferenceChangeP**](#s:refchange.params): Reference energy change and/or reference time correction.
- [**TrackingP**](#s:tracking.params): Tracking parameters.

%---------------------------------------------------------------------------------------------------
(s:match)=
## Match Element

Orbit, Twiss, and dispersion matching element.

Under Construction...

Element parameter groups associated with this element type are:
- [**ApertureP**](#s:aperture.params): Aperture parameters.
- [**BodyShiftP**](#s:bodyshift.params): Orientation of element with respect to its nominal position.
- [**FloorP**](#s:floor.params): Floor position and orientation.
- [**MetaP**](#s:meta.params): Meta parameters.
- [**ReferenceP**](#s:ref.params): Reference parameters.
- [**ReferenceChangeP**](#s:refchange.params): Reference energy change and/or reference time correction.
- [**TrackingP**](#s:tracking.params): Tracking parameters.

The length of this element is considered to be zero so if `Length` is specified, it must be zero.

%---------------------------------------------------------------------------------------------------
(s:multipole)=
## Multipole Element

Multipole element.

Under Construction...

Element parameter groups associated with this element type are:
- [**ApertureP**](#s:aperture.params): Aperture parameters.
- [**BodyShiftP**](#s:bodyshift.params): Orientation of element with respect to its nominal position.
- [**ElectricMultipoleP**](#s:elec.mult.params): Electric multipoles
- [**FloorP**](#s:floor.params): Floor position and orientation.
- [**MagneticMultipoleP**](#s:mag.mult.params): Magnetic multipoles.
- [**MetaP**](#s:meta.params): Meta parameters.
- [**ReferenceP**](#s:ref.params): Reference parameters.
- [**ReferenceChangeP**](#s:refchange.params): Reference energy change and/or reference time correction.
- [**TrackingP**](#s:tracking.params): Tracking parameters.

%---------------------------------------------------------------------------------------------------
(s:nullele)=
## NullEle Element

Placeholder element used for bookkeeping.

Under Construction...

%---------------------------------------------------------------------------------------------------
(s:octupole)=
## Octupole Element

Octupole element.

Under Construction...

Element parameter groups associated with this element type are:
- [**ApertureP**](#s:aperture.params): Aperture parameters.
- [**BodyShiftP**](#s:bodyshift.params): Orientation of element with respect to its nominal position.
- [**ElectricMultipoleP**](#s:elec.mult.params): Electric multipoles
- [**FloorP**](#s:floor.params): Floor position and orientation.
- [**MagneticMultipoleP**](#s:mag.mult.params): Magnetic multipoles.
- [**MetaP**](#s:meta.params): Meta parameters.
- [**ReferenceP**](#s:ref.params): Reference parameters.
- [**ReferenceChangeP**](#s:refchange.params): Reference energy change and/or reference time correction.
- [**TrackingP**](#s:tracking.params): Tracking parameters.

%---------------------------------------------------------------------------------------------------
(s:patch)=
## Patch Element

Crooked drift used to shift the reference orbit.

Under Construction...

Element parameter groups associated with this element type are:
- [**ApertureP**](#s:aperture.params): Aperture parameters.
- [**BodyShiftP**](#s:bodyshift.params): Orientation of element with respect to its nominal position.
- [**FloorP**](#s:floor.params): Floor position and orientation.
- [**MetaP**](#s:meta.params): Meta parameters.
- [**ReferenceP**](#s:ref.params): Reference parameters.
- [**ReferenceChangeP**](#s:refchange.params): Reference energy change and/or reference time correction.
- [**TrackingP**](#s:tracking.params): Tracking parameters.

%---------------------------------------------------------------------------------------------------
(s:quadrupole)=
## Quadrupole Element

Under Construction...

Element parameter groups associated with this element type are:
- [**ApertureP**](#s:aperture.params): Aperture parameters.
- [**BodyShiftP**](#s:bodyshift.params): Orientation of element with respect to its nominal position.
- [**ElectricMultipoleP**](#s:elec.mult.params): Electric multipoles
- [**FloorP**](#s:floor.params): Floor position and orientation.
- [**MagneticMultipoleP**](#s:mag.mult.params): Magnetic multipoles.
- [**MetaP**](#s:meta.params): Meta parameters.
- [**ReferenceP**](#s:ref.params): Reference parameters.
- [**ReferenceChangeP**](#s:refchange.params): Reference energy change and/or reference time correction.
- [**TrackingP**](#s:tracking.params): Tracking parameters.

%---------------------------------------------------------------------------------------------------
(s:rfcavity)=
## RFCavity Element

Under Construction...

Element parameter groups associated with this element type are:
- [**ApertureP**](#s:aperture.params): Aperture parameters.
- [**BodyShiftP**](#s:bodyshift.params): Orientation of element with respect to its nominal position.
- [**ElectricMultipoleP**](#s:elec.mult.params): Electric multipoles
- [**FloorP**](#s:floor.params): Floor position and orientation.
- [**MagneticMultipoleP**](#s:mag.mult.params): Magnetic multipoles.
- [**MetaP**](#s:meta.params): Meta parameters.
- [**ReferenceP**](#s:ref.params): Reference parameters.
- [**ReferenceChangeP**](#s:refchange.params): Reference energy change and/or reference time correction.
- [**SolenoidP**](#s:solenoid.params): Solenoid field.
- [**TrackingP**](#s:tracking.params): Tracking parameters.

Note: Multipole parameters represent DC fields. A common example is a DC solenoid field which
helps focusing.

%---------------------------------------------------------------------------------------------------
(s:sextupole)=
## Sextupole Element

Under Construction...

Element parameter groups associated with this element type are:
- [**ApertureP**](#s:aperture.params): Aperture parameters.
- [**BodyShiftP**](#s:bodyshift.params): Orientation of element with respect to its nominal position.
- [**ElectricMultipoleP**](#s:elec.mult.params): Electric multipoles
- [**FloorP**](#s:floor.params): Floor position and orientation.
- [**MagneticMultipoleP**](#s:mag.mult.params): Magnetic multipoles.
- [**MetaP**](#s:meta.params): Meta parameters.
- [**ReferenceP**](#s:ref.params): Reference parameters.
- [**ReferenceChangeP**](#s:refchange.params): Reference energy change and/or reference time correction.
- [**TrackingP**](#s:tracking.params): Tracking parameters.

%---------------------------------------------------------------------------------------------------
(s:solenoid)=
## Solenoid Element

Under Construction...

Element parameter groups associated with this element type are:
- [**ApertureP**](#s:aperture.params): Aperture parameters.
- [**BodyShiftP**](#s:bodyshift.params): Orientation of element with respect to its nominal position.
- [**ElectricMultipoleP**](#s:elec.mult.params): Electric multipoles
- [**FloorP**](#s:floor.params): Floor position and orientation.
- [**MagneticMultipoleP**](#s:mag.mult.params): Magnetic multipoles.
- [**MetaP**](#s:meta.params): Meta parameters.
- [**ReferenceP**](#s:ref.params): Reference parameters.
- [**ReferenceChangeP**](#s:refchange.params): Reference energy change and/or reference time correction.
- [**SolenoidP**](#s:solenoid.params): Solenoid field.
- [**TrackingP**](#s:tracking.params): Tracking parameters.

%---------------------------------------------------------------------------------------------------
(s:taylor)=
## Taylor Element

Taylor map element

Under Construction...

Element parameter groups associated with this element type are:
- [**ApertureP**](#s:aperture.params): Aperture parameters.
- [**BodyShiftP**](#s:bodyshift.params): Orientation of element with respect to its nominal position.
- [**FloorP**](#s:floor.params): Floor position and orientation.
- [**MetaP**](#s:meta.params): Meta parameters.
- [**ReferenceP**](#s:ref.params): Reference parameters.
- [**ReferenceChangeP**](#s:refchange.params): Reference energy change and/or reference time correction.
- [**TrackingP**](#s:tracking.params): Tracking parameters.

The length of this element is considered to be zero so if `Length` is specified, it must be zero.

%---------------------------------------------------------------------------------------------------
(s:wiggler)=
## Wiggler Element

Under Construction...

Element parameter groups associated with this element type are:
- [**ApertureP**](#s:aperture.params): Aperture parameters.
- [**BodyShiftP**](#s:bodyshift.params): Orientation of element with respect to its nominal position.
- [**ElectricMultipoleP**](#s:elec.mult.params): Electric multipoles
- [**FloorP**](#s:floor.params): Floor position and orientation.
- [**MagneticMultipoleP**](#s:mag.mult.params): Magnetic multipoles.
- [**MetaP**](#s:meta.params): Meta parameters.
- [**ReferenceP**](#s:ref.params): Reference parameters.
- [**ReferenceChangeP**](#s:refchange.params): Reference energy change and/or reference time correction.
- [**TrackingP**](#s:tracking.params): Tracking parameters.

