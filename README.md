#README for Facebook SDK
========================
##What is the Facebook SDK?
===========================
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

###Set Up An App
================
* Visit the App Dashboard [here](https://developers.facebook.com/apps "App Dashboard")

##Add a Like button
===================
- To add a like button anywhere on your page, insert the following line of HTML:

`<div class="fb-like" data-send="true" data-width="450" data-show-faces="true"></div>`

##Add a Feed dialog

- After your FB.init() you added earlier, add the following code snippet:

```
FB.ui({
  method: 'feed',
  link: 'https://developers.facebook.com/docs/dialogs/',
  caption: 'An example caption',
}, function(response){});
```


