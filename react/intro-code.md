# Introduction to React
1. [Reactstrap Configuration](#reactstrap-configuration)
2. [React Component](#reactstrap-component)

## Reactstrap Configuration
1. Install `reactstrap`
```shell
yarn add bootstrap@4.0.0
yarn add reactstrap@5.0.0
yarn add react-popper@0.9.2
```
2. Use Bootstrap4
Add following codes to `index.js`:
```javascript
import 'bootstrap/dist/css/bootstrap.min.css';
```
3. Adding a Navigation Bar
Add following codes to `App.js`:
```javascript
import { Navbar, NavbarBrand } from 'reactstrap';

class App extends Component {
  render() {
    return (
      <div className="App">
        <Navbar dark color="primary">
          <div className="container">
            <NavbarBrand href="/">Ristorante Con Fusion</NavbarBrand>
          </div>
        </Navbar>
      </div>
    );
  }
}
```
