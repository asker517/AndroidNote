# Android坐标系

------
### android 中的坐标系统
> * 屏幕的左上角是坐标系统原点（0,0）
> * 原点向右延伸是X轴正方向，原点向下延伸是Y轴正方向

![Android-Coordinate-System](https://raw.githubusercontent.com/asker517/AndroidNote/master/png/coordinate.png)

### Scroll
> * getScrollY(): view相对于“坐标系统原点(0,0)”在Y轴上的偏移量
> * getScrollX(): view相对于“坐标系统原点(0,0)”在X轴上的偏移量
> * view.scrollTo(x,y):  将整个父视图的左上角定为(0,0)，再移动这个屏幕的左上角到父视图的点(x,y)处，注意此处的x和y是根据父视图的坐标系来定的。
> * view.scrollBy(x,y):  x代表横向移动的距离，y代表纵向移动的距离

### MotionEvent类中 getRowX()和 getX()
> * event.getRowX(): 触摸点相对于**屏幕原点**的X坐标
> * event.getX(): 触摸点相对于其所在**组件原点**的X坐标

### android.view.View.layout(int l, int t, int r, int b)
> *   layout的过程就是确定View在屏幕上显示的具体位置，在代码中就是设置其成员变量mLeft，mTop，mRight，mBottom的值，这几个值构成的矩形区域就是该View显示的位置，不过这里的具体位置都是相对与父视图的位置

### View坐标
> * view.getX(): 获取相对于父视图而言的两个左边缘的距离;
> * view.getY(): 获取相对于父视图而言的两个上边缘的距离;

### view.getLocationOnScreen(int[2] location)
> * **location[0]:** 代表X值，表示该view的左边缘与屏幕的左边缘之间的距离。可以想象，当滑屏产生，view开始移动该值肯定会改变的。
> * **location[1]:** 代表Y值，表示该view的上边缘与屏幕的上边缘之间的距离，该距离肯定是包含标题栏的高度的。




