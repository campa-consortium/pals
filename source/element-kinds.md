(c:ele.kinds)=
# Element Kinds

Note: `name`, `length`, and `s_position` parameters stand alone and not part of any parameter group.

Example:
```{code} yaml
Solenoid:
  name: cleo
  length: 3.74
  SolenoidP:
    Ksol: -0.15
```

%---------------------------------------------------------------------------------------------------
(s:ackicker)=
## ACKicker Element

Time varying kicker element

Under Construction...

Element parameter groups associated with this element kind are:
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

Element parameter groups associated with this element kind are:
- [**ApertureP**](#s:aperture.params): Aperture parameters.
- [**BeamBeamP**](#s:beambeam.params): Beam-beam interaction parameters.
- [**BodyShiftP**](#s:bodyshift.params): Orientation of element with respect to its nominal position.
- [**FloorP**](#s:floor.params): Floor position and orientation.
- [**MetaP**](#s:meta.params): Meta parameters.
- [**ReferenceP**](#s:ref.params): Reference parameters.
- [**ReferenceChangeP**](#s:refchange.params): Reference energy change and/or reference time correction.
- [**TrackingP**](#s:tracking.params): Tracking parameters.

The length of this element is considered to be zero so if `length` is specified, it must be zero.

%---------------------------------------------------------------------------------------------------
(s:beginningele)=
## BeginningEle Element

Initial element at start of a branch.

Under Construction...

Element parameter groups associated with this element kind are:
- [**ApertureP**](#s:aperture.params): Aperture parameters.
- [**BodyShiftP**](#s:bodyshift.params): Orientation of element with respect to its nominal position.
- [**FloorP**](#s:floor.params): Floor position and orientation.
- [**MetaP**](#s:meta.params): Meta parameters.
- [**ReferenceP**](#s:ref.params): Reference parameters.
- [**TrackingP**](#s:tracking.params): Tracking parameters.

The length of this element is considered to be zero so if `length` is specified, it must be zero.

%---------------------------------------------------------------------------------------------------
(s:bend)=
##  Bend Elements: RBend and SBend

Dipole bend. There are two kinds of bends depending upon the "logical shape". 
The `RBend` element has a "rectangular" logical shape and the `SBend` element has a "sector"
logical shape.

Element parameter groups associated with this element kind are:
- [**ApertureP**](#s:aperture.params): Aperture parameters.
- [**BendP**](#s:bend.params): Bend parameters
- [**BodyShiftP**](#s:bodyshift.params): Orientation of element with respect to its nominal position.
- [**ElectricMultipoleP**](#s:elec.mult.params): Electric multipoles
- [**FloorP**](#s:floor.params): Floor position and orientation.
- [**MagneticMultipoleP**](#s:mag.mult.params): Magnetic multipoles.
- [**MetaP**](#s:meta.params): Meta parameters.
- [**ReferenceP**](#s:ref.params): Reference parameters.
- [**ReferenceChangeP**](#s:refchange.params): Reference energy change and/or reference time correction.
- [**TrackingP**](#s:tracking.params): Tracking parameters.

`RBend` and `SBend` elements are parameterized exactly the same way by the `BendP` parameter group. 
For example, `e1` and `e1_rect` have the same meaning for both kinds of bends.

The logical shape of a bend, in most situations, is irrelevant.
The only case where the logical shape can be used by a program is when the bend angle is varied.
In this case, for a `SBend`, the face angles `e1` and `e2` can be
held constant and `e1_rect` and `e2_rect` can be varied to keep the relationship
between `e1` and `e1_rect`, and `e2` and `e2_rect` satisfied as discussing in the
[`BendP`](#s:bend.params) documentation. Similarly, for a `RBend`,
the face angles `e1_rect` and `e2_rect` can be
held constant and `e1` and `e2` can be varied to keep the relationship
between `e1` and `e1_rect`, and `e2` and `e2_rect` satisfied.

%---------------------------------------------------------------------------------------------------
(s:converter)=
## Converter Element

Target to produce new species. EG: Positron converter.

Under Construction...

Element parameter groups associated with this element kind are:
- [**ApertureP**](#s:aperture.params): Aperture parameters.
- [**BodyShiftP**](#s:bodyshift.params): Orientation of element with respect to its nominal position.
- [**ElectricMultipoleP**](#s:elec.mult.params): Electric multipoles
- [**FloorP**](#s:floor.params): Floor position and orientation.
- [**MagneticMultipoleP**](#s:mag.mult.params): Magnetic multipoles.
- [**MetaP**](#s:meta.params): Meta parameters.
- [**ReferenceP**](#s:ref.params): Reference parameters.
- [**ReferenceChangeP**](#s:refchange.params): Reference energy change and/or reference time correction.
- [**TrackingP**](#s:tracking.params): Tracking parameters.

The length of this element is considered to be zero so if `length` is specified, it must be zero.

%---------------------------------------------------------------------------------------------------
(s:crabcavity)=
## CrabCavity Element

RF crab cavity

Under Construction...

Element parameter groups associated with this element kind are:
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

Element parameter groups associated with this element kind are:
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

Element parameter groups associated with this element kind are:
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

Note: This element does not have a `length` nor an `s_position`.

%---------------------------------------------------------------------------------------------------
(s:fiducial)=
## Fiducial Element

Global coordinate system fiducial point.

Under Construction...

The length of this element is considered to be zero so if `length` is specified, it must be zero.

%---------------------------------------------------------------------------------------------------
(s:floorshift)=
## FloorShift Element

Global coordinates shift.

Under Construction...

Element parameter groups associated with this element kind are:
- [**MetaP**](#s:meta.params): Meta parameters.
- [**ReferenceP**](#s:ref.params): Reference parameters.

%---------------------------------------------------------------------------------------------------
(s:foil)=
## Foil Element

Material that can strip electrons from a particle.
Will also cause energy loss and diffusion.

Under Construction...

Element parameter groups associated with this element kind are:
- [**ApertureP**](#s:aperture.params): Aperture parameters.
- [**BodyShiftP**](#s:bodyshift.params): Orientation of element with respect to its nominal position.
- [**FloorP**](#s:floor.params): Floor position and orientation.
- [**MetaP**](#s:meta.params): Meta parameters.
- [**ReferenceP**](#s:ref.params): Reference parameters.
- [**ReferenceChangeP**](#s:refchange.params): Reference energy change and/or reference time correction.
- [**TrackingP**](#s:tracking.params): Tracking parameters.

The length of this element is considered to be zero so if `length` is specified, it must be zero.

%---------------------------------------------------------------------------------------------------
(s:fork)=
## Fork Element

Element used to connect lattice branches together.

Under Construction...

Element parameter groups associated with this element kind are:
- [**ApertureP**](#s:aperture.params): Aperture parameters.
- [**BodyShiftP**](#s:bodyshift.params): Orientation of element with respect to its nominal position.
- [**FloorP**](#s:floor.params): Floor position and orientation.
- [**MetaP**](#s:meta.params): Meta parameters.
- [**ReferenceP**](#s:ref.params): Reference parameters.
- [**ReferenceChangeP**](#s:refchange.params): Reference energy change and/or reference time correction.
- [**TrackingP**](#s:tracking.params): Tracking parameters.

The length of this element is considered to be zero so if `length` is specified, it must be zero.

%---------------------------------------------------------------------------------------------------
(s:girder)=
## Girder Element

Element to support in space a group of other elements.

Under Construction...

Note: This element does not have a `length` nor an `s_position`.

%---------------------------------------------------------------------------------------------------
(s:instrument)=
## Instrument Element

Measurement element.

Under Construction...

Element parameter groups associated with this element kind are:
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

Element parameter groups associated with this element kind are:
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

Element parameter groups associated with this element kind are:
- [**ApertureP**](#s:aperture.params): Aperture parameters.
- [**BodyShiftP**](#s:bodyshift.params): Orientation of element with respect to its nominal position.
- [**FloorP**](#s:floor.params): Floor position and orientation.
- [**MetaP**](#s:meta.params): Meta parameters.
- [**ReferenceP**](#s:ref.params): Reference parameters.
- [**ReferenceChangeP**](#s:refchange.params): Reference energy change and/or reference time correction.
- [**TrackingP**](#s:tracking.params): Tracking parameters.

The length of this element is considered to be zero so if `length` is specified, it must be zero.

%---------------------------------------------------------------------------------------------------
(s:mask)=
## Mask Element

Collimation element.

Under Construction...

Element parameter groups associated with this element kind are:
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

Element parameter groups associated with this element kind are:
- [**ApertureP**](#s:aperture.params): Aperture parameters.
- [**BodyShiftP**](#s:bodyshift.params): Orientation of element with respect to its nominal position.
- [**FloorP**](#s:floor.params): Floor position and orientation.
- [**MetaP**](#s:meta.params): Meta parameters.
- [**ReferenceP**](#s:ref.params): Reference parameters.
- [**ReferenceChangeP**](#s:refchange.params): Reference energy change and/or reference time correction.
- [**TrackingP**](#s:tracking.params): Tracking parameters.

The length of this element is considered to be zero so if `length` is specified, it must be zero.

%---------------------------------------------------------------------------------------------------
(s:multipole)=
## Multipole Element

Multipole element.

Under Construction...

Element parameter groups associated with this element kind are:
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

Element parameter groups associated with this element kind are:
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

Element parameter groups associated with this element kind are:
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

Element parameter groups associated with this element kind are:
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

Element parameter groups associated with this element kind are:
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

Element parameter groups associated with this element kind are:
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

Element parameter groups associated with this element kind are:
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

Element parameter groups associated with this element kind are:
- [**ApertureP**](#s:aperture.params): Aperture parameters.
- [**BodyShiftP**](#s:bodyshift.params): Orientation of element with respect to its nominal position.
- [**FloorP**](#s:floor.params): Floor position and orientation.
- [**MetaP**](#s:meta.params): Meta parameters.
- [**ReferenceP**](#s:ref.params): Reference parameters.
- [**ReferenceChangeP**](#s:refchange.params): Reference energy change and/or reference time correction.
- [**TrackingP**](#s:tracking.params): Tracking parameters.

The length of this element is considered to be zero so if `length` is specified, it must be zero.

%---------------------------------------------------------------------------------------------------
(s:unionele)=
## UnionEle Element

The `UnionEle` element holds a set of overlapping elements.

Element parameter groups associated with this element kind are:
- [**ApertureP**](#s:aperture.params): Aperture parameters.
- [**BodyShiftP**](#s:bodyshift.params): Orientation of element with respect to its nominal position.
- [**FloorP**](#s:floor.params): Floor position and orientation.
- [**MetaP**](#s:meta.params): Meta parameters.
- [**ReferenceP**](#s:ref.params): Reference parameters.
- [**ReferenceChangeP**](#s:refchange.params): Reference energy change and/or reference time correction.
- [**TrackingP**](#s:tracking.params): Tracking parameters.

For each element contained in the `UnionEle`, the nominal position of the contained element is
such that the center of the contained element is at the center of the `UnionEle` with the
body coordinates of the contained element aligned with the body coordinates of the `UnionEle`.
Any contained element can be shifted from the nominal position by setting the contained element's
`BodyShiftP` parameters. The entire collection of elements can be oriented using the `UnionEle`'s
`BodyShiftP` parameters.

Example:
```{code} yaml
UnionEle:
  name: MMM
  length: 2.1
  Solenoid:
    name: Sa      # Contained elements can be named.
    length: 1.3
    BodyShiftP:          # Orient the Solenoid
      x_offset: 0.03
      ...
  RFCavity:
    name: Ra
    BodyShiftP:          # Orient the RFCavity
      y_rot: 0.012
      ...
  BodyShiftP:           # The UnionEle itself can be oriented.
    ...
```

Besides using a `UnionEle` when elements overlap physically, the other way of handling this
situation is to position elements in a beamline to overlap using the [`placement`](#s:placement) 
construct or to use [`superposition`](#s:superposition).


%---------------------------------------------------------------------------------------------------
(s:wiggler)=
## Wiggler Element

Under Construction...

Element parameter groups associated with this element kind are:
- [**ApertureP**](#s:aperture.params): Aperture parameters.
- [**BodyShiftP**](#s:bodyshift.params): Orientation of element with respect to its nominal position.
- [**ElectricMultipoleP**](#s:elec.mult.params): Electric multipoles
- [**FloorP**](#s:floor.params): Floor position and orientation.
- [**MagneticMultipoleP**](#s:mag.mult.params): Magnetic multipoles.
- [**MetaP**](#s:meta.params): Meta parameters.
- [**ReferenceP**](#s:ref.params): Reference parameters.
- [**ReferenceChangeP**](#s:refchange.params): Reference energy change and/or reference time correction.
- [**TrackingP**](#s:tracking.params): Tracking parameters.

