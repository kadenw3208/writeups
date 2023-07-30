# Secrets
Category: Web Exploitation
Points: 200
## Problem Description
We have several pages hidden. Can you find the one with the flag?The website is running  [here](http://saturn.picoctf.net:65352/).
## Writeup
When we first go to the website and go to inspect element, we see a page called folders, so let's navigate there.
```html
<!DOCTYPE html>
<html>
  <head>
    <title></title>
    <link rel="stylesheet" href="hidden/file.css" />
  </head>

  <body>
    <h1>Finally. You almost found me. you are doing well</h1>
    <img src="https://media1.tenor.com/images/0a6aff9f825af62c05adfbd75039cc7b/tenor.gif?itemid=4648337" alt="Something Like That GIF - Andy Parksandrecreation Wtf GIFs" style="max-width: 833px; background-color: rgb(151, 121, 85);" width="833" height="937.125">
  </body>
</html>
```
When we go to look in the folder again, we can see another folder called "hidden". So we navigate there again:
```html
<!DOCTYPE html>
<html>
  <head>
    <title>LOGIN</title>
    <!-- css -->
    <link href="superhidden/login.css" rel="stylesheet" />
  </head>
  <body>
    <form>
      <div class="container">
        <form method="" action="/secret/assets/popup.js">
          <div class="row">
            <h2 style="text-align: center">
              Login with Social Media or Manually
            </h2>
            <div class="vl">
              <span class="vl-innertext">or</span>
            </div>

            <div class="col">
              <a href="#" class="fb btn">
                <i class="fa fa-facebook fa-fw"></i> Login with Facebook
              </a>
              <a href="#" class="twitter btn">
                <i class="fa fa-twitter fa-fw"></i> Login with Twitter
              </a>
              <a href="#" class="google btn">
                <i class="fa fa-google fa-fw"></i> Login with Google+
              </a>
            </div>

            <div class="col">
              <div class="hide-md-lg">
                <p>Or sign in manually:</p>
              </div>

              <input
                type="text"
                name="username"
                placeholder="Username"
                required
              />
              <input
                type="password"
                name="password"
                placeholder="Password"
                required
              />
              <input type="hidden" name="db" value="superhidden/xdfgwd.html" />

              <input
                type="submit"
                value="Login"
                onclick="alert('Thank you for the attempt but oops! try harder. better luck next time')"
              />
            </div>
          </div>
        </form>
      </div>

      <div class="bottom-container">
        <div class="row">
          <div class="col">
            <a href="#" style="color: white" class="btn">Sign up</a>
          </div>
          <div class="col">
            <a href="#" style="color: white" class="btn">Forgot password?</a>
          </div>
        </div>
      </div>
    </form>
  </body>
</html>
```
We do the same thing and find a folder called superhidden.
```html
<!DOCTYPE html>
<html>
  <head>
    <title></title>
    <link rel="stylesheet" href="mycss.css" />
  </head>

  <body>
    <h1>Finally. You found me. But can you see me</h1>
    <h3 class="flag">picoCTF{succ3ss_@h3n1c@10n_790d2615}</h3>
  </body>
</html>
```
We can see our flag now!
<br>`picoCTF{succ3ss_@h3n1c@10n_790d2615}`
