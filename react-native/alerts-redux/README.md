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

## Gestures
- Scrolling, sliding, tappingg

### Best Practices
- Feedback/highlighting: Touchable, TouchableHighlight
- Cancel-ability

## PanResponder
- Can recognize simple multi-touch gestures
- Reconciles several touches into a single gesture
- Gesture state
  - stateID: persisted as long as there at least one touch on screen
  - moveX, moveY: screen coordinates of the recently-moved touch
  - x0, y0: screen coordinates
  - dx, dy: accumulated distance of the gesture since the touch started
  - vx, vy: current velocity of the gesture
- Handlers
  
  
