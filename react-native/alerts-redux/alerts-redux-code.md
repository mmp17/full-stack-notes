# [CODE]Alerts, Animations, Gestures, and Persist Redux Store

## Swipe Options Buttons and Alerts
1. Install the package
```shell
yarn add react-native-swipeout
```
2. Import the package
```js
import Swipeout from 'react-native-swipeout';
```
3. Set up swipe buttons
```js
const rightButton = [
  {
    text: 'Delete',
    type: 'delete',
    onPress: () => this.props.deleteFavorite(item.id)
  }
];
```
4. Surround list items with `<Swipeout>`
```js
<Swipeout right={rightButton} autoClose={true}>
  <ListItem ... />
</Swipeout>
```
