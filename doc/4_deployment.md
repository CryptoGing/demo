# Pi Platform Demo app: Deployment Guide

**Warning: The purpose of this project is to be simple to run, with very few configuration steps. There is no**
**intent to make it 100% secure, infinitely scalable, or suitable for a live production app handling**
**real Pi on the mainnet. Use it at your own risk and customize it as needed to improve security and scalability.**

The production deployment uses docker-compose, and needs to run 4 containers:

* **reverse-proxy**: a simple nginx setup to reverse-proxy requests to the frontend and backend containers
* **backend**: the backend app (a very simple JSON API built using Node)
* **mongo**: the database (uses an extremely simple single-instance MongoDB setup)
* **frontend**: the SPA frontend app (built using React and create-react-app)

If you are following the Pi Developer Portal App Checklist the following steps are covered here.
- App Checklist: Complete Steps 6-9 to prepare the app for deployment
  - Step 7: Verify Domain Ownership - Add the string supplied in this step to your .env file. This is detailed in step 4 of this list.
  - Step 8: Process a transaction - Visit your app in the Pi Browser and complete a payment


## Setup notes

The following setup process was tested on Ubuntu Server 22.04.1. You may need to adapt it to your own needs
depending on your distro.

It assumes you're running as root. If that's not the case, prepend all commands with `sudo` or start
a root shell with `sudo bash`.


### 1. Set up environment variables (1/3)

From within the root file of the demo directory:

Create a .env config file to enable the deployment method to pick up your environment variables:

```shell
# Must be in the root directory (ex. MyDemoApp/demo)

# Create .env from the starter template:
cp .env.example .env

# Edit the resulting file:
vi .env
# or:
nano .env
```

Save the following environment variables.

Example variables from [`3_pre_deployment.md`]("./3_pre_deployment.md")
```DNS
A   mydemoapp.com           123.123.123.123
A   backend.mydemoapp.com   123.123.123.123
```

Input and save in the below format: 

```
FRONTEND_URL=https://mydemoapp.com
FRONTEND_DOMAIN_NAME=mydemoapp.com
BACKEND_URL=https://backend.mydemoapp.com
BACKEND_DOMAIN_NAME=backend.mydemoapp.com
```


### 2. Create and Save initial environment variables (2 of 3)

Obtain the following values from the developer portal:

**Domain Verification Key**: Go to the developer portal, and on your list of registered apps click on the app you are verifying.  Next click on the "App Checklist" and click on step 7. From this page you can obtain the string that needs to be added to your `.env` file.

<img title="Dev Portal Verify URL"  src="./img/domain_verification.png" style="width:400px;height:550px;" />

**API key**: obtained by tapping the "API Key" button on the App Dashboard.
> If using a previously registered app that was started in development. Use the API key that was > saved to your .env file of the backend development setup.
> Creating a new key will invalidate the previous key.

<img title="Dev Portal API"  src="./img/api_key.png" style="width:300px;height:250px;" />

Then, copy-paste those values in the following two keys of your .env file:

```
# Add your Domain Validation Key here:
DOMAIN_VALIDATION_KEY=

# Add your API key here:
PI_API_KEY=
```


### 3. Set up MongoDB environment variables (3 of 3)

Configure the following environment variables:

```
# Generate a secure password for your MongoDB database and paste it here:
MONGODB_PASSWORD=

# Generate a random string (e.g 64 alphanumeric characters) and paste it here:
SESSION_SECRET=
```


### 4. Run the docker containers:

**Make sure you are in the `platform-demo-app` directory before running any `docker-compose` command!**

```
docker-compose build
docker-compose up -d
```

You can check which containers are running using either one of the following two commands:

```
docker ps
docker-compose ps
```


You can print out logs of the Docker containers using the following command:

```
docker-compose logs -f <service-name>

# e.g:
docker-compose logs -f reverse-proxy
```


### 5. Verify Domain Ownership

Go to the developer portal, and on your list of registered apps click on the app you are verifying. While the app is deployed, click on the "Verify Domain" button.
This should verify your frontend domain and mark it as verified (green check mark on the developer portal).

![](./img/domain_verified.png)


### 6. Access application within Pi Browser, Process a Payment:

Open your frontend app's URL in the developer portal and make sure everything works by signing it and placing
an order, then proceeding with the payment (you will need a testnet wallet in order to complete this step).
