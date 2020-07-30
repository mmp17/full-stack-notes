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
```js
import { Animated, Easing } from 'react-native';
Animated.timing(
  this.animatedValue, 
  {
    toValue: 8,
    duration: 8000,
    easing: Easing.linear
  }
).start();
```

- Can compose animations: `parallel()`, `sequence()`, `stagger()`

### Animated Components
- Animated.Image
- Animated.ScrollView
- Animated.Text
- Animated.View
```js
import * as Animatable from 'react-native-animatable';

<Animatable.View animation="fadeInDown" duration={2000} delay={1000}>
```

### React-native-animatable
- Animations exposed as functions on animatable elements
- Get a reference to an element
- Apply animation functions
- Takes a duration argument
- Returns a promise that is resolved when animation completes successfully or is cancelled
