# AppWidget
If you want to create your appwidget for your app, you can use this starter sample.
If you think to just put two TextView on screen, again use ListView. Because if your text lenght is dynamic you cant control your area size and cant add simply Scrollview. Scrollview doesn't support inside appwidgets.

[For more info](https://developer.android.com/guide/topics/appwidgets/index.html)

[StackWidget Sample](https://android.googlesource.com/platform/development/+/master/samples/StackWidget) - import project with Android Studio

[WeatherListWidget Sample](https://github.com/android/platform_development/tree/master/samples/WeatherListWidget)



# updatePeriodMillis
 
 - Updates requested with updatePeriodMillis will not be delivered more than once every 30 minutes.
 - If you think android:updatePeriodMillis not working, don't forgot to add android:exported="true" at your receiver. After that if onUpdate not triggered check super.onReceive inside onReceive method. 
 - If you want to update your widget more than once every 30 minutes , you must use AlarmManager and set android:updatePeriodMillis to 0
 
 ```java
 Intent alarm = new Intent(context, WidgetProvider.class);
 alarm.setAction(AppWidgetManager.ACTION_APPWIDGET_UPDATE);
 alarm.putExtra(AppWidgetManager.EXTRA_APPWIDGET_IDS, appWidgetIds);
 pendingIntent = PendingIntent.getBroadcast(context, 0, alarm, PendingIntent.FLAG_CANCEL_CURRENT);
 alarmManager.setRepeating(AlarmManager.RTC, System.currentTimeMillis(),1000, pendingIntent);
 ```

# Update Widget Outside
You can update your appwidget inside from Activity or Fragment
```java
 AppWidgetManager appWidgetManager = AppWidgetManager.getInstance(context);
 int appWidgetIds[] = appWidgetManager.getAppWidgetIds(new ComponentName(context, WidgetProvider.class));
 appWidgetManager.notifyAppWidgetViewDataChanged(appWidgetIds, R.id.widget_list);
```
