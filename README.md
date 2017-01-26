![buffit logo](https://dl.dropboxusercontent.com/u/9299425/BUFFIT.png)

This app is built with [Node](http://nodejs.org) and [Express](http://expressjs.com), and comes ready to go for Heroku deployment. 

Other modules used are the [body-parser](https://github.com/expressjs/body-parser) middleware for express and [request](https://github.com/request/request) for simplified HTTP requests.

<h3>Get you an app for your Buffer</h3>
First thing you should is set up an app for your [Buffer account](http://buffer.com/developers), and take note of the credentials: 
<ul>
<li>client_id </li>
<li>client_secret (you'll receive this by email)</li>
<li>access_token </li>
</ul>

`redirect_uri` is required to set up the app, however, you won't be in need of that for the slash command.

<h3>Deploy the code to Heroku</h3>
Next step is deploying the code to Heroku. But **before you do**, check the `PROFILE_IDS` object in the code and add the profiles you would like to post to. 

```javascript
const PROFILE_IDS =
{
  'service': ['username']
};
```
A little explanation how it works:
  1. the app makes a request to the Buffer API for the list of profiles you have.
  2. the app will then search for `service`, then `username` in the packet that was received.  It'll get the corresponding `id` for use in the API request. 
  3. the `service` values are an array, so just add the usernames of any profile for that service. For example, if you have two Twitter profiles you'd like to post to, add `'twitter': [ 'handle1', 'handle2' ]` to the object.

For more info on this you can check out the [API docs](http://buffer.com/developers/api).

After you've deployed your code to Heroku, you can go to the Settings and input your Buffer credentials in the Config Vars.

Check out the [Slack API](http://api.slack.com) and the [Buffer API](http://buffer.com/developers/api) for more information.
