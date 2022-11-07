# Pre-Deployment
These steps are intended to get you prepared to deploy the app to a server. 

## Setup notes

The following setup process was tested on Ubuntu Server 22.04.1. You may need to adapt it to your own needs
depending on your distro (specifically, the "Install Docker" step).

It assumes you're running as root. If that's not the case, prepend all commands with `sudo` or start
a root shell with `sudo bash`.


### 1. Install Docker and docker-compose:

Run the following command in order to get the latest docker version and the latest docker-compose version
(required because of [this issue](https://github.com/datahub-project/datahub/issues/2020#issuecomment-736850314))

```shell
apt-get update && \
apt-get install -y zip apt-transport-https ca-certificates curl gnupg-agent software-properties-common && \
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | apt-key add - && \
add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" && \
apt-get update && \
apt-get install -y docker-ce docker-ce-cli containerd.io && \
curl -L "https://github.com/docker/compose/releases/download/1.27.4/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose && \
chmod +x /usr/local/bin/docker-compose
```


## 2. Get a server and set up your DNS

Obtain a domain name and set up 2 DNS records pointing to your server. One will be used for the frontend app, and one will be used for the backend app.

Here is an example, assuming your domain name is mydemoapp.com and your server IP is 123.123.123.123.

**Note:** The domain must support ‘https://’ which is required by the Pi Developer Portal. 

```DNS
A   mydemoapp.com           123.123.123.123
A   backend.mydemoapp.com   123.123.123.123
```

## 2. Pi Developer Portal Setup
### Option 1: Update Development app within the Developer Portal
> If you previously registered an app within the Pi Developer Portal and started the Demo app 
> locally, you can update that app registration to deploy the demo app to a server.

From Pi Browser, navigate to develop.pi and click on the previously registered app
Click on the App Checklist and complete the below step.

  - Step 6: Deploy the App to the Production Environment - Add the Production URL


### Option 2: Register your app on the Developer Portal
> If you did not previously start the demo app locally you will need to complete these steps.

Open `develop.pi` in the Pi Browser, on your mobile phone, and go through the prerequisite steps
(e.g verifying your email address).

Register an App:
  - Name: The name of your app
  - Description: A public user-facing description of your app

<img title="Register An App" alt="Registration Form for an App" src="./img/register_app.PNG" style="width:300px;height:600px;" />

<br />

This will bring you to the App Dashboard, from this screen you can continue the setup of the demo app for deployment.

- App Checklist: Complete Steps 6-9 to prepare the app for deployment
  - Step 6: Deploy the App to the Production Environment - Add the Production URL
  - Step 7: Verify Domain Ownership - Add the string supplied in this step to your .env file. This is detailed in step 4 of this list.
  - Step 8: Process a transaction - Visit your app in the Pi Browser and complete a payment

 <img title="Developer Portal App Checklist" alt="App Checklist" src="./img/app_checklist.png" style="width:300px;height:1100px;" />
<br/>

- App Configuration: Additional information that can be adjusted but is not necessary 
  - Whitelisted usernames: you can leave this blank at this point
  - Hosting type: select "Self hosted"
  - App URL: Enter the intended production URL of your app (e.g "https://mydemoapp.com"),
  or simply set it up to an example value (e.g "https://example.com"). This must be an HTTPs URL.
  - Development URL: This is irrelevant for deployment.
