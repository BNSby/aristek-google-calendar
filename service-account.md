## Creating a service account

A service account's credentials include a generated email address that is unique, a client ID, and at least one public/private key pair.

If your application runs on Google App Engine, a service account is set up automatically when you create your project.

If your application doesn't run on Google App Engine or Google Compute Engine, you must obtain these credentials in the Google Developers Console. To generate service-account credentials, or to view the public credentials that you've already generated, do the following:

1.  Open the [**Service accounts** section](https://console.cloud.google.com/iam-admin/serviceaccounts) of the Developers Console's **IAM & Admin** page.
2.  Click **Create service account**.
3.  In the **Create service account** window, type a name for the service account and select **Furnish a new private key**. If you want to [grant G Suite domain-wide authority](https://developers.google.com/identity/protocols/OAuth2ServiceAccount#delegatingauthority) to the service account, also select **Enable G Suite Domain-wide Delegation**. Then, click **Create**.

Your new public/private key pair is generated and downloaded to your machine; it serves as the only copy of this key. You are responsible for storing it securely.

You can return to the [Developers Console](https://console.developers.google.com/) at any time to view the client ID, email address, and public key fingerprints, or to generate additional public/private key pairs. For more details about service account credentials in the Developers Console, see [Service accounts](https://developers.google.com/console/help/service-accounts) in the Developers Console help file.

Take note of the service account's email address and store the service account's private key file in a location accessible to your application. Your application needs them to make authorized API calls.

**Note:** You must store and manage private keys securely in both development and production environments. Google does not keep a copy of your private keys, only your public keys.

### Delegating domain-wide authority to the service account

If your application runs in a G Suite domain and accesses user data, the service account that you created needs to be granted access to the user data that you want to access.

The following steps must be performed by an administrator of the G Suite domain:

1.  Go to your G Suite domain’s [Admin console](http://admin.google.com).
2.  Select **Security** from the list of controls. If you don't see **Security** listed, select **More controls** from the gray bar at the bottom of the page, then select **Security** from the list of controls. If you can't see the controls, make sure you're signed in as an administrator for the domain.
3.  Select **Advanced settings** from the list of options.
4.  Select **Manage third party OAuth Client access** in the **Authentication** section.
5.  In the **Client name** field enter the service account's **Client ID**.
6.  In the **One or More API Scopes** field enter the list of scopes that your application should be granted access to. For example, if your application needs domain-wide access to the Google Drive API and the Google Calendar API, enter: https://www.googleapis.com/auth/drive, https://www.googleapis.com/auth/calendar.
7.  Click **Authorize**.

Your application now has the authority to make API calls as users in your domain (to "impersonate" users). When you prepare to make authorized API calls, you specify the user to impersonate.
