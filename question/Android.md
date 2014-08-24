## Android Service中弹出Dialog窗口 ##
1. 注册权限 **<uses-permission android:name="android.permission.SYSTEM_ALERT_WINDOW"/>**
2. 代码部分:
 
    AlertDialog dialog = b.create();
            **dialog.getWindow().setType(WindowManager.LayoutParams.TYPE_SYSTEM_ALERT);**
            dialog.show();