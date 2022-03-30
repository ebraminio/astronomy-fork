//[astronomy](../../../index.md)/[io.github.cosinekitty.astronomy](../index.md)/[Spherical](index.md)/[toVector](to-vector.md)

# toVector

[jvm]\
fun [toVector](to-vector.md)(time: [AstroTime](../-astro-time/index.md)): [AstroVector](../-astro-vector/index.md)

Converts spherical coordinates to Cartesian coordinates.

Given spherical coordinates and a time at which they are valid, returns a vector of Cartesian coordinates. The returned value includes the time, as required by the type #AstroVector.

## Parameters

jvm

| | |
|---|---|
| time | The time that should be included in the return value. |