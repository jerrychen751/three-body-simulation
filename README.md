# three-body-simulation
Python project simulating the 3-body problem in physics.

### Assumptions/Simplifications
- Planetary bodies are in an isolated system (no other forces acting on them other than gravitational forces among themselves).
- Planetary bodies are point masses (avoid dealing with collisions).
- The force between two bodies is described by Newton's law of universal gravitation.

### Process
1. Using Newton's Laws of Motion and the Law of Universal Gravitation, derive a set of differential equations governing the motion of each planetary body.

The force of that `i` exerts on `j` is denoted here as $\vec{F}_{\text{i,j}}.

```math
\Sigma \vec{F}_{\text{ext, 1}} = m_1 \frac{d^2 \vec{p}_1}{dt^2} = \vec{F}_{\text{2,1}} + \vec{F}_{\text{3,1}}
```
```math
\Sigma \vec{F}_{\text{ext, 2}} = m_2 \frac{d^2 \vec{p}_2}{dt^2} = \vec{F}_{\text{1,2}} + \vec{F}_{\text{3,2}}
```
```math
\Sigma \vec{F}_{\text{ext, 3}} = m_3 \frac{d^2 \vec{p}_3}{dt^2} = \vec{F}_{\text{1,3}} + \vec{F}_{\text{2,3}}
```

Rewriting the equations with the law of gravitation (where $\vec{p}_i$ is the 3D coordinate/position of the i-th planetary body) and simplifying:
```math
\begin{gather}
\frac{d^2\vec{p}_1}{dt^2} &= Gm_3 \frac{\vec{p}_3 - \vec{p}_1}{|\vec{p}_3 - \vec{p}_1|^3} + Gm_2 \frac{\vec{p}_2 - \vec{p}_1}{|\vec{p}_2 - \vec{p}_1|^3} \\
\frac{d^2\vec{p}_2}{dt^2} &= Gm_3 \frac{\vec{p}_3 - \vec{p}_2}{|\vec{p}_3 - \vec{p}_2|^3} + Gm_1 \frac{\vec{p}_1 - \vec{p}_2}{|\vec{p}_1 - \vec{p}_2|^3} \\
\frac{d^2\vec{p}_3}{dt^2} &= Gm_1 \frac{\vec{p}_1 - \vec{p}_3}{|\vec{p}_1 - \vec{p}_3|^3} + Gm_2 \frac{\vec{p}_2 - \vec{p}_3}{|\vec{p}_2 - \vec{p}_3|^3}
\end{gather}
```

2. Use fundamental dimensions to rewrite the variables within the set of differential equations into dimensionless quantities.

```math
\begin{gather}
p' = p/L \\
m' = m/M \\
t' = t/T = \sqrt{\frac{MG}{L^3}}
\end{gather}
```

($\vec{p}'$, $m'$, and $t'$ are dimensionless variables, and $L$ and $M$ are fundamental dimensions for length and mass.)

Plugging these definitions into the above set of differential equations, we get this:
```math
\begin{gather}
\frac{d^2 (L \vec{p'}_1)}{d(\frac{t'}{\sqrt{GM/L^3}})^2} = G m_3 \frac{L(\vec{p'}_3 - \vec{p'}_1)}{|L(\vec{p'}_3 - \vec{p'}_1)|^3} + G m_2 \frac{L(\vec{p'}_2 - \vec{p'}_1)}{|L(\vec{p'}_2 - \vec{p'}_1)|^3} \\
\frac{d^2 (L \vec{p'}_2)}{d(\frac{t'}{\sqrt{GM/L^3}})^2} = G m_1 \frac{L(\vec{p'}_1 - \vec{p'}_2)}{|L(\vec{p'}_1 - \vec{p'}_2)|^3} + G m_3 \frac{L(\vec{p'}_3 - \vec{p'}_2)}{|L(\vec{p'}_3 - \vec{p'}_2)|^3} \\
\frac{d^2 (L \vec{p'}_3)}{d(\frac{t'}{\sqrt{GM/L^3}})^2} = G m_1 \frac{L(\vec{p'}_1 - \vec{p'}_3)}{|L(\vec{p'}_1 - \vec{p'}_3)|^3} + G m_2 \frac{L(\vec{p'}_2 - \vec{p'}_3)}{|L(\vec{p'}_2 - \vec{p'}_3)|^3} \\
\end{gather}
```

After simplifying:
```math
\begin{gather}
\frac{d^2\vec{p'}_1}{dt'^2} = m'_3 \frac{\vec{p'}_3 - \vec{p'}_1}{|\vec{p'}_3 - \vec{p'}_1|^3} + m'_2 \frac{\vec{p'}_2 - \vec{p'}_1}{|\vec{p'}_2 - \vec{p'}_1|^3} \\
\frac{d^2\vec{p'}_2}{dt'^2} = m'_3 \frac{\vec{p'}_3 - \vec{p'}_2}{|\vec{p'}_3 - \vec{p'}_2|^3} + m'_1 \frac{\vec{p'}_1 - \vec{p'}_2}{|\vec{p'}_1 - \vec{p'}_2|^3} \\
\frac{d^2\vec{p'}_3}{dt'^2} = m'_1 \frac{\vec{p'}_1 - \vec{p'}_3}{|\vec{p'}_1 - \vec{p'}_3|^3} + m'_2 \frac{\vec{p'}_2 - \vec{p'}_3}{|\vec{p'}_2 - \vec{p'}_3|^3}
\end{gather}
```

3. Transform system of 2nd order differential equations into system of first ODEs.

By converting the set of 3 second-order ODEs into 6 first-order ODEs, Python's numerical solving methods can be applied.

```math
\begin{aligned}
\frac{d\vec{p'}_1}{dt} &= \vec{v}_1 \\
\frac{d\vec{p'}_2}{dt} &= \vec{v}_2 \\
\frac{d\vec{p'}_3}{dt} &= \vec{v}_3 \\
\frac{d\vec{v}_1}{dt} &= m_3 \frac{\vec{p'}_3 - \vec{p'}_1}{|\vec{p'}_3 - \vec{p'}_1|^3} + m_2 \frac{\vec{p'}_2 - \vec{p'}_1}{|\vec{p'}_2 - \vec{p'}_1|^3} \\[2ex]
\frac{d\vec{v}_2}{dt} &= m_3 \frac{\vec{p'}_3 - \vec{p'}_2}{|\vec{p'}_3 - \vec{p'}_2|^3} + m_1 \frac{\vec{p'}_1 - \vec{p'}_2}{|\vec{p'}_1 - \vec{p'}_2|^3} \\[2ex]
\frac{d\vec{v}_3}{dt} &= m_1 \frac{\vec{p'}_1 - \vec{p'}_3}{|\vec{p'}_1 - \vec{p'}_3|^3} + m_2 \frac{\vec{p'}_2 - \vec{p'}_3}{|\vec{p'}_2 - \vec{p'}_3|^3}
\end{aligned}
```

Now, it becomes an initial value problem. The position of any planetary body can be computed at any time given their initial positions and velocities.