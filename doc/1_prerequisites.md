# Prerequisites:
## Pi Network
- A Pi Account
  - Required to create the credentials needed for the app to communicate with Pi Network servers
  - Pi App is available for [Android](https://play.google.com/store/apps/details?id=com.blockchainvault) and [iOS](https://itunes.apple.com/us/app/pi-network/id1445472541).

- Download Pi Browser
  - Pi Browser is available for [Android](https://play.google.com/store/apps/details?id=pi.browser) and [iOS](https://apps.apple.com/us/app/pi-browser/id1560911608).


## Packages and Libraries
- NodeJS installation (recommended version: Node v16 LTS **or lower**)
  - if you're running with node 17 or higher, you'll need to use `yarn startNode17` to work around [this issue](https://github.com/facebook/create-react-app/issues/11562)

- `yarn` installation (npm is not supported for the demo app front end)
  - most NodeJS packages will include yarn but it may be required to install separately

- Functional [Docker Engine](https://docs.docker.com/engine/) or [Mongosh](https://www.mongodb.com/docs/mongodb-shell/) installation

## Programming Tools (Basic Understanding)
- Writing and using [Environment files (.env or dotenv)](https://malware.expert/general/what-is-env-files/)
- Editing text files using [Nano](https://linuxize.com/post/how-to-use-nano-text-editor/) or [Vi](https://docs.rockylinux.org/books/admin_guide/05-vi/) 

##  Register App within the Developer Portal
Open `develop.pi` in the Pi Browser, on your mobile phone, and go through the prerequisite steps
(e.g verifying your email address).

Create a new app by clicking the "Register an App" button.

The Process is as follows:

1. Register an App:
  - Name: The name of your app
  - Description: A public user-facing description of your app
  - Network: select "Pi Testnet"
  - Submit the form

<img title="Register An App" alt="Registration Form for an App" src="./img/register_app.PNG" style="width:300px;height:600px;" />

<br/>

This will bring you to the App Dashboard, from this screen you can continue the development of the demo app.

**Complete steps 1 through 5 before moving to the development outline**
 
- App Checklist: Complete Steps 1-5 to prepare the app for launch in development mode
  - Step 1: "Register an App" was completed previously
  - Step 2: Configure App Hosting - Hosting type: select "Self hosted"
  - Step 3: Create a Pi Wallet, see this [Pi Wallet Introduction](https://pi-apps.github.io/community-developer-guide/docs/importantTopics/paymentFlow/piWallet/) for more information
  - Step 4: Review this documentation and our [Community Developer Guide](https://pi-apps.github.io/community-developer-guide/) for help getting setup
  - Step 5: Configure App Development URL: the URL on which your app is running on your development environment. If your using the default
    setup for the demo app frontend, this is "http://localhost:3314. **Note:** If you need, you can change the port by specifying it in
    `frontend/.env` file, as the value of the `PORT` environment variable.
 
 <img title="Developer Portal App Checklist" alt="App Checklist" src="./img/app_checklist.png" style="width:300px;height:1100px;" />
 
 <br/>
 
- App Configuration: Additional information that can be adjusted
  - Whitelisted usernames: you can leave this blank at this point
  - App URL: This is irrelevant for development. You can use the intended production URL of your app (e.g "https://mydemoapp.com"),
    or simply set it up to an example value (e.g "https://example.com"). This must be an HTTPs URL
  - Development URL: The URL on which your app is running on your development environment. If your using the default
    setup for the demo

#### Move to [2_Development](./doc/development.md) to set up the demo app locally
