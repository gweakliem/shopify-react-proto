# React Prototype Shopify App

Based on [this tutorial](https://shopify.dev/tutorials/build-a-shopify-app-with-node-and-react)



Some notes:
1. Make sure you use the HTTPS urls from ngrok when configuring the app - I was getting these "Request origin could 
not be verified errors" which were caused by the server setting cookies flagged as Secure but the connection wasn't, 
so the browser blocks those cookies. 

1. I had to install next pinned to a specific canary revision to work around issues with 
installing dependencies 
```
npm install --save react-dom next@"v9.5.6-canary.14"
```
1. The authentication step doesn't always work as documented. Eventually I installed without 
issues, but these two articles shed some light if you run into the "Request origin could not be verified" 
error when you try to add the app to a store:
https://community.shopify.com/c/Shopify-APIs-SDKs/Is-this-tutorial-Build-a-Shopify-App-with-Node-and-React-still/m-p/789010#M51864

https://shopify.dev/tools/app-bridge/getting-started#authenticate-with-oauth
1. Using `ngrok`, the connection will time out and not let you know, if you have problems
reaching the app, restart the tunnel.

1. You may get an error 
> Oauth error invalid_request: The redirect_uri is not whitelisted

This may mean that the redirect_uri is misconfigured, but it also may mean the API keys are incorrect.

https://community.shopify.com/c/Shopify-APIs-SDKs/Bug-State-nonce-lost-when-redirected-back-to-app-during-install/td-p/679662