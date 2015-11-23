# Deploy StackEdit to private server and publish to github

When install the StackEdit, it will publish to github by their account, and it can only run on localhost, how to let it run on private server, we need to add a server to get token from github.

Edit `public/res/constants.js file`
```js
constants.BASE_URL = "http://stackedit.y9i.net/";
constants.GITHUB_CLIENT_ID = 'e47fef6055344579799d';
constants.GATEKEEPER_URL = "http://tokenproxy.y9i.net/";
```

Change getToken function on `public/res/helpers/githubHelper.js` file

Change the correct url for get token from github.