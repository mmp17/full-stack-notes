# Alerts, Animations, Gestures, and Persist Redux Store

## Animated API
### Values in Animated
- `Animated.Value()`: single values
- `Animated.ValueXY()`: vectore
- `Interpolate()`: map input ranges to different output ranges

### Animation Types
- `Animated.decay()`: fast start and slows to a stop
- `Animated.spring()`: spring physics model
- `Animated.timing()`: animate values over time using easing functions
- Can compose animations: `parallel()`, `sequence()`, `stagger()`

### Animated Components
- Animated.Image
- Animated.ScrollView
- Animated.Text
- Animated.View

### React-native-animatable
- Animations exposed as functions on animatable elements
- Get a reference to an element
- Apply animation functions
- Takes a duration argument
- Returns a promise that is resolved when animation completes successfully or is cancelled
