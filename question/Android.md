##Android Service中弹出Dialog窗口
1.注册权限

```
<uses-permission android:name="android.permission.SYSTEM_ALERT_WINDOW"/>
```

2.代码部分

```
AlertDialog dialog = b.create();
dialog.getWindow().setType(WindowManager.LayoutParams.TYPE_SYSTEM_ALERT);
dialog.show();
```
        
##判断程序是否在前台运行
1.注册权限

```
<uses-permission android:name="android.permission.GET_TASK"/>
```

2.代码部分:

```

 private boolean isRunningInForeground() {
    		ActivityManager manager = (ActivityManager)getSystemService(Context.ACTIVITY_SERVICE);
    		List<ActivityManager.RunningAppProcessInfo> appProcesses = manager.getRunningAppProcesses();
	if (appProcesses == null) return false;
	for (ActivityManager.RunningAppProcessInfo appProcess : appProcesses) {
      		if (appProcess.processName.equals(MY_APP_PACKAGE)
          		&& appProcess.importance == ActivityManager.RunningAppProcessInfo.IMPORTANCE_FOREGROUND) {
       		 	return true;
     		 }
    		}
			return false;
		}
```


##Popupwindow响应Key事件
Popupwindow本身无法设置OnKeyListener,所以只能给popupwindow.getContentView().setOnKeyListener{...},并且要设置

```
popupwindow.getContentView().setFocusableInTouchMode(true);
```

##ListView最佳精确恢复滚动位置方法之一
```
//Save the current state
Parcelable state = mListView.onSaveInstanceState();

//Restore the state
mListView.onRestoreInstanceState(state);
```

