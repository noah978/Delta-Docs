# Custom Skin Filter Examples

This page hopes to contains a vast set of example filters that will display the JSON code and then explain what precisely the filter is doing.

## CICategoryBlur



## CICategoryColorAdjustment



## CICategoryColorEffect

```
"name": "CIColorMonochrome",
"parameters": {
  "inputIntensity": 0.5,
  "inputColor": {
    "r": "128",
    "g": "128",
    "b": "128"
  }
}
```
Makes the colors 50% closer to the color gray.

## CICategoryCompositeOperation



## CICategoryDistortionEffect



## CICategoryGenerator



## CICategoryGeometryAdjustment

```
  "name": "CIAffineTransform",
  "parameters": {
    "inputTransform": {
      "rotation": 180
    }
  }
```
Rotates image 180 degrees.

---

```
"name": "CIAffineTransform",
"parameters": {
  "inputTransform": {
    "scaleX": -1
  }
}
```
Scales image across the x-axis negatively, which reflects it over the x-axis.

---



## CICategoryGradient

```
"name": "CISmoothLinearGradient",
"parameters": {
  "inputPoint0": {
    "x": 120,
    "y": 0
  },
  "inputPoint1": {
    "x": 120,
    "y": 53
  },
  "inputColor0": {
    "r": 255,
    "g": 255,
    "b": 255,
    "a": 0
  },
  "inputColor1": {
    "r": 0,
    "g": 0,
    "b": 0
  }
}
```
Creates a smooth linear gradient from Point0 to Point1.

## CICategoryHalftoneEffect



## CICategoryReduction



## CICategorySharpen



## CICategoryStylize

```
"name": "CICrystallize",
"parameters": {
  "inputRadius": 6,
  "inputCenter": {
    "x": "120",
    "y": "0"
  }
}
```
Creates a crystalized image similar to stained glass.

---



## CICategoryTileEffect



## CICategoryTransition

```
  "name": "CIAffineTransform",
  "parameters": {
    "inputTransform": {
      "rotation": 180
    }
  }
```
