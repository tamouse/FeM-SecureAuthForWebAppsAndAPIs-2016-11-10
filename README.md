# Frontend Masters workshop Secure Authentication for Web Applications &amp; APIs with Ryan Chenkie

* Co-Instructor: Ryan Chenkie
  * [website](http://ryanchenkie.com/)
  * [twitter](https://twitter.com/ryanchenkie)
  * [github](https://github.com/chenkie)

* Co-Instructor: Lukas Ruebbelke
  * [website](http://onehungrymind.com)
  * [twitter](https://twitter.com/simpulton)
  * [github](https://twitter.com/simpulton)

## Links

* Slides: [https://frontendmasters.com/assets/resources/ryanchenkie/secure-auth.pdf](https://frontendmasters.com/assets/resources/ryanchenkie/secure-auth.pdf)

### Demo

The demo for this course consists of two main parts: a front end
application and an API.

The demo API is hosted at
https://user-authentication-api-ocokqryugz.now.sh/api but you may also
pull it down and run it locally if you like. Please note that if you
do this, you'll need to have Mongo running locally as well. As an
alternative, you can sign up for an MLab account and provide your
credentials in a `.env` file. See the readme in the API repo for
further details.

The front end demos are offered in Angular 2, Angular 1.x, and
React. Pull down the repo that you would like to work with and follow
the instructions in the readme for how to install the dependencies and
run the app. Make sure the application runs for you before starting.

* Demo API: [https://user-authentication-api-ocokqryugz.now.sh/api](https://user-authentication-api-ocokqryugz.now.sh/api)
* API: [https://github.com/chenkie/user-authentication-api](https://github.com/chenkie/user-authentication-api)
* Angular 2: [https://github.com/chenkie/angular2-user-authentication](https://github.com/chenkie/angular2-user-authentication)
* Angular 1.x: [https://github.com/chenkie/angular1-user-authentication](https://github.com/chenkie/angular1-user-authentication)
* React: [https://github.com/chenkie/react-user-authentication](https://github.com/chenkie/react-user-authentication)


## Videos

### Day 1

* [Segment 1](https://livestream.com/accounts/4894689/events/6617190/videos/141470376)

* [Segment 2](https://livestream.com/accounts/4894689/events/6617190/videos/141527296)

* [Segment 3](https://livestream.com/accounts/4894689/events/6617190/videos/141530976)

* [Segment 4](https://livestream.com/accounts/4894689/events/6617190/videos/141532145)

* [Segment 5](https://livestream.com/accounts/4894689/events/6617190/videos/141540939)

* [Segment 6](https://livestream.com/accounts/4894689/events/6617190/videos/141542893)

## Other

* [Postman](https://www.getpostman.com/) manually test and check your APIs

* [JSON Web Encryption JWE](https://tools.ietf.org/html/draft-ietf-jose-json-web-encryption-40)
* [JWT vs JWS vs JWE - What They Are and When to Use Which](https://securedb.co/community/jwt-vs-jws-vs-jwe/)

* [Where to Store JWTs - Cookies vs HTML5 Web Storage  Stormpath](https://stormpath.com/blog/where-to-store-your-jwts-cookies-vs-html5-web-storage)

* Background coding playlist: Spotify [Deep House Relax](https://open.spotify.com/user/spotify/playlist/7BixMZxL4bhgULJQ5wPbUz)


### Fixes

#### ENOENT `.env` in React demo

* **Problem:** Receiving error ` Error: ENOENT: no such file or directory, open '.env'`

* **Solution:** Create an (empty) `.env` file at the project root:

```bash
touch .env
```


#### Bug in React code

Change "login" to "signup" on this line: https://github.com/chenkie/react-user-authentication/blob/master/src/views/Main/Login/Login.js#L47 (via user Brandon B on chat)

```javascript
  onSignupSubmit(event) {
    event.preventDefault()
    const { username, email, password } = this.state
    if (username && email && password) {
      // this.props.auth.login(username, email, password) // <= OLD, INCORRECT
      this.props.auth.signup(username, email, password) // <= NEW, CORRECT
        .then(result => {
          if (!result.token) {
            this.setState({signupError: result.message})
            return
          }
          this.props.auth.finishAuthentication(result.token)
          this.context.router.push('/profile')
        })
    }
  }
```
