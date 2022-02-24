# Configure your existing IoT Hub

In order to use the following hooks, you need to perform additional setup steps:

* [useConnectionState](../using-react/hooks.md#useconnectionstate)
* [useDeviceTwin](../using-react/hooks.md#usedevicetwin)

In both cases, the IoT Hub routing must be configured.

## Device Twin Changed Events

For 'Device Twin Changed Events', which are required for the [useDeviceTwin](../using-react/hooks.md#usedevicetwin) hook, a routing rule must be added as follows:

![](<../.gitbook/assets/image (18).png>)

If you want to use Azure CLI, you can accomplish the same in the following way:

{% tabs %}
{% tab title="AZ CLI" %}
```bash
az iot hub route create \
  --route-name ux4iot-twinchanges  \
  --hub-name IOT_HUB_NAME \
  --resource-group RESOURCE_GROUP_OF_IOT_HUB \
  --condition true \
  --endpoint events \
  --source twinchangeevents
```
{% endtab %}
{% endtabs %}

## Connection State Events

For 'Connection State Events', which are required for the [useConnectionState](../using-react/hooks.md#useconnectionstate) hook, a routing rule must be added as follows:

![](<../.gitbook/assets/image (19).png>)

If you want to use Azure CLI, you can accomplish the same in the following way:

{% tabs %}
{% tab title="AZ CLI" %}
```bash
az iot hub route create \
  --route-name ux4iot-connectionevents  \
  --hub-name IOT_HUB_NAME\
  --resource-group RESOURCE_GROUP_OF_IOT_HUB \
  --condition true \
  --endpoint events \
  --source deviceconnectionstateevents
```
{% endtab %}
{% endtabs %}
