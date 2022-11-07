# Pi Platform Demo App: Development Environment

The following document explains how to set up a development environment and run the Pi Platform Demo App in the sandbox environment.

This outline assumes you have completed the steps in [`1_prerequisites.md`](), if you have not start there. 

## 1. Clone the Github repo and navigate to the project directory:

While in the directory or repository intended for saving your instance

```sh
git clone git@github.com:pi-apps/platform-demo-app.git

cd platform-demo-app
```
Or 
```sh
git clone https://github.com/pi-apps/demo.git

cd platform-demo-app
```


## 2. Start the frontend development server

Setup the frontend app following the [Pi Demo App Frontend documentation](../frontend/README.md).


## 3. Start the backend development server

Setup backend server following the [Pi Demo App Backend documentation](../backend/README.md).


## 4. Open the app in the Pi Sandbox

To test all of the Demo App features, you need to run it in the Pi Sandbox.

The purpose of the Sandbox is to enable running and debugging a Pi App in a desktop browser, although a Pi Appis meant to be opened in the Pi Browser by end-users.

For more information on the Sandbox head to our [Community Developer Guide](https://pi-apps.github.io/community-developer-guide/docs/gettingStarted/piAppPlatform/piAppPlatformSDK/#the-sandbox-flag).

**on your desktop browser** open the sandbox URL from Step 6 of App Checklist. Authenticate the sandbox code that is displayed in the browser within the Pi App by clicking on Pi Utilities on the sidebar menu. 

![Sandbox URL](./img/sandbox_url.png)

![Sandbox URL](./img/sandbox_firefox.png)

> **WARNING**
>
> The demo app uses express session cookies which, in the Sandbox environment, are not correctly saved on the client on some browsers.
> To properly test all of the features of the Demo App, we recommend you to open the sandbox app using Mozilla Firefox.

### Congratulations! The app is running locally in the Pi Sandbox enabling you to sign in, place an order and make a testnet payment.

### Next step is to prepare to deploy the application to a server. [Overview Here](./doc/3_pre_deployment.md)

# More Information - Developing on Pi
Have additional questions? Refer to our
[Pi Developer Guide](https://pi-apps.github.io/community-developer-guide/).
