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
```math
\Sigma \vec{F}_{\text{ext, 2}} = m_2 \frac{d^2 \vec{p}_2}{dt^2} = \vec{F}_{\text{1,2}} + \vec{F}_{\text{3,2}}
```
```math
\Sigma \vec{F}_{\text{ext, 3}} = m_3 \frac{d^2 \vec{p}_3}{dt^2} = \vec{F}_{\text{1,3}} + \vec{F}_{\text{2,3}}
```

Rewriting the equations with the law of gravitation (where $\vec{p}_i$ is the 3D coordinate/position of the i-th planetary body):
```math
\begin{aligned}
\frac{d^2\vec{p}_1}{dt^2} &= Gm_3 \frac{\vec{p}_3 - \vec{p}_1}{|\vec{p}_3 - \vec{p}_1|^3} + Gm_2 \frac{\vec{p}_2 - \vec{p}_1}{|\vec{p}_2 - \vec{p}_1|^3} \\
\frac{d^2\vec{p}_2}{dt^2} &= Gm_3 \frac{\vec{p}_3 - \vec{p}_2}{|\vec{p}_3 - \vec{p}_2|^3} + Gm_1 \frac{\vec{p}_1 - \vec{p}_2}{|\vec{p}_1 - \vec{p}_2|^3} \\
\frac{d^2\vec{p}_3}{dt^2} &= Gm_1 \frac{\vec{p}_1 - \vec{p}_3}{|\vec{p}_1 - \vec{p}_3|^3} + Gm_2 \frac{\vec{p}_2 - \vec{p}_3}{|\vec{p}_2 - \vec{p}_3|^3}
\end{aligned}
```

2. Use characteristic variables to simplify the variables within the set of differential equations into dimensionless quantities.
3. Transform system of 2nd order differential equations into system of first ODEs.