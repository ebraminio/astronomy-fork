# Astronomy Engine (Python)

This is the complete programming reference for the Python version of
Astronomy Engine. Supports Python 3. Does NOT support Python 2.
See the [home page](https://github.com/cosinekitty/astronomy) for more info.

---

## Quick Start
To get started quickly, here are some [examples](../../demo/python/).

---

## Contents

- [Topic Index](#topics)
- [Classes](#classes)
- [Enumerated Types](#enumerations)
- [Error Types](#errors)
- [Functions](#functions)

---

<a name="topics"></a>
## Topic Index

### Position of Sun, Moon, and planets

| Function | Description |
| -------- | ----------- |
| [HelioVector](#HelioVector) | Calculates vector with respect to the center of the Sun. |
| [GeoVector](#GeoVector)     | Calculates vector with respect to the center of the Earth. |
| [Equator](#Equator)         | Calculates right ascension and declination. |
| [Ecliptic](#Ecliptic)       | Converts J2000 equatorial coordinates to J2000 ecliptic coordinates. |
| [EclipticLongitude](#EclipticLongitude) | Calculates ecliptic longitude of a body in the J2000 system. |
| [Horizon](#Horizon)         | Calculates horizontal coordinates (azimuth, altitude) for a given observer on the Earth. |
| [LongitudeFromSun](#LongitudeFromSun) | Calculates a body's apparent ecliptic longitude difference from the Sun, as seen by an observer on the Earth. |

### Rise, set, and culmination times

| Function | Description |
| -------- | ----------- |
| [SearchRiseSet](#SearchRiseSet) | Finds time of rise or set for a body as seen by an observer on the Earth. |
| [SearchHourAngle](#SearchHourAngle) | Finds when body reaches a given hour angle for an observer on the Earth. Hour angle = 0 finds culmination, the highest point in the sky. |

### Moon phases

| Function | Description |
| -------- | ----------- |
| [MoonPhase](#MoonPhase) | Determines the Moon's phase expressed as an ecliptic longitude. |
| [SearchMoonPhase](#SearchMoonPhase) | Finds the next instance of the Moon reaching a specific ecliptic longitude separation from the Sun. |
| [SearchMoonQuarter](#SearchMoonQuarter) | Finds the first quarter moon phase after a given date and time. |
| [NextMoonQuarter](#NextMoonQuarter) | Finds the next quarter moon phase after a previous one that has been found. |

### Lunar perigee and apogee

| Function | Description |
| -------- | ----------- |
| [SearchLunarApsis](#SearchLunarApsis) | Finds the next perigee or apogee of the Moon after a specified date. |
| [NextLunarApsis](#NextLunarApsis) | Given an already-found apsis, finds the next perigee or apogee of the Moon. |

### Visual magnitude and elongation

| Function | Description |
| -------- | ----------- |
| [Illumination](#Illumination) | Calculates visual magnitude and phase angle of bodies as seen from the Earth. |
| [SearchPeakMagnitude](#SearchPeakMagnitude) | Searches for the date and time Venus will next appear brightest as seen from the Earth. |
| [AngleFromSun](#AngleFromSun) | Returns full angle seen from Earth between body and Sun. |
| [Elongation](#Elongation) | Calculates ecliptic longitude angle between a body and the Sun, as seen from the Earth. |
| [SearchMaxElongation](#SearchMaxElongation) | Searches for the next maximum elongation event for Mercury or Venus that occurs after the given date. |

### Oppositions and conjunctions

| Function | Description |
| -------- | ----------- |
| [SearchRelativeLongitude](#SearchRelativeLongitude) | Finds oppositions and conjunctions of planets. |

### Equinoxes, solstices, and apparent solar motion

| Function | Description |
| -------- | ----------- |
| [SearchSunLongitude](#SearchSunLongitude) | Finds the next time the Sun reaches a specified apparent ecliptic longitude in the *true equator of date* system. |
| [Seasons](#Seasons) | Finds the equinoxes and solstices for a given calendar year. |
| [SunPosition](#SunPosition) | Calculates the Sun's apparent ecliptic coordinates as seen from the Earth. |

### Coordinate transforms

The following four orientation systems are supported.
Astronomy Engine can convert a vector from any of these orientations to any of the others.
It also allows converting from a vector to spherical (angular) coordinates and back,
within a given orientation. Note the 3-letter codes for each of the orientation systems;
these are used in function and type names.

- **EQJ = Equatorial J2000**: Uses the Earth's equator on January 1, 2000, at noon UTC.
- **EQD = Equator of-date**: Uses the Earth's equator on a given date and time, adjusted for precession and nutation.
- **ECL = Ecliptic**: Uses the mean plane of the Earth's orbit around the Sun. The x-axis is referenced against the J2000 equinox.
- **HOR = Horizontal**: Uses the viewpoint of an observer at a specific location on the Earth at a given date and time.

| Function | Description |
| -------- | ----------- |
| [RotateVector](#RotateVector) | Applies a rotation matrix to a vector, yielding a vector in another orientation system. |
| [InverseRotation](#InverseRotation) | Given a rotation matrix, finds the inverse rotation matrix that does the opposite transformation. |
| [CombineRotation](#CombineRotation) | Given two rotation matrices, returns a rotation matrix that combines them into a net transformation. |
| [VectorFromSphere](#VectorFromSphere) | Converts spherical coordinates to Cartesian coordinates. |
| [SphereFromVector](#SphereFromVector) | Converts Cartesian coordinates to spherical coordinates. |
| [VectorFromEquator](#VectorFromEquator) | Given angular equatorial coordinates, calculates equatorial vector. |
| [EquatorFromVector](#EquatorFromVector) | Given an equatorial vector, calculates equatorial angular coordinates. |
| [VectorFromHorizon](#VectorFromHorizon) | Given apparent angular horizontal coordinates, calculates horizontal vector. |
| [HorizonFromVector](#HorizonFromVector) | Given a vector in horizontal orientation, calculates horizontal angular coordinates. |
| [Rotation_EQD_EQJ](#Rotation_EQD_EQJ) | Calculates a rotation matrix from equatorial of-date (EQD) to equatorial J2000 (EQJ). |
| [Rotation_EQD_ECL](#Rotation_EQD_ECL) | Calculates a rotation matrix from equatorial of-date (EQD) to ecliptic J2000 (ECL). |
| [Rotation_EQD_HOR](#Rotation_EQD_HOR) | Calculates a rotation matrix from equatorial of-date (EQD) to horizontal (HOR). |
| [Rotation_EQJ_EQD](#Rotation_EQJ_EQD) | Calculates a rotation matrix from equatorial J2000 (EQJ) to equatorial of-date (EQD). |
| [Rotation_EQJ_ECL](#Rotation_EQJ_ECL) | Calculates a rotation matrix from equatorial J2000 (EQJ) to ecliptic J2000 (ECL). |
| [Rotation_EQJ_HOR](#Rotation_EQJ_HOR) | Calculates a rotation matrix from equatorial J2000 (EQJ) to horizontal (HOR). |
| [Rotation_ECL_EQD](#Rotation_ECL_EQD) | Calculates a rotation matrix from ecliptic J2000 (ECL) to equatorial of-date (EQD). |
| [Rotation_ECL_EQJ](#Rotation_ECL_EQJ) | Calculates a rotation matrix from ecliptic J2000 (ECL) to equatorial J2000 (EQJ). |
| [Rotation_ECL_HOR](#Rotation_ECL_HOR) | Calculates a rotation matrix from ecliptic J2000 (ECL) to horizontal (HOR). |
| [Rotation_HOR_EQD](#Rotation_HOR_EQD) | Calculates a rotation matrix from horizontal (HOR) to equatorial of-date (EQD). |
| [Rotation_HOR_EQJ](#Rotation_HOR_EQJ) | Calculates a rotation matrix from horizontal (HOR) to J2000 equatorial (EQJ). |
| [Rotation_HOR_ECL](#Rotation_HOR_ECL) | Calculates a rotation matrix from horizontal (HOR) to ecliptic J2000 (ECL). |

---
