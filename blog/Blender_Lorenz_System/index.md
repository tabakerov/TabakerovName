## Lorenz System

Imagine a point in space. It has three coordinates (given that space is 3D). These coordinates can be processed with some math formula, so there are a new set of coordinates. Let’s treat them as a vector and move the point in the direction the vector’s pointing. Now there are a new set of coordinates. Repeat.

Lorenz System is a special kind of math formula for 3D coordinates. A point from any place in 3D space will be “attracted” to an area where this point will start moving along a closed orbit. If many points are moving along that orbit, a really beautiful and interesting image can be created.

So, let’s create such a thing using Blender 3D.

## The Equations

The equasions are pretty simple:

```
dx/dt = σ * (y - x)

dy/dt = x * (ρ - z) - y

dz/dt = x * y - β * z
```

Where σ (Sigma), ρ (Rho), and β (Beta) are constants, which equal 10, 28, and 8/3, respectively, but these constants can be altered in some range of values before the system starts to lose its fancy property of being an attractor.

## Implementation

There are some methods to implement the Lorenz System in Blender. 