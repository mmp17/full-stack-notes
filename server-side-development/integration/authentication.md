# Integrating  the React Client and Server
## User Authentication
1. Client POST request to /users/login
    1. Request body contains username, pwd
2. Server validates and replies with the token if successful
    2. Response body contains token
3. Client saves the token in local storage
4. Client includes the token in the header of every request
5. Setting authorization header in the fetch request

### Changes in codes
[1. Updating the CORS Whitelist](#1.-Updating-the-CORS-Whitelist)

[2. Updating the Routes](#2.-Updating-the-Routes)

[3. Update the user's login process](#3.-Update-the-user's-login-process)

[4. Add JWT token verification endpoint](#4.-Add-JWT-token-verification-endpoint)

#### 1. Updating the CORS Whitelist

In `cors.js`:
```
var whitelist = ['http://localhost:3000', 'https://localhost:3443', 'http://<Your Computer's Name>:3001']
```

#### 2. Updating the Routes

In `router.js`:

Change
```javascript
.get(cors.cors, (req, res, next) => {
	Promotions.find({})
		...
})
```
to
```javascript
.get(cors.cors, (req, res, next) => {
	Promotions.find(req.query)  // pass in query parameter
		...
})
```

#### 3. Update the user's login process

*Distinguish between the situation where a genuine error occurs during authentication as opposed to when username or password is invalid.*

In `userRouter.js`:

Change
```javascript
userRouter.post('/login', cors.corsWithOptions, passport.authenticate('local'), (req, res) => {
	...
});
```

to 
```javascript
userRouter.post('/login', cors.corsWithOptions, (req, res, next) => {
	// err: error during authentication process
	// info: contain info if user not exists
	passport.authenticate('local', (err, user, info) => {
		if (err)
			return next(err);
		// username/pwd not correct
		if (!user) {  
			res.statusCode = 401; // Unauthorized
			res.setHeader('Content-Type', 'application/json');
			res.json({
				success: false,
				status:  'Login Unsuccessful!',
				err: info
			});
		}
		// no error occurred
		req.logIn(user, (err) => {
			if (err) {
				res.statusCode = 401; // Unauthorized
				res.setHeader('Content-Type', 'application/json');
				res.json({
					success: false,
					status:  'Login Unsuccessful!',
					err: 'Could not log in user!'
				});
			}
			// generate the token if successful
			var token = authenticate.getToken({ _id: req.user._id });
			res.statusCode = 200; // Unauthorized
			res.setHeader('Content-Type', 'application/json');
			res.json({
				success: true,
				status:  'Login Successful!',
				token: token
			});
		});
	}) (req, res, next);
```

#### 4. Add JWT token verification endpoint

*Add an endpoint that verifies if the token is still valid/expired, return true/false*

In `userRouter.js`:

```javascript
userRouter.get('/checkJWTToken', cors.corsWithOptions, (req, res) => {
	passport.authenticate('jwt', { session: false }, (err, user, info) =>  {
		if (err)
			return next(err)
		if (!user) {
			res.statusCode = 401; // unauthorized
			res.setHeader('Content-Type', 'application/json');
			return res.json({ 
				status: 'JWT invalid!', 
				success: false, 
				err: info})
		}
		else {
			res.statusCode = 200;
			res.setHeader('Content-Type', 'application/json');
			res.json({ 
				status: 'JWT valid!', 
				success: true, 
				err: user });
		}
	}) (req, res);
});
```
