
![enter image description here](https://actyv-bootcamp.s3.ap-south-1.amazonaws.com/banners/jwt.jpg)



# AUTHENTICATION WITH JWT & PASSPORT

 
## Introduction

If you have visited any website then you might have expreinced that if you are logged out then you will be not able to access the profile page or profile route as you can see in following figure. 

<img src="https://dhhmzgirqh63s.cloudfront.net/21704.gif"/>


you can do it by maintaing sessions, setting session keys by just checking passwords and user name. Let us look that how server give response after login. See on the following figure. If we want to access some page then we used to login so we send our user name and password to server .server validates that and if it found correct it gives the data to browser
![enter image description here](http://robmclarty.com/system/pictures/sources/64/flow-basic_large.jpg?1450223652)
 But one of the best and safest approach now days is JWT and Passport.So basically we are going to learn how to safe our routes. So let just have a look on JWT and Passport. 

## JWT: 
JWT means **JSON WEB TOKEN**. 
Let us assume that you are going in big carnival. you can use any of the toys or swimming pools and other games if you have done the payment for that carnival. So if you have to go swiming pool and then to any movie show in that carnival then you do not pay every time . You have to just pay at counter . The counter person will give you a token or ticket and you have to just show that token to be get authenticated in each shops and you can play what you want.

If you have to access some route but it requires authentication, then after getting logged in, some key or reference or token should be given there from server , so every time we do not have to login. We can save that key and every time when we go to that protected routes to access them, the server can check that key and give the access each time. So you can save that key in local session storage or cookies or on local storage.

So basicaly that key or reference or token is JWT. Because it will be in form of JSON object.
that is why it is known as JSON Web Tokens.
So see the following figure which is showing the process .
![enter image description here](http://robmclarty.com/system/pictures/sources/69/multiserver-jwt_large.jpg?1450224622)

First user will login and then user will get a token and everytime if he has to access the file he will send his token to server and will recieve the data.
So Auth server is that counter from which you have to buy the ticket or you have to get logged in by username and paasword then you will be getting that ticket for visiting all the shops.
So here boxes in three colors are showing diffrent servers . One is that auth service which check the username and password and give you the tickets. and rest of them in red color can be any service you want to use like videos, pics, post etc.

## Structure of a JWT:
Since JWT is token which is cheked by server each time when you want to use its service so that token should contain the data to identify that it is you so he can provide your data to you only. And that token's data should have to encrypted so no one can create the duplicate token and use it for you authentication.

JWT consists of three parts 
1.  Header
2.  Payload
3.  Signature

![enter image description here](https://jwt372146972.files.wordpress.com/2019/10/image.png?w=1024&resize=493,492)

Raed the lines and then see in figure provided.

**Header**
The header typically consists of two parts: 
1:  Type of token, which is JWT, 
2: The hashing algorithm that is used to encrypt data or payload, such as HMAC SHA256 or RSA. 

So you can see in figure that json header is containing `alg` and `typ` in object  to hold algorithm name and type of token.
Default algorithm for json web token package is  **HS256**.

**Payload**
The second part of the token is the payload, which we need to encode.
An example payload is shown below:

```
{
 "name": "John Doe",
 "admin": true
}

```

**Signature**
To create the signature part, you have to take the encoded header, the encoded payload, a secret, the algorithm specified in the header, and sign that.

```
HMACSHA256(
 base64UrlEncode(header) + "." +
 base64UrlEncode(payload),
 secret
 )
```
Then you will get a jwt from server and will look like as shown below:

`eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c`

you have to save this token in local storage or session storage and this  jwt will be sent from frontend with each request to authenticate the routes.


## How to authenticate
 Now let us see how to authenticate a route. First take a look at steps involved:

1.  **Define a strategy**: For example: for login with username and password we use "local" strategy and we use "jwt" strategy for protecting the routes.
2.  **Initialize the Passport**
3.  Add passport middleware to protect the route.

We will these steps one by one☝️. 

First step is to require the Strategy. The syntax for the same is:

`const JWTStrategy = require("passport-jwt").Strategy;`

Then passport give you predefined methods to extract the JWTs from req headers. To make use of them you need to import the following:

`const ExtractJWT = require("passport-jwt").ExtractJwt;`

Then we need to import passport.js:

`const passport = require("passport");`

Then we need to define the options to use with the strategy. Example:

```
const options = {
	jwtFromRequest: ExtractJWT.fromAuthHeaderAsBearerToken(),
	secretOrKey: process.env.JWT_SECRET
};
```


Now we have to use this jwt strategy in passport. The syntax for this is:

```
passport.use(
	new JWTStrategy(options, async function(jwtPayload, done) {
		await User.findById({ _id:  jwtPayload.id })
		.then(user => {
			if (user) {
				return done(null, user);
			}
			return  done(null, jwtPayload.id);
		})
		.catch(err => done(err));
	});
);
```

Here we are asking passport to use the JWT Strategy and we provide the strategy with the options we defined above, and it will return us `jwtPayload` and `done`.

**jwtPayload** is the same data we encoded in the json web token and
**done** is the function which will call the next middleware. We will talk about it later.

Now we have to initialize the passport. Open `app.js` in the root directory.

Now first we have to require the above strategy inside app.js like below:

`require("./passport/strategy/index");`

and then we initialize using:

`app.use(passport.initialize());`

When its done we just need to protect our routes. For this please first move to the `passport/authenticate` branch and open `routes/index.js`. Let's first see the syntax for it:

```
router.get(
	"/read",
	passport.authenticate("jwt", { session: false }),
	userController.readUser
);
```

Until now we used to it like below

```
router.get("/read", userController.readUser);
```

But to authenticate it we used the passport's jwt startegy like this: `passport.authenticate("jwt", { session: false })`

Now what it will do is before actually hitting the controller method it will first validate the token and then send the request to the controller.

and if you remember we did something like this `done(null, user)`  and we said `done` is a function which calls the next middleware and in this case the next middleware is the controller and what done(null, user) will do is , it will append the user to request object. So in controller we can use the req.user to access the user sent by done method.

To see this in action move to `contoller/index` file and search for readUser method. 

```
module.exports.readUser = (req, res) => {
	res.status(HttpStatus.OK).json({ user: req.user });
};
```

if you try to hit the route `/read` then it will return "Unauthorized". To make it work we have to send a token with the request so that passport can verify and let you proceed further.

![enter image description here](https://actyv-assets.s3.ap-south-1.amazonaws.com/bootcamp/passport_6.png)

But we haven't created a token yet. You can use [jwt.io](https://jwt.io/) or we added a route "/get/jwt/token" for it in `routes/index.js`. You can call this route passing and it will return you the token.

For your learning purpose we hardcoded the value `{ id:  "5d91d0cdc6044d08ec7e2581" }`. So this method will return a token encoded with this is. Look at `generateTokens` method in `controller/index.js`

![enter image description here](https://actyv-assets.s3.ap-south-1.amazonaws.com/bootcamp/postman_5.png)

Now after getting the token let's see how to pass this in postman.

![enter image description here](https://actyv-assets.s3.ap-south-1.amazonaws.com/bootcamp/passport_7.png)

Since there will not be an actual user with id : 5d91d0cdc6044d08ec7e2581, so this return the decoded id from token.

But this will be not the case in a production env where we will have hit a route to get a token. So we are going to solve that now. The flow will be like this.

post "/login" route will be protected by "Local Strategy" and it will return us with a token. Then with each subsequent request like "/profile" we will send this token in the header and get "/profile" route is protected by "jwt" strategy which will validate the token and will let us proceed further.

So now move to `passport/login` branch.

The local strategy lies in the "passport/strategy/local/index.js" file. Open this file.

Before proceeding further lets create a user and save it to database:

![enter image description here](https://actyv-assets.s3.ap-south-1.amazonaws.com/bootcamp/passport_8.png)

First we will import the local strategy and bcrypt for password compare:

```
const LocalStrategy = require("passport-local").Strategy;
const bcrypt = require("bcryptjs");
```

Then we will have to define the options for the local strategy:

```
const options = {
	usernameField: process.env.USERNAME_FIELD,
	password: process.env.PASSWORD_FIELD
};
```

In usernameField and password we need to assign them with the properties in which username and password is coming from the request. Like for eg. from the frontend if you are sending the username through "email" object and password through "password" like 

```
{
	email: "lazy-developer@email.com",
	password: "toolazytoset"
}
```

then the passport option will be as follows: 

```
const options = {
	usernameField: "email",
	password: "password"
};
```

and then we pass these options in new LocalStrategy() as below:

```
passport.use(
	new LocalStrategy(options, async (email, password, done) => {
	await User.findOne({ email })
		.then(user => {
			if (user) {
				bcrypt.compare(password, user.password, function(err, isMatch) {
					if (err) done(err);
					if (isMatch) return done(null, user);
					return done(null, false);
				});
			}
		})
		.catch(err => done(err));
	})
);
```

here we are just finding the user by email and then comparing the password. If the password matches then we are sending the user via done method.

Now it's time to use this local strategy in the login route.

Open "routes/index.js" where you will find the below piece of code:

`router.post("/login", passport.authenticate("local"), userController.loginUser)`.

Here we are saying whenever there is a post request on login then first authenticate it with local strategy which is comparing if the password matches or not. If it maches then it will go to longinUser method inside "controller/index.js" which is as follows:

```
module.exports.loginUser = (req, res) => {
	const token = jwt.sign({ id: req.user._id }, process.env.JWT_SECRET);
	res.status(HttpStatus.OK).json({ token });
};
```

As I said previously also, done(null, user) will add a user property to request object which can later be used as req.user. So in loginUser method we are generating a token using user's id property and we are sending back to the frontend.


Let's login using wrong password:

![enter image description here](https://actyv-assets.s3.ap-south-1.amazonaws.com/bootcamp/passport_9.png)

Now let's try with correct password:

![enter image description here](https://actyv-assets.s3.ap-south-1.amazonaws.com/bootcamp/passport_10.png)

Now this will return a token and now we can use this token to authenticate the "/read" route.

![enter image description here](https://actyv-assets.s3.ap-south-1.amazonaws.com/bootcamp/passport_11.png)







