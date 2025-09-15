# Lorentz Solver

This Lorentz solver is designed to compute the paths of particles in complex custom electromagnetic spaces and then animate them using the Manim library for maximum clarity.  

[GitHub Repo](https://www.github.com/ihsan-sa/Lorentz-Solver-V2)

## The Lorentz Force and solvers

A Lorentz solver is a simulation tool which simulates the effect of the Lorentz force on particles in various electromagnetic spaces. The Lorentz force on a charge particle is described by the following equation:


$$
F = q(\vec{E} + \vec{v} \times \vec{B})
$$


where  is the Lorentz force,  is the charge on the particle,  and  are the vector describing the electric and magnetic fields at the location of the particle respectively, and  is the velocity of the particle. For more details on the scientific principles and equations involved in the simulations of various objects in different spaces, please see the Physics and Math page.

## Solver operation

This Lorentz solver functions by creating a space and adding various objects. These objects have predefined electric and magnetic fields. At each time step, the simulation computes the total electric and magnetic field at particles' location. Then, a numerical integration method is used to compute the updated acceleration, velocity and position of the particle. These are logged to a CSV and then read by the animation program. 

The user specifies the simulation environment settings, including simulation type, simulation and animation duration, time step and numerical method. The user then adds objects and particles to the space, specifying the required parameters. For more information about the configuration of a simulation, please see the Simulation and Configuration page.

## Simulation examples

### Particle motion simulation 1

<figure>
  <video width="100%" controls>
    <source src="/Projects/LorentzSolver/sim1.mp4" type="video/mp4">
    Your browser does not support the video tag.
  </video>
  <figcaption>Figure 1: Video of particle simulation.</figcaption>
</figure>

### Particle motion simulation 2 - no intro

<figure>
  <video width="100%" controls>
    <source src="/Projects/LorentzSolver/sim2.mp4" type="video/mp4">
    Your browser does not support the video tag.
  </video>
  <figcaption>Figure 2: Video of particle simulation - no intro.</figcaption>
</figure>

### \(\vec{E} \times \vec{B}\) drift simulation

<figure>
  <video width="100%" controls>
    <source src="/Projects/LorentzSolver/sim3.mp4" type="video/mp4">
    Your browser does not support the video tag.
  </video>
  <figcaption>Figure 3: Video of \(\vec{E} \times \vec{B}\) drift simulation.</figcaption>
</figure>

### grad(\(\vec{B}\)) drift simulation

<figure>
  <video width="100%" controls>
    <source src="/Projects/LorentzSolver/sim4.mp4" type="video/mp4">
    Your browser does not support the video tag.
  </video>
  <figcaption>Figure 4: Video of grad(\(\vec{B}\)) drift simulation.</figcaption>
</figure>

### Rudimentary visualization of grad(\(\vec{B}\)) simulation \(\vec{B}\) vector field.

<figure>
  <video width="100%" controls>
    <source src="/Projects/LorentzSolver/sim5.mp4" type="video/mp4">
    Your browser does not support the video tag.
  </video>
  <figcaption>Figure 5: Video of udimentary visualization of grad(\(\vec{B}\)) simulation \(\vec{B}\) vector field.</figcaption>
</figure>