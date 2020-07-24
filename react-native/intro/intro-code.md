# Introduction
1. [React Native](#react-native)
2. [React Navigation](#react-navigation)
3. [Icons and Buttons](#icons-and-buttons)

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
### Stack Navigation
1. Create a stack navigator
- returns `Screen` and `Navigator`
  - `Navigator` should contain `Screen` as its children to define the configuration for routes
```js
const MenuNavigator = createStackNavigator()
```
2. Configure the navigator
- `NavigationContainer`: wraps all navigators structure
- `Stack.Screen name="Home"`: corresponds to the name of the route
- `initialRouteName`: the screen shows first
```js
<NavigationContainer>
  <Stack.Navigator initialRouteName="Home">
    <Stack.Screen name="Home" component={HomeScreen} />
    <Stack.Screen name="Details" component={DetailsScreen} />
  </Stack.Navigator>
</NavigationContainer>
```
3. Specifying options
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
### Safe Area
1. Import the library
```js
import { SafeAreaProvider, SafeAreaView } from 'react-native-safe-area-context';
```
2. Apply safe are insets
```js
<SafeAreaView>
  <Text>This is top text.</Text>
  <Text>This is bottom text.</Text>
</SafeAreaView>
```
3. Wrap the app in `SafeAreaProvider`: detect if the app is running on a device with notches
```js
<SafeAreaProvider> 
  <NavigationContainer>{/*(...) */}</NavigationContainer>
</SafeAreaProvider>
```
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
