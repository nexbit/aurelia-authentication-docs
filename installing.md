# Installation

Head over to your terminal of choice, and navigate to your project. Now run the following command:

`jspm i aurelia-authentication`

or for webpack

`npm i aurelia-authentication`

All done. Let's move on.

## Configuring

Aurelia-authentication comes mostly pre-configured. During plugin configuration you can apply your custom setting. For configuration options and defaults see [baseConfig](baseConfig.md).

```js
import authConfig from './authConfig';

export function configure(aurelia) {
  aurelia.use
    /* Your other plugins and init code */

    /* configure aurelia-authentication from config file */
    .plugin('aurelia-authentication', baseConfig => {
        baseConfig.configure(authConfig);
    });

    /* configure aurelia-authentication with a config object */
    .plugin('aurelia-authentication', baseConfig => {
        baseConfig.configure({baseUrl: 'https://api.example.com/auth'});
    });
  });
```

Aurelia-authentication can use the endpoints of aurelia-api.

```js
export function configure(aurelia) {
  aurelia.use
    /* Your other plugins and init code */

    /* setup the api endpoints first */
    .plugin('aurelia-api', configure => {
      configure
        .registerEndpoint('auth', 'https://myapi.org/auth')
        .registerEndpoint('protected-api', 'https://myapi.org/protected-api')
        .registerEndpoint('public-api', 'http://myapi.org/public-api');
        .setDefaultEndpoint('auth');
    })

    /* configure aurelia-authentication to use above aurelia-api endpoints */
    .plugin('aurelia-authentication', baseConfig => {
        baseConfig.configure({
          endpoint: 'auth',                   // '' for the default endpoint
          configureEndpoints: ['auth', 'api'] // '' for the default endpoint
        });
    });
  });
```
