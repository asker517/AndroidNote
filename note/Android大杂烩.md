##Android Service中弹出Dialog窗口
1.注册权限

```
<uses-permission android:name="android.permission.SYSTEM_ALERT_WINDOW"/>
```

2.代码部分

```java
AlertDialog dialog = b.create();
dialog.getWindow().setType(WindowManager.LayoutParams.TYPE_SYSTEM_ALERT);
dialog.show();
```


----------


  
##判断程序是否在前台运行
1.注册权限

```
<uses-permission android:name="android.permission.GET_TASK"/>
```

2.代码部分:

```java
    private boolean isRunningInForeground() {
        ActivityManager manager = (ActivityManager) getSystemService(Context.ACTIVITY_SERVICE);
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


----------

##Popupwindow响应Key事件
Popupwindow本身无法设置OnKeyListener,所以只能给popupwindow.getContentView().setOnKeyListener{...},并且要设置

```java
popupwindow.getContentView().setFocusableInTouchMode(true);
```

##PopupWindow在空间充足的情况下弹出位置

```java
 int[] location = new int[2];  
 anchor.getLocationOnScreen(location); 
 //上方
 popupWindow.showAtLocation(v, Gravity.NO_GRAVITY, location[0], location[1]-popupWindow.getHeight()); 
 
 //正上方
 popupWindow.showAtLocation(parent, Gravity.NO_GRAVITY, location[0]+anchor.getWidth()/2-popupWindow.getWidth()/2, location[1] - popupWindow.getHeight());
 
 //下方
 popupWindow.showAsDropDown(anchor);
 
 //正下方
 popupWindow.showAsDropDown(andhor,andhor.getWidth()/2-popupWindow.getWidth()/2,0);
 
 //左边
 popupWindow.showAtLocation(anchor, Gravity.NO_GRAVITY, location[0] - popupWindow.getWidth(), location[1]);
 
 //右边
 popupWindow.showAtLocation(anchor, Gravity.NO_GRAVITY, location[0] + anchor.getWidth(), location[1]); 
 
```


----------

##ListView最佳精确恢复滚动位置方法之一

```java
//Save the current state
Parcelable state = mListView.onSaveInstanceState();

//Restore the state
mListView.onRestoreInstanceState(state);
```

----------

##判断点击位置是否在指定的View上

```java
private boolean isInRangeOfView(View view, MotionEvent ev) {

        int[] location = new int[2];
        view.getLocationOnScreen(location);
        int x = location[0];
        int y = location[1];
        if (ev.getRawX() < x || ev.getRawX() > (x + view.getWidth()) || ev.getRawY() < y || ev.getRawY() > (y
            + view.getHeight())) {
            return false;
        }
        return true;
    }
```

----------

##判断ListView是否滚动到了顶部(无Header情况)
```java
View firstItem = listView.getChildAt(0);  //返回的是可见视图范围内的第一条Item视图
Rect rect = new Rect(0, 0, firstItem.getWidth(), firstItem.getHeight());
listView.getChildVisibleRect(firstItem, rect, null);
if (rect.height() < firstItem.getHeight()) { 
   //ListView第一个条目没有完全显示完(未到达顶部)
}
```

----------

##9.png图片制作
左上为拉伸区域；右下为内容显示区域

----------

##LayoutInflater的三种方式区别

- LayoutInflater.inflate(resId , null)：**创建ID为resId的view，并且返*回该view*；不能正确处理该view自身定义的宽和高**，因为：layout_width，layout_height是相对了父级设置的，必须与父级的LayoutParams一致。而此root参数为null，不会生成相应的LayoutParams。

-  LayoutInflater.inflate(resId , parent,，false)：**创建ID为resId的view，并且返*回该view*；可以正确处理view自身定义的宽和高**，因为root参数不为空，view会从root.generateLayoutParams(attrs)得到的对应的LayoutParams。

- LayoutInflater.inflate(resId , parent,，true)：**创建ID为resId的view，并且把该view加入到parent，最终*返回的是parent*；可以正确处理view自身定义的宽和高。**
