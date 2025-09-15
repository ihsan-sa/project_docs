# Simulation Configuration

## Config file

### General structure 

The `config.txt` file has various sections, denoted by tags. The structure is shown below. The `%%` is used to denote a comment, although this is not supported in the solver.  

!!! note
    It is usually best to leave 2-3 lines between tags.

```
TITLE
%% parameters

AUTHOR
%% parameters

SIM
%% parameters

CONFIG
%% parameters

%% object definitions

# %% this is the end character. The solver will stop reading when it gets to this character.
```

### Title

The **TITLE** section is comprised of two titles lines:

```
TITLE
%% line 1
%% line 2
```

!!! example
    ```
    TITLE
    Simulation of the ExB drift of a particle
    in an electric and magnetic field
    ```

### Author

The author's name is displayed in the bottom right corner of the screen for the entire animation.

```
AUTHOR
%% name
```

!!! example
    ```
    AUTHOR
    Ihsan
    ```

### Animation settings

The **SIM** section contains one parameter, the animation time. For more animation settings, see the Animation section.

```
SIM
%% animation time
%% display the object descriptions at the start of the simulation. Add "Disp obj descp" or leave blank
```

!!! example
    ```
    SIM
    10
    Disp obj descp
    ```

### Computation settings

#### General structure

The **CONFIG** section contains information about the numerical simulation. 

```
CONFIG
%% simulation type
%% other parameters
```

The simulation type can be:

+ Lorentz Motion, which computes the path of particles in the specified space.

+ \(\vec{B}\) Field, which computes the magnetic vector field in the specified region by logging the field vectors in the space.

+ \(\vec{E}\) Field, which computes the electric vector field in the specified region by logging the field vectors in the space.

!!! note
    The \(\vec{B}\) Field and \(\vec{E}\) Field simulations are still under development and are using very crude patched together experimental code by me, various online sources and AI. This is purely experimental and will be re-written by me once experimentation is complete. All other code is written by me.

#### Lorentz motion

```
CONFIG
Lorentz Motion
%% simulation time
%% simulation time step
%% numerical method
```

The numerical method can be either RK4 Euler (recommended), RK4 Hybrid or Euler.  

!!! example 
    ```
    CONFIG
    Lorentz Motion
    10
    0.01
    RK4 Euler
    ```

#### \(\vec{B}\) Field

```
CONFIG
B Field
%% coordinates of one corner of the space
%% coordinates of the opposite corner of the space
%% Step size between vectors in 3D space
```

!!! example
    ```
    CONFIG
    B Field
    [-2,-2,-2]
    [2,2,2]
    1
    ```

#### \(\vec{E}\) Field

!!! info
    Coming soon.

```
CONFIG
E Field
%% coordinates of one corner of the space
%% coordinates of the opposite corner of the space
%% Step size between vectors in 3D space
```

!!! example
    ```
    CONFIG
    E Field
    [-1,-1,-1]
    [2,2,2]
    0.5
    ```

### Object definitions

There are a number of objects that can be added to a simulation space:

+ Particle (P)

+ Uniform Fields  

    + Uniform Magnetic Field (UMF)

    + Uniform Electric Field (UEF)

+ Static Point charge (SPC)

+ Sectioned Uniform Fields   

    + Sectioned Uniform Magnetic Field (SUMF)

    + Sectioned Uniform Electric Field (SUEF)

+ Wire (W)

+ Wire Loop (WL)

+ Magnetic dipole (MD) -- coming soon

Later, more complex premade combinations of objects will be added. For example: 

+ Tokamak Fusion Reactor

#### Particle

A particle has _initial position_, _initial velocity_, _charge_ and _mass_ (all in standard SI units). Hence,  it is defined as follows:

``` 
P
%% position vector
%% velocity vector
%% charge
%% mass
```

!!! example
    ```
    P
    [0,0,0]
    [1,1,1]
    1.6e-19
    1.67e-27
    ```

#### Uniform fields

##### Uniform Magnetic Field (UMF)

```
UMF
%% field vector
```
!!! tip
    Ensure to account for magnitude when determining the field vector.

!!! example
    ```
    UMF
    [0,0,1]
    ```

##### Uniform Electric Field (UEF)

```
UEF
%% field vector
```
!!! tip
    Ensure to account for magnitude when determining the field vector.

!!! example
    ```
    UEF
    [0,1,0]
    ```

#### Static Point Charge (SPC)

Definition of a SPC is similar to a particle, but does not include velocity or mass.

```
SPC
%% position vector
%% charge
```

!!! example
    ```
    SPC
    [3,0,0]
    -6e-6
    ```

#### Sectioned Uniform Fields

Uniform fields can be restricted to a section in space. These are called sectioned uniform fields.   
For the moment, the spaces are computed based on the larges rectangular prism formed by the corners, but this will be updated to work for more complex 3D shapes.

##### Sectioned Uniform Magnetic Field (SUMF)

```
SUMF
%% field vector
%% 8 coordinates of the coordinates of the space
```

!!! example
    ```
    SUMF
    [0,0,10]
    [-1,-1,-1]
    [0,1,1]
    [0,0,0]
    [0,0,0]
    [0,0,0]
    [0,0,0]
    [0,0,0]
    [0,0,0]
    ```

##### Sectioned Uniform Electric Field (SUEF)

!!! info
    Coming soon!

```
SUEF
%% field vector
%% 8 coordinates of the coordinates of the space
```

!!! example
    ```
    SUMF
    [0,2,1]
    [-1,-2,-1]
    [0,1,2]
    [0,0,0]
    [0,0,0]
    [0,0,0]
    [0,0,0]
    [0,0,0]
    [0,0,0]
    ```

## Animation

### Display configurations

There exist additional animation settings available in the `scene.py` file in the `./animation` folder. Some familiarity with Manim Community may be useful.
User configuration is found under the `# Simulation configuration` and `settings` comment at the top of the `plot_particle_path` class and other scene classes. 

The start of each animation begins with an optional presentation of the objects. The code will read the config file and display the object settings two by two, although this will cause the animation to take longer.  

This can be toggled on and off by changing `output_ctxt` to `output_ctxt = True` and vice-versa. 

When uniform fields are added, field vectors can be shown (blue for magnetic and orange for electric).  
This can be toggled on and off my changing `show_vecs` and the scale of the vectors can be adjusted via `vector_scale`.  

By default, the object presentation is switched off and the vectors are displayed with 0.2 scale.

### High-quality rendering

For higher quality rendering, consult Manim Community's documentation. You can run the generic command:   

```
manim -pqh ./animation/scene.py [class_name]
```

After running `make` and updating `config.txt`, you will need to run the execuatable `./compiled_files/compiled_solver`.
Then, if you are running a Lorentz Motion simulation, run the command:

```
manim -pqh ./animation/scene.py plot_particle_path
```

For a \(\vec{B}\) Field simulation, run:

```
manim -pqh ./animation/scene.py disp_b_vec_field
```