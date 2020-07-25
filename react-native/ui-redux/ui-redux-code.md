# [Code]React Native UI Elements and Redux
1. [Icons and Buttons](#icons-and-buttons)

## Icons and Buttons
- `raised`: add box shadow to button
- `reverse`: reverses color scheme
```js
<Icon raised
  reverse
  name={ props.favorite ? 'heart' : 'heart-o'}
  type="font-awesome"
  color='#fc9d9d'
  size={20}
  onPress={() => 
    props.favorite ? console.log('Already favorite') : props.onPress()} 
/>
```
