# Beam Designer

## Purpose
Beam Designer is an interactive web app that calculates and displays the
shear, moment, and deflection behavior of a beam. It also checks bending
strength and deflection against the specified limits.

## Inputs
- Support condition: simply supported or cantilever
- Span: feet (ft), greater than zero
- Point loads:
  - Magnitude: kips (kip), downward
  - Position along the beam: feet (ft), from the left support or fixed end
  - Multiple point loads may be added
- Uniform loads:
  - Magnitude: kips per foot (kip/ft), downward
  - Start and end positions along the beam: feet (ft), from the left support
    or fixed end
  - Multiple uniform-load segments may be added
- Member type: steel W-shape or lumber
- Steel W-shape:
  - Selected by W-shape size from a built-in section database
  - Section modulus S and moment of inertia I are provided by the database
- Lumber:
  - Selected by size
  - Gross rectangular dimensions and section properties are used
- Waste factor:
  - Optional percentage from 0% to 15%
  - Displayed as a slider with a numeric current-value indicator
  - Default: 10%
- Material properties:
  - Modulus of elasticity E: ksi
  - Allowable bending stress Fb: ksi
- All load values must be entered as positive magnitudes; negative loads
  are not allowed
- Required fields must be populated before calculations may run
- The deflection limit is fixed at span/360

## Assumptions
The assumptions used by the app can be opened from an info button in the
interface.

- Units are consistent with the units shown in the Inputs section.
- Reactions and internal forces are reported in kips and kip-feet.
- Deflection is reported in inches.
- Bending stress is reported in ksi and is calculated as fb = M/S.
- The app analyzes one beam with static loads.
- Point loads act vertically downward at a position along the span.
- Uniform loads act vertically downward over their specified segments.
- Deflection uses the elastic beam deflection equations for the selected
  support and load conditions.
- Beam self-weight is not included unless entered as a uniform load.

## Calculations
- Reactions, shear, and moment from statics
- Deflection in inches
- Bending stress fb = M/S, compared to the allowable stress
- Deflection compared to span/360

## Outputs
- The beam with its loads, and the three diagrams
- Pass or fail for bending and deflection

## Look and feel
Clean and professional, with an example beam loaded when it opens.

## Validation
20 ft simply supported W12x26 with 1 kip/ft: M = 50.0 kip-ft,
deflection 0.609 in.

## Out of scope
Continuous beams and buckling.

## Build stages

### Stage 1: Page layout mockup
Create the static layout: header, input panel, assumptions info button,
beam diagram area, three diagram panels, and pass/fail summary. Use the
example beam as placeholder labels and sample diagram outlines.

**Test:** Check the desktop and mobile layout, confirm every section is
readable, and verify that the info button opens and closes the assumptions
panel.

### Stage 2: Input controls and validation
Add support-type selection, span, point-load rows, uniform-load rows, and
member selection controls. Include add/remove actions and positive-value
validation.

**Test:** Try valid and invalid values; confirm the calculate action remains
unavailable until required fields are valid and load positions remain within
the span.

### Stage 3: Beam and load visualization
Draw the beam with its supports and place entered point and uniform loads
visually along it. Keep calculations out of this stage.

**Test:** Check that support symbols update between simply supported and
cantilever, and verify load positions scale correctly at each beam end and
between supports.

### Stage 4: Static reactions and diagrams
Implement reactions, shear, and bending moment for point and uniform loads.
Generate the shear and moment diagrams and report maximum values.

**Test:** First test the simply supported uniform-load example: expected
maximum moment should be 50.0 kip-ft. Then test a cantilever and a
combination of point loads against hand calculations.

### Stage 5: Deflection and bending calculations
Add EI deflection calculations, maximum bending stress using fb = M/S, and
unit conversions. Generate the deflection diagram.

**Test:** Test the W12x26 example; verify M = 50.0 kip-ft and deflection
approximately 0.609 inches. Add a separate check of units and a known
cantilever deflection case.

### Stage 6: Pass/fail results and polish
Compare maximum bending stress against Fb and maximum deflection against
span/360. Add clear pass/fail indicators, values, utilization percentages,
and reset/example controls.

**Test:** Find combinations that clearly pass and fail each check independently,
confirm the correct indicator appears, and verify the displayed formula, units,
and max-value locations.