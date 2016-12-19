##样式
1.修改ScrollBar样式
属性：
水平：
```
android:scrollbars="horizontal"
android:scrollbarThumbHorizontal="xxx"
```
竖直：
```
android:scrollbars="vertical"
android:scrollbarThumbVertical="@drawable/scrollbar"
```
样式：
```
<shape>
<solid android:color="#9d333"/>
<corners android:radius="2dp"/>
</shape>
```

android:scrollbarStyle="xxx"，设置滚动条的位置。
insideOverlay:默认
insideInset：（位置在padding内，会插入在View后面，不会遮挡View）
outsideOverlay：（位置在padding外，覆盖在View上，如果滚动条比padding大会遮挡View）
outsideInset：（位置在padding外，会插入在View后面，不会遮挡View）

2.去除滑动尽头阴影效果
android:overScrollMode="never" 