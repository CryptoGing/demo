# Pi Demo App

Pi Demo App is an example of how you can implement the various required flows in your app's code.
It aims to show you how to use Pi Platform API on the backend side and Pi SDK on the frontend side of your app.

It is composed of two major parts:

* **backend**: a backend app (a very simple JSON API built using Node and ExpressJS)
* **frontend**: a single-page frontend app (built using React and create-react-app)

The demo app's backend uses a local MongoDB server to store user data and session details. This needs to be set up by the developer, instructions are included. 


## 1 Prerequisites

Read [`doc/1_prerequisites.md`](./doc/2_prequisites.md) to prepare your machine for setup and to complete the needed steps for registering with Pi Network.


## 2 Development

Follow [`doc/2_development.md`](./doc/2_development.md) to start this app in development locally.

> **WARNING**
>
> The demo app uses express session cookies which, in the Sandbox environment, are not correctly saved on the client on some browsers.
> To properly test all of the features of the Demo App, you *need* to open the sandbox app using Mozilla Firefox.


## 3 Pre-Deployment

Read [`doc/3_pre_deployment.md`](./doc/3_pre_deployment.md) and complete the steps to prepare for deploying to a server. 


## 4 Deployment

Follow [`doc/4_deployment.md`](./doc/4_deployment.md) to deploy this app on a server. 


## Flows

For a detailed overview of the flows that support the demo app features, please refer to
[Pi Demo App Flows](./FLOWS.md).
