## Lorenz System

Imagine a point in a space. It has 3 coordinates (given the space is 3D). This coordinates can be processed with some math formula so there are a new set of coordinates. Let’s treat them as a vector and move the point in direction the vector’s pointing. Now there are new set of coordinates. Repeat.

Lorenz System is a special kind of math formula for 3D coordinates. A point from any place in 3D space will be “attracted” to an area where this point will start moving along closed orbit. If there are a lot of points moving along that orbit a really beautiful and interesting image can be created.

So, let’s create such thing using Blender 3D.

## The Equasions

The equasions are pretty simple:

```
dx/dt = σ * (y - x)

dy/dt = x * (ρ - z) - y

dz/dt = x * y - β * z
```

where σ (Sigma), ρ (Rho) and β (Beta) are constants equal 10, 28 and 8/3 respectively. But this constants can be altered in some range of values before the system starts to lose its fancy property of being attractor.

## Implementation

There are some methods to implement the Lorenz System in Blender. 