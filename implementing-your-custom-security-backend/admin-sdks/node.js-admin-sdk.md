# Node.js

The Node Admin SDK can be found on [GitHub](https://github.com/deviceinsight/ux4iot-admin-node).

First, add the dependency:

{% tabs %}
{% tab title="NPM" %}
```bash
npm install ux4iot-admin-node
```
{% endtab %}

{% tab title="Yarn" %}
```bash
yarn add ux4iot-admin-node
```
{% endtab %}
{% endtabs %}

Initialize the SDK using the connection string. You can retrieve the connection string from the Azure portal.

```javascript
const Ux4iotAdmin = require('ux4iot-admin');
const sdk = new Ux4iotAdmin({
    connectionString: "HostName=...;Key=secret";
});
```

Now you can whitelist grant requests using:

```javascript
sdk.grant(grantRequest);
```

Usually, the `grantRequest` will be exactly identical to the body received by the custom security backend. In the security backend, you merely decide which grant requests to forward and which not to forward.

If you want to revoke the grant at a later point in time, you can do this using:

```javascript
sdk.revokeGrant({
  sessionId: "ijfoewio22490320",
  deviceId: "d123",
  grantType: "subscribeToTelemetry"
});
```

You can revoke all grants for a session with this:

```javascript
sdk.revokeSession("ijfoewio22490320");
```

You can even revoke all sessions:

```javascript
sdk.revokeAll();
```
