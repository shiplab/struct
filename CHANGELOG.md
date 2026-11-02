# Changelog

## 1.0.0, November 2026

First public version.

**Structure from the blocks**
- Regions are cut at the transverse bulkheads found in the blocks and run from the aft end to the fore end of the hull. Each region has one section at its middle, on the real hull.
- Inner bottom, inner side or longitudinal bulkhead, and tween decks are read from the blocks.
- Plates, longitudinals and primary members are sized to DNV Rules for Ships Pt.3 Ch.2 (January 2015, ships under 100 m). The hull girder section modulus is checked against the rule value along the length.
- Transverse framing is guessed per region: for ships under 60 m, and for regions near the ends. It can be changed by hand. Floors, side frames, deck and tween beams use the general stiffener formula, with estimated end brackets.
- Buckling is checked in simplified form, after the classic DNV Pt.3 Ch.1 Sec.13, with the Johnson correction: plates, and longitudinals as columns.
- Hull girder shear stress is checked at the neutral axis, with the IACS UR S11 wave shear plus the still-water shear of the DBB loads.
- Rule moments are distributed along the length as in Sollied (2009). End regions are judged at their own section.
- Transverse bulkheads are sized with a simplified Sec.9 method.

**Web frames**
- One web frame per region is modelled as a plane frame of Timoshenko beams, in the manner of Nauticus Hull 3D Beam. Double bottom and double side are double skin beams; the other members are built T girders with a plate flange.
- Load cases are read from the blocks: full load, ballast and tank test.
  - Each case covers sea pressure, green sea, liquid heads and the DBB mass of dry spaces.
  - Every case can be edited or switched off, and new cases added.
- The plating is also checked as the flange of the web frames. This is biaxial buckling with the DNV interaction formula, after Sollied (2009). Where the plating fails this check, the proposal thickens it.
- Lightening holes can be given per member; they reduce its shear area.

**Learn the basics**
- Eight lessons on a box barge, after the barge example and the methods in Sollied (2009):
  1. loads, shear force and bending moment;
  2. section properties;
  3. hull girder stresses;
  4. rule moments;
  5. local strength;
  6. buckling;
  7. a web frame member by hand;
  8. holes and two-way loading.
- Each lesson has:
  - answers checked within 2%;
  - a worked solution that fills the answers;
  - a comparison with the app;
  - sliders for its conditions, where every change clears the answers.

**The app**
- Examples: the barge of the compendium (opened at start), R/V Gunnerus, PSV, AHTS, tanker, feeder container ship and handysize bulk carrier.
- Views:
  - Section, 3D and Frame views, with the profiles in their real shape;
  - the Spaces and Loads overlays in the Frame view;
  - an adjustable height for the tables.
- Report PDF; Save work and open it again.
- How to, About and a user manual (`docs/manual.pdf`).
- For educational use only (disclaimer in About, the report and the manual).
- MIT license (`LICENSE`); the Gunnerus data stays CC BY-NC 4.0.

**Fixes to the DBB core included here**, to be carried to the DBB editor:
- The still-water bending moment had the wrong sign, so hogging was taken as sagging. The load is now buoyancy minus weight, so the moment is positive in sagging, as the core states.
- The hidden buoyancy hull of the Gunnerus example is cleaned of slicing drop-outs with `dev/smooth-gunnerus.js`.
