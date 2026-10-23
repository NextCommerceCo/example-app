### Example Server to Server App

This app is intended as a demonstration of how to use the Next Commerce [App Framework](https://developers.nextcommerce.com/docs/apps) in a "server to server" context.

#### Features

* [OAuth Setup Flow](https://developers.nextcommerce.com/docs/apps/oauth)
* [Session Token Login](https://developers.nextcommerce.com/docs/apps/oauth/session-auth)
* [App Settings](https://developers.nextcommerce.com/docs/apps/settings)
* [Admin API access and scopes](https://developers.nextcommerce.com/docs/admin-api/permissions)
* [Webhooks](https://developers.nextcommerce.com/docs/webhooks) setup, data validation, and `app.uninstalled` event handling.


### How to Setup

This app uses [Django](https://docs.djangoproject.com/en/4.1/intro/install/), you can follow Django install guides to ensure you have Python in your local environment.

#### Create App In Partner Account
The first step is to create an [App](https://developers.nextcommerce.com/docs/apps) in your [Next Commerce Partner Account](https://accounts.nextcommerce.com/partners/). You'll need your app Client ID and Client Secret later on in the setup process.

#### Install Dependencies
```
pip install -r requirements.txt
```
#### Setup Public Tunnel

To access your localhost for app development, you can use [Ngrok](https://ngrok.com/) or [LocalTunnel](https://localtunnel.github.io/www/) to create and open a public tunnel to your local machine.

#### Environment Variables

| Variable | Description|
|--- | --- |
|APP_DOMAIN| Your domain when running the app (ie your public tunnel url).|
|CLIENT_ID| Your App Client ID found in your partner account. |
|CLIENT_SECRET| Your App Client Secret found in your partner account. |

To run this Django project, you'll need to set environment variables with your local app domain, app client id and client secret (from your app in your partner account).

```
export <VARIABLE>=<VALUE>
```

#### Run Django App

To run the Django app locally, use the following command.

*Django port needs to match the public tunnel port.*

```
python manage.py runserver 0.0.0.0:<PORT>
```

#### Setup App

To set up your App in the platform, you need to configure and push your app. See the [example app files](./29next-app/).

**App Files**
```
├── config.yml
├── manifest.json
└── snippets
    └── checkout-message.html
```

With your configured `manifest.json` and `config.yml`, you can now build and push your app to your account.
```
nak build && nak push
```

#### Push Your App

You can now use [App Kit](https://developers.nextcommerce.com/docs/apps/app-kit) to push your [App Manifest](https://developers.nextcommerce.com/docs/apps/manifest) to your partner account and link your development store to your app.


#### Install on Development Store
You can now connect your app to your development store which starts the OAuth setup flow and configures Admin API access. :tada:
