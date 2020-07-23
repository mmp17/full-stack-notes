# Introduction
1. [React Native](#react-native)
w. [React Navigation](#react-navigation)

## React Native
1. Installing React Native Development Tools
```shell
npm install create-react-native-app -g
```
2. Scaffolding an App
```shell
create-react-native-app <app name>
```
3. Gives access to Expo SDK

## React Navigation
### Create navigation between components
1. Create a stack navigator
```js
const MenuNavigator = createStackNavigator()
```
2. specify screens
```js
{
  Menu: { screen: Menu },
  Dishdetail: { screen: Dishdetail }
}
```
3. navigate options
```js
// common navigation options: applied to all the screens
{
  initialRouteName: 'Menu',  // menu as first screen
  navigationOptions: {
    headerStyle: {
      backgroundColor: '#512DA8'
    },
    headerTintColor:  '#fff',
    headerTitleStyle: {
      color: '#fff'
    }
  }
}
```
4. Make use of the navigator
```js
<MenuNavigator />
```
5. specify navigation options for specific component
```js
static navigationOptions = {
  title: 'Menu'  // title of the status bar
}
```
