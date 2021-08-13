## Setup local projects

1. Pull the last version of [paypal-smart-payment-buttons](https://github.com/paypal/paypal-smart-payment-buttons), go to [this file](https://github.com/paypal/paypal-smart-payment-buttons/blob/master/src/api/socket.js#L211) and add `debugger;`  on line 210
2. run ` npm i`  and `npm webpack`
3. pull [clientsdknodeweb](https://github.paypal.com/Checkout-R/clientsdknodeweb)  and modify the proxy/smart  section, change the value like this:

  ```json
  "/smart": "http://localhost.paypal.com:8001",
  ```

4. pull [smartcomponentnodeweb](https://github.paypal.com/Checkout-R/smartcomponentnodeweb) and modify the `package.json` adding an alias section pointing to the path were `paypal-smart-payment-buttons` is located . You can run `pwd` in the console in `paypal-smart-payment-buttons` folder and copy that value, the result should look like this:
  ```json
  "alias": {
      "@paypal/smart-payment-buttons": "/Users/gaortega/workspace/paypal-smart-payment-buttons"
    }
  ```
6. Launch `smartcomponentnodeweb` by running 
  ```bash
  PORT=8001 npm run start
  ``` 
7. Launch `clientsdknodeweb`  by running:

```bash
  npm run start
```
## Debug using real device

1. Please follow [this steps](https://www.busbud.com/blog/debug-ios-safari-mac/) in order to enable remote debugging with Safari and your real device.
2. Not sure if it resolves the `localhost.paypal` domains, if so, please continue, otherwise, I need to write a guide in order to do that through a proxy.
3. Go to http://bluesuncorp.co.uk/icv4/native-local.htm#DO_NOT_CHANGE_THIS_HASH
4. wait until second render occurs (when all labels are ready) and then click venmo button, hopefully de breakpoint will be activated and we will see what information the `parsedData` variable contains