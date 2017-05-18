# OAuth
Introduction to how OAuth works.

## Introduction
So why is OAuth important?
It lets you authenticate with someone else's service. For example, you can have a user authenticate with Facebook or Google.

You can use this authentication to access the Facebook or Google API, or just to let them log in to your site using a different service (i.e. logging in with Google or Facebook)

This adds a layer of security, and anybody who's anybody uses OAuth now for authentication, because it's pretty swag.

## How it works

I'll do a quick example with Ion, which allow for authentication using OAuth. You can then use this to make requests to the Ion API.

Here's what goes down:

Quick flow -
1. Your user visits your site
2. You need the user to give permission for you to access the Ion API
3. The click "Log in with Ion" or whatever.
4. They get redirected to a site generated and hosted on Ion specifically for logging in users for your app.
5. They log in.
6. Ion then redirects back to your site, with some extra information that you can use to make API requests

What you have to do -
1. You have to set up your application with Ion
    * [https://ion.tjhsst.edu/oauth](https://ion.tjhsst.edu/oauth)
2. You'll get a Client ID and a Client Secret. The Client Secret should be (guess what) Secret.

What TJ Ion does - 
1. It keeps track of which apps are registered for a user, and what permissions each app has.
2. It keeps track of the redirect URLs for each app.

A deeper look at list #1 -
1. Your user visits your site
    * Sure, that's pretty straightforward
2. You need the user to give permission for you to access the Ion API
    * You provide them with a "log in with Ion" button or something
3. The click "Log in with Ion" or whatever.
    * You send a request to the OAuth server
    * https://ion.tjhsst.edu/oauth/auth?response_type=code&client_id=CLIENT_ID&redirect_uri=REDIRECT_URI&scope=photos&state=1234zyx
4. They get redirected to a site generated and hosted on Ion specifically for logging in users for your app.
    * You are no longer in control of this.
5. They log in.
    * The smart part is that you never have their password. They log into Ion on Ion servers.
6. Ion then redirects back to your site, with some extra information that you can use to make API requests
    * The client gets an authorization **code**
    * To make requests, they send this code to your servers.
    * Your servers exchange this for an access token.
    * They then use this access token to access API services and stuff.
    
## Additional Reading

These are some really great resources and you should read these.

A better explanation of how OAuth works
- https://aaronparecki.com/oauth-2-simplified/

A better explanation of the different types of grants
- https://alexbilbie.com/guide-to-oauth-2-grants/
