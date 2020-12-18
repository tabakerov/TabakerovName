## Lorenz System

Imagine a point in space. It has three coordinates (given that space is 3D). These coordinates can be processed with some math formula, so there are a new set of coordinates. Let's treat them as a vector and move the point in the direction the vector's pointing. Now there are a new set of coordinates. Repeat.

Lorenz System is a special kind of math formula for 3D coordinates. A point from any place in 3D space will be "attracted" to an area where this point will start moving along a closed orbit. If many points are moving along that orbit, a really beautiful and intriguing image can be created.

So, let's create such a thing using Blender 3D.

## The Equations

The equasions are pretty simple:

```
dx/dt = σ * (y - x)

dy/dt = x * (ρ - z) - y

dz/dt = x * y - β * z
```

Where σ (Sigma), ρ (Rho), and β (Beta) are constants, which equal 10, 28, and 8/3, respectively, but these constants can be altered in some range of values before the system starts to lose its fancy property of being an attractor.

## Implementation

There are some methods to implement the Lorenz System in Blender. An object can be instantiated on each step of an orbit. Or animation keys for the object's location can be added so that the object will move along the Lorenz System's trajectory.

I want to have many small objects orbiting in space, and I don't want to manage spawning objects manually; that's why I'll be using a particle system and apply Lorenz System's math to each particle at every step.

Usage of a particle system gives a couple of benefits: easy control for spawn rate and spawn position, dispose of aged particles. Also, external force fields can be applied to the particle system to add some irregularities to otherwise "mathematically perfect" movement - that will give a more natural look if an animation has to be done.

### Implementing Equations

Transforming the Lorenz System's equations to Python is trivial enough:

```
def lorenz(location):
    # Location in Blender is a 3-items tuple, and Python allows to 'deconstruct' a tuple into pieces it's constructed with using an expression like on the line below
	x, y, z = location
    
    # This value defines how small will be a step of the calculation. Smaller the value - more precise trajectory and less movement velocity
    dt = 0.01

    # Lorenz System constants Sigma, Rho and Beta
    s = 10.0
    r = 28.0
    b = 8.0/3.0
    dx = dt * (s * (y - x))
    dy = dt * (x * (r - z) -y)
    dz = dt * (x * y - b * z)

    # And returning a new position as a tuple
    return (x+dx, y+dy, z+dz)
```

A couple of coments here 