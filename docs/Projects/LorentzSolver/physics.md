# Physics and Math

## Lorentz Equation
### Objects
The equation for the Lorentz force on a particle moving through an electric and magnetic field is:
$$
F = q(\vec{E} + \vec{v} \times \vec{B})
$$

This equation is numerically integrated using various techniques, an RK4-euler hybrid solution being the most successful in this simulation.  
The code for this simulation can be found in the ``void Space::simulate(long double const t, long double const dt) const`` function in `./numerical_simulation/space.cpp`.

The magnetic field produced by a moving particle also needs to be accounted for.