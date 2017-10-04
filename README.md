# AppWidget
Android Homescreen widget(Appwidget) sample

# updatePeriodMillis
 
 - Updates requested with updatePeriodMillis will not be delivered more than once every 30 minutes.
 - If you think android:updatePeriodMillis not working, don't forgot to add android:exported="true" at your receiver. After that if onUpdate not triggered check super.onReceive inside onReceive method. 
