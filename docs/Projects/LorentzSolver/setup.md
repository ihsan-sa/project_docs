# Installation and Setup

## Dependencies and installation

This project requires a number of dependencies:  

+ Manim Community dependencies, including `manim` Python library, `ffmpeg` and `Python`. Installation of these packages is attempted when makefile is run, but manual installation may be required.

+ The new version of `g++`

+ Python libraries including `pandas`, `os`, `numpy` and `csv`. Installation of these is also attempted in the makefile.

To run the default installation and compilation, run `make`. To clean up the environment, run `make clean`.   
Compiled files are stored in the `compiled_files` directory and additional text files are stored in `other_config_files`.  

## Steps

1. Run `make`

2. Update the `config.txt` file. Specific instructions will be covered in the Simulation Configuration. There is a simple config file provided for first simulations.

3. Run `./simulate.py` to run the numerical simulation and animate using Manim.

4. The resulting video can be found in the `media/videos/scene/480p15`

The C++ code reads the config file and runs the appropriate simulation. The electric and magnetic field strengths are computed at each particles' position, and then the Lorentz equation is integrated to determine the new velocity and position of each particle (see Physics and Math page). The numerical integration is performed using the algorithm specified in the config file (see Simulation Configuration section). The particle positions are logged to the `data.csv` file after each simulation timestep.  

Next, the python code reads both the config and data files and animates the data using Manim, whether it be a particle motion animation or \(\vec{E}\) or \(\vec{B}\) vector field visualization.