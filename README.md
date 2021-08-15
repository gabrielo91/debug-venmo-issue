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

### 
# Debug using real device

## Setting the proxy

The firs thing you need to do is set up the proxy in order to allow to your mobile devices to access to the local domains running in your machine, just like `localhost.paypal.com`

1. To begin with, please follow [this steps](https://www.busbud.com/blog/debug-ios-safari-mac/) in order to enable remote debugging with Safari and your real device.
2. Download and install [charles](https://www.charlesproxy.com/), it is the proxy that will hel up us to reach sites running in our machine
3. One installed, please open it and click on the top right gear and select `Proxy Settings`, take note of the port number, this is is the `Proxy Port`.
4. Click `help` -> `Local IP Address`, this si your `Machine ip address`
5. On your mobile device (iOS) Go to Settings > Wifi > Click on the currently connected Wifi router > Note down your `Mobile IP address`.
6. on the top right gear, select `Control Access Settings` and there add the your `Mobile IP address`.

## Configure HTTP Proxy On Mobile Devices.

1. On your device go to Settings > WiFi > Click on the currently connected Wifi router > Configure Proxy > Manual  and set the Server IP (your `Machine ip address`) and the Port - `Proxy Port` > Save
2. That's all, your mobile device can now resolve the hostnames to your local machine


### Getting the value we need

1. Open Safari, select your connected device
2. Go to http://bluesuncorp.co.uk/icv4/native-local.htm#DO_NOT_CHANGE_THIS_HASH
3. wait until second render occurs (when all labels are ready) and then click venmo button, hopefully de breakpoint will be activated and we will see what information the `parsedData` variable contains

### References:

- https://www.axelerant.com/blog/how-to-test-and-debug-local-sites-on-mobile-devices-connected-to-a-network
- https://www.busbud.com/blog/debug-ios-safari-mac/
- https://www.charlesproxy.com/