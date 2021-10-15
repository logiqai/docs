# Configuring Prometheus

LOGIQ monitoring is powered by Prometheus. The steps below assume that your LOGIQ UI is up and running. To connect to your prometheus setup, head over the _Data Sources_ in settings

![Data Sources](<../.gitbook/assets/Screen Shot 2020-04-27 at 5.50.11 PM.png>)

We are going to click on the _New Data Source_ button

![](<../.gitbook/assets/Screen Shot 2020-04-27 at 5.53.33 PM.png>)

Next, let us select the prometheus Data source from the data sources screen

{% hint style="success" %}
LOGIQ supports many data sources, LOGIQ's provides tighter integration with Prometheus and uses its time series database for monitoring.
{% endhint %}

![](<../.gitbook/assets/Screen Shot 2020-04-27 at 5.57.40 PM.png>)

Enter your prometheus data source URL and check the connection by clicking on _Test Connection_

![](<../.gitbook/assets/Screen Shot 2020-04-27 at 6.06.46 PM.png>)

{% hint style="success" %}
You are now ready to visualize your metrics
{% endhint %}
