# Watson Machine Learning Scoring Demo

## Overview

This is a simple application that shows you how to call the scoring endpoint for a deployed model in the Watson Machine Learning service.

## Installing

1. Install [Node](https://nodejs.org)
2. Clone this repo
  - *change to directory where you want to install*
  - `git clone https://github.com/ibm-watson-data-lab/watson-ml-scoring-demo`
3. Install node modules
  - `cd watson-ml-scoring-demo`
  - `npm install`

## Run Locally

1. Copy the `.env.template` file to `.env`
  - `cp .env.template .env`
  
The file should look similar to the following:

```
WML_SERVICE_PATH=https://ibm-watson-ml.mybluemix.net
WML_USERNAME=
WML_PASSWORD=
WML_INSTANCE_ID=
WML_MODEL_ID=
WML_DEPLOYMENT_ID=
```

2. Fill in username, password, and instance ID using the credentials in your IBM Watson Machine Learning service
 a. Go to the service in your IBM Cloud instance
 b. Click _Service Credentials_
 c. Expand your credentials

3. Fill in your model ID and deployment ID
 a. Go to your model under the Assets in your Data Science Platform or Watson Data Platform account
 b. Click the _Deployments_ tab
 c. Click the deployment
 d. Copy and paste the Deployment ID and Model ID values

## Run in IBM Cloud

1. Copy the `manifest.yml.template` file to `manifest.yml`
  - `cp manifest.yml.template manifest.yml`

The file should look similar to the following:

```
applications:
- path: .
  buildpack: sdk-for-nodejs
  no-route: false
  memory: 128M
  instances: 1
  domain: mybluemix.net
  name: watson-ml-scoring-demo
  host: watson-ml-scoring-demo-${random-word}
disk_quota: 256M
services:
 - IBM Watson Machine Learning
env:
  WML_MODEL_ID: xxx
  WML_DEPLOYMENT_ID: xxx
```

2. Specify the name of your Watson Machine Learning Service
  - Replace `IBM Watson Machine Learning` under *services:* with the name of the Watson Machine Learning service provisioned in your account

3. Fill in your model ID and deployment ID
 a. Go to your model under the Assets in your Data Science Platform or Watson Data Platform account
 b. Click the _Deployments_ tab
 c. Click the deployment
 d. Copy and paste the Deployment ID and Model ID values to the environment variables under *env:*

