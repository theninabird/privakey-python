# PrivaKeySDK

[![license:mit](https://img.shields.io/badge/license-mit-blue.svg)](https://opensource.org/licenses/MIT)

## Overview

This Python example is intended to aid developers in implementing Privakey Authentication Services in their service.

No warranties, explicit nor implied, are provided.  This and other provided libraries are provided as sample implementations only.

For more information visit [www.privakey.com](https://www.privakey.com) or contact support@privakey.com.

## Packages

* python 2.7+ python-pip python-dev build-essential libssl-dev libsasl2-dev
* oic 0.7.6+
* pyjwkest 1.0.1+
* cherrypy 3.2.4+
* pyaml 15.03.1+
* cffi 1.4.1+

## Setup

1. Download the Privakey app from the [Apple Store](https://itunes.apple.com/us/app/privakey/id968897948?mt=8) or [Google Play](https://play.google.com/store/apps/details?id=com.probaris.mid).
2. Sign up through the Privakey app.
3. Log in to the [Privakey Admin Portal](https://idp.privakey.com/IdentityServer) and sign up as a new company.
4. In the Admin Portal, also create a Relying Party. The redirect URI for this sample is "https://localhost:80/code_flow".
5. Open the settings.yaml.example and set your client id and client secret.
6. Install the required dependencies:

`pip install -r requirements.txt`

## Run

Run the sample with the following command:

`sudo python rp.py settings.yaml.example`

This will start a local server at https://localhost:80.

Enter your Privakey login to start the process.

## Advanced Setup

By default, this sample uses 'Code Flow'. If you want to switch it to 'Implicit Flow', do the following:

1. Log in to the [Privakey Admin Portal](https://idp.privakey.com/IdentityServer).
2. Add a new redirect URI to your existing Relying Party: "https://localhost:80/implicit_flow"
3. In src/settings.yaml.example, swap the commented/uncomment lines as follows:

```yaml
  redirect_uris:
    #- "{base}/code_flow"    
    - "{base}/implicit_flow"
    
  response_types:
    #- code    
    - [id_token, token]
```