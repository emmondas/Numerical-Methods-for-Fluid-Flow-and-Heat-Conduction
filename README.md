# Numerical-Methods-for-Fluid-Flow-and-Heat-Conduction
A MATLAB project that applies a full toolkit of numerical methods to two canonical engineering problems: laminar flow through a circular pipe (Hagen-Poiseuille flow) and 1D steady-state heat conduction through a multi-layer composite wall.
Problems Studied

Problem 1 — Laminar Pipe Flow (Chapters 1–3)
Analyzes fully-developed laminar flow of air (μ = 1.813 × 10⁻⁵ Pa·s) through a pipe of radius R = 0.2 m and length L = 20 m under a pressure drop Δp = 5 Pa.

Problem 2 — Composite Wall Heat Transfer (Chapters 4–7)
Solves for the temperature distribution through a four-layer wall (copper, aluminum, stainless steel, and an insulating layer) with fixed boundary temperatures of 800 °C and 0 °C on either side.

Numerical Methods Implemented

Each chapter tackles a distinct numerical technique built from scratch (no black-box toolbox calls):

Chapter 1 — Analytical baseline & error analysis: Computes the theoretical parabolic velocity profile from Hagen-Poiseuille, decodes 8-bit binary experimental velocity data into decimal, and reports the absolute relative true error at each radial position
Chapter 2 — Numerical differentiation: Estimates wall shear stress using forward, central, and backward finite-difference approximations of dV/dr on non-uniform spacing
Chapter 3 — Root finding: A from-scratch bisection method that inverts the velocity equation to find the radial position for a user-specified velocity, iterating until the absolute relative approximate error falls below 5 × 10⁻⁵
Chapter 4 — Linear systems: Sets up and solves the thermal-resistance network for the four-layer wall as a matrix equation Ax = B to recover interior node temperatures
Chapter 5 — Interpolation: Two approaches on the same data — a single 4th-order polynomial fit through all five nodes, plus a piecewise quadratic spline with continuity and slope-matching constraints at the internal knots
Chapter 6 — Regression: A hand-computed least-squares quadratic regression using the normal equations, along with a residual plot to visually assess goodness of fit
Chapter 7 (Extra Credit) — Numerical integration: Applies the composite trapezoidal rule to integrate a variable thermal conductivity function k(x) = x⁻ˣ · ln(x + 1.2), adaptively increasing the number of trapezoids until the absolute relative true error against the symbolic exact integral is below 10⁻⁵
Deliverables

The script generates a labeled results table (radial position, theoretical velocity, experimental velocity, error) and six figures: velocity profiles overlaid, error vs. position, shear stress vs. position, the wall temperature distribution with interpolated polynomial and spline overlays, the regression fit, and the residual plot.

Tech Stack
MATLAB (Symbolic Math Toolbox used only for the exact integral in Chapter 7's error benchmark)
No numerical-methods toolboxes used — every method is implemented from first principles
External input: Ch1_Velocity_Binary.txt (binary-encoded experimental velocity measurements)
How to Run
Open the script in MATLAB with Ch1_Velocity_Binary.txt in the working directory
Run the script section by section (each %% block corresponds to one part of the report)
When Chapter 3 prompts, enter a target velocity (must lie within the theoretical velocity range) and an initial high guess for the radial position
Notes

The project is organized to mirror an academic report — each %% section is a self-contained deliverable, and the accompanying PDF report explains the derivation and results for each part. It's a good demonstration piece for anyone interested in seeing classical numerical methods implemented directly rather than through library calls.
