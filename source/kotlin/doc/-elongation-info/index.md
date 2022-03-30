//[astronomy](../../../index.md)/[io.github.cosinekitty.astronomy](../index.md)/[ElongationInfo](index.md)

# ElongationInfo

[jvm]\
class [ElongationInfo](index.md)(time: [AstroTime](../-astro-time/index.md), visibility: [Visibility](../-visibility/index.md), elongation: [Double](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-double/index.html), eclipticSeparation: [Double](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-double/index.html))

Contains information about the visibility of a celestial body at a given date and time.

See #Astronomy.elongation for more detailed information about the members of this class. See also #Astronomy.searchMaxElongation for how to search for maximum elongation events.

## Constructors

| | |
|---|---|
| [ElongationInfo](-elongation-info.md) | [jvm]<br>fun [ElongationInfo](-elongation-info.md)(time: [AstroTime](../-astro-time/index.md), visibility: [Visibility](../-visibility/index.md), elongation: [Double](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-double/index.html), eclipticSeparation: [Double](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-double/index.html)) |

## Properties

| Name | Summary |
|---|---|
| [eclipticSeparation](ecliptic-separation.md) | [jvm]<br>val [eclipticSeparation](ecliptic-separation.md): [Double](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-double/index.html)<br>The difference between the ecliptic longitudes of the body and the Sun, as seen from the Earth. |
| [elongation](elongation.md) | [jvm]<br>val [elongation](elongation.md): [Double](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-double/index.html)<br>The angle in degrees between the body and the Sun, as seen from the Earth. |
| [time](time.md) | [jvm]<br>val [time](time.md): [AstroTime](../-astro-time/index.md)<br>The date and time of the observation. |
| [visibility](visibility.md) | [jvm]<br>val [visibility](visibility.md): [Visibility](../-visibility/index.md)<br>Whether the body is best seen in the morning or the evening. |