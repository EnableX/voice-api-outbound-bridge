# Unlocking Outbound Call Capabilities: A Guide to EnableX Programmable Voice API

Initiate your outbound call solutions with EnableX Programmable Voice APIs! Our Basic Client Examples give you a firsthand experience of leveraging EnableX capabilities for initiating outbound calls, whether you're on a Mac, Linux, or Windows.

## Pre-requisite
- You will need Enablex Application credentials, APP ID and APP KEY. To find credentials, register with EnableX (https://portal.enablex.io/cpaas/trial-sign-up/).
- You will need a place for hosting this application either cloud or local machine.


## Installation
- `git clone https://github.com/EnableX/voice-api-outbound-bridge.git`
- `cd voice-api-outbound-bridge`
- `npm install`


## Setting up configurations using environment variables
- Set APP ID and APP KEY. It is required configuration.
  - `export ENABLEX_APP_ID=`
  - `export ENABLEX_APP_KEY=`

- Set port. Default port is set to 3000. It is an optional configuration.
  - `export SERVICE_PORT=`

- Make a file with name ".env" in root directory . And copy content of .env.example in .env file . Then set these variables in .env file.
- `ENABLEX_APP_ID` , `ENABLEX_APP_KEY` , `SERVICE_PORT` 

## Webhook - EnableX will send HTTP requests to your application (`/event`) after certain events occur.

For Mac and Linux, open a terminal window and type the following commands. Note - Replace all the characters after the = with values from your EnableX account:

- If you have deployed this service on a web server which is publicly accessible, set the public URL. Example - `https://{PUBLIC_URL}`
  - `export PUBLIC_WEBHOOK_URL=`
- If you want to test this service on a web server running locally on your own computer at a given port, with ngrok, you can generate URL that tunnels requests to your web server running locally. Once ngrok installed, run following -
  - `./ngrok http {SERVICE_PORT}` . It should provide you a ngrok URL something similar to `https://fc6c892d6cd7.ngrok.io`. Now, Set the ngrok URL. Example - `https://fc6c892d6cd7.ngrok.io`
    - `export PUBLIC_WEBHOOK_URL=`
- Set to run the service on http / https (false / true)
  - `export LISTEN_SSL=`

For Windows

  - In .env file update these variables `PUBLIC_WEBHOOK_URL` , `LISTEN_SSL`.
  - Their explanation is given in Linux/Mac section (Upper section).


## SSL Certificate (Self Signed or Registered). It is required configuration if LISTEN_SSL is set to true.

 For Linux/Mac:
  - Make a directory called certs on the root of the project
    - `mkdir certs`
  - Change to certs directory
    - `cd certs`
  - Create and Install certificates
    - `sudo openssl req -nodes -new -x509   -keyout example.key -out example.crt   -days 365   -subj '/CN=example.com/O=My Company Name LTD./C=US'; cat example.crt > example.ca-bundle`
  - use the certificate .key [self signed or registered]
    - `export CERTIFICATE_SSL_KEY=`
  - use the certificate .crt [self signed or registered]
    - `export CERTIFICATE_SSL_CERT=`
  - use the certificate CA[chain] [self signed or registered]
    - `export CERTIFICATE_SSL_CACERTS=`
  - switch to the root of the project
    - `cd ..`
 
For Windows (Using Git Bash):
  - Make a directory called certs on the root of the project
    - `mkdir certs`
  - Change to certs directory
    - `cd certs`
  - Create and Install certificates
    - `openssl req -nodes -new -x509   -keyout example.key -out example.crt   -days 365` 
    - `cat example.crt > example.ca-bundle`
  - Update these fields manually in .env file if not given else you can ignore it. 
    - use the certificate .key [self signed or registered]
      - `CERTIFICATE_SSL_KEY=`
    - use the certificate .crt [self signed or registered]
      - `CERTIFICATE_SSL_CERT=`
    - use the certificate CA[chain] [self signed or  registered]
      - `CERTIFICATE_SSL_CACERTS=`
  - switch to the root of the project
    - `cd ..`


## Starting the client application script
- For Outbound Calls,
  - `node client-outbound-bridge.js`
