# three-body-simulation
Python project simulating the 3-body problem in physics.

### Starting Assumptions
- Planetary bodies are in an isolated system (no other forces acting on them other than gravitational forces among themselves).
- 

### Process
1. Using Newton's Laws of Motion and the Law of Universal Gravitation, derive a set of differential equations governing the motion of each planetary body.

```math
\Sigma \vec{F}_{\text{ext, 1}} = m_1 \frac{d^2 \vec{p}_1}{dt^2} = \vec{F}_{\text{2,1}} + \vec{F}_{\text{3,1}}
```

2. Use characteristic variables to simplify the variables within the set of differential equations into dimensionless quantities.
3. Transform system of 2nd order differential equations into system of first ODEs.