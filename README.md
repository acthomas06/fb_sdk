#README for Facebook SDK
===================
##What is the Facebook SDK?
===================
- SDK stands for "Software Development Kit"
- Allows insertion of Facebook Plugins
    *"Like" button
    *"Share" button
    *"Comment" box
    *"Activity" feed

##Basic Setup
* Place the following code before the `<body>` tag of each page.
```
<div id="fb-root"></div>
    <script>
      window.fbAsyncInit = function() {
        FB.init({
          appId      : '{your-app-id}',
          status     : true,
          xfbml      : true
        });
      };

      (function(d, s, id){
         var js, fjs = d.getElementsByTagName(s)[0];
         if (d.getElementById(id)) {return;}
         js = d.createElement(s); js.id = id;
         js.src = "//connect.facebook.net/en_US/all.js";
         fjs.parentNode.insertBefore(js, fjs);
       }(document, 'script', 'facebook-jssdk'));
    </script>
```

##Set Up An App
* Visit the App Dashboard [here](https://developers.facebook.com/apps "App Dashboard")
* Fill in your App Display Name and a namespace (optional)

##Add a Like button
- To add a like button anywhere on your page, insert the following line of HTML:

`<div class="fb-like" data-send="true" data-width="450" data-show-faces="true"></div>`

##Add a Feed dialog

- After your FB.init() you added earlier, add the following code snippet:

```
FB.ui({
  method: 'feed',
  link: 'https://developers.facebook.com/docs/dialogs/',
  caption: 'An example caption',
  description: ('This is an example description'),
  picture: 'insert img url here'
}, function(response){});
```

##Facebook Login

- After you have initialized the FaceBook SDK, you will need to implement some authentication code within your fbAsyncInit function but after your FB.init():

```
FB.Event.subscribe('auth.authResponseChange', function(response) {
	if (response.status === 'connected') {
	  testAPI();		
	} else if (response.status === 'not_authorized') {
		FB.login();
	} else {
		FB.login();
	}
});
```	

- Now make the following alterations to the SDK loader function:

```
(function(d){
   var js, id = 'facebook-jssdk', ref = d.getElementsByTagName('script')[0];
   if (d.getElementById(id)) {return;}
   js = d.createElement('script'); js.id = id; js.async = true;
   js.src = "//connect.facebook.net/en_US/all.js";
   ref.parentNode.insertBefore(js, ref);
  }(document));
```

- This will make sure that your SDK loads asynchronously.

- Next we need to implement the testAPI() function we called earlier.  This will go directly after the SDK loader function.

```
function testAPI() {
    console.log('Welcome!  Fetching your information.... ');
    FB.api('/me', function(response) {
      console.log('Good to see you, ' + response.name + '.');
    });
}
```

- Finally, we will implement a `Login` button with one simple line of code:

`<fb:login-button show-faces="true" width="200" max-rows="1"></fb:login-button>`


