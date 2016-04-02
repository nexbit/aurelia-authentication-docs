# Endpoints

Aurelia-authentication allows you to work with multiple endpoints. This is useful, because not every API uses the same authentication methods.

## Configuring
aurelia-authentication uses [aurelia-api](https://github.com/SpoonX/aurelia-api), which has support for [multiple endpoints](https://github.com/SpoonX/aurelia-api/blob/master/doc/getting-started.md#multiple-endpoints).
By default, aurelia-authentication uses the HttpClient from [aurelia-fetch-client](https://github.com/aurelia/fetch-client) when no specific endpoint has been configured, and if no [default endpoint](https://github.com/SpoonX/aurelia-api/blob/master/doc/getting-started.md#default-endpoint) was configured.
So, if you want aurelia-authentication to use your **default** endpoint, you only have to configure aurelia-api.
If you wish to use a **specific** endpoint to have aurelia-authentication talk to, you have to set the `endpoint` config option to a string, being the endpoint name.

### Authorization header
If you require more flexibility, and want to send the authorization header along to multiple endpoints, you can simply use the `configureEndpoints` config option.
Set this to an array of endpoint names to configure, and aurelia-authentication will do the rest, and make sure that all requests to these endpoints (when authenticated) get enriched with the authorization header.

### Configure the Fetch Client
If you don't want to use aurelia-api, you have to configure the aurelia-fetch-client. In your aurelia app file, inject the {FetchConfig} class from aurelia-authentication. We need to explicitly opt-in for the configuration of your fetch client by calling the configure function of the FetchConfig class:
```
import 'bootstrap';

import {inject} from 'aurelia-framework';
import {Router} from 'aurelia-router';
import {FetchConfig} from 'spoonx/aurelia-authentication';
@inject(Router,FetchConfig, AppRouterConfig )
export class App {

  constructor(router, fetchConfig, appRouterConfig){
    this.router = router;
    this.fetchConfig = fetchConfig;
  }
  
  activate(){
    this.fetchConfig.configure();
  }
}
```
