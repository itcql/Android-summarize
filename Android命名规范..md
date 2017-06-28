# Android 命名规范
### Resources files
#### Drawable files
Naming conventions for drawables:  
| Asset Type   | Prefix            |		Example               |
|--------------| ------------------|-----------------------------|
| Action bar   | `ab_`             | `ab_stacked.9.png`          |
| Button       | `btn_`	            | `btn_send_pressed.9.png`    |
| Dialog       | `dialog_`         | `dialog_top.9.png`          |
| Divider      | `divider_`        | `divider_horizontal.9.png`  |
| Icon         | `ic_`	            | `ic_star.png`               |
| Menu         | `menu_	`           | `menu_submenu_bg.9.png`     |
| Notification | `notification_`	| `notification_bg.9.png`     |
| Tabs         | `tab_`            | `tab_pressed.9.png`         |

Naming conventions for icons (taken from [Android iconography guidelines](http://developer.android.com/design/style/iconography.html)):

| Asset Type                      | Prefix             | Example                      |
| --------------------------------| ----------------   | ---------------------------- |
| Icons                           | `ic_`              | `ic_star.png`                |
| Launcher icons                  | `ic_launcher`      | `ic_launcher_calendar.png`   |
| Menu icons and Action Bar icons | `ic_menu`          | `ic_menu_archive.png`        |
| Status bar icons                | `ic_stat_notify`   | `ic_stat_notify_msg.png`     |
| Tab icons                       | `ic_tab`           | `ic_tab_recent.png`          |
| Dialog icons                    | `ic_dialog`        | `ic_dialog_info.png`         |

Naming conventions for selector states:

| State	       | Suffix          | Example                     |
|--------------|-----------------|-----------------------------|
| Normal       | `_normal`       | `btn_order_normal.9.png`    |
| Pressed      | `_pressed`      | `btn_order_pressed.9.png`   |
| Focused      | `_focused`      | `btn_order_focused.9.png`   |
| Disabled     | `_disabled`     | `btn_order_disabled.9.png`  |
| Selected     | `_selected`     | `btn_order_selected.9.png`  |

#### Dimensions
app应该只定义一组有限的diemens,它们必须要被不断重复使用。这样大多数deimensions默认就是all
应该用：
<WHAT>_ALL_<DESCRPITION>_<SIZE>

特定页面也可以用：
<WHAT>_<WHERE>_<DESCRPITION>_<SIZE>
这里的what是下面表格中的一种：  
|前缀|用法|
|--------------|----------------|
|width|宽度|
|height|	高度|
|size	|宽度=高度|
|margin	|margin外边距|
|padding|	padding内边距|
|elevation	|角度|
|keyline|	边缘对齐位置|
|textsize	|文本大小的sp|
注意上面的列表包含了大部分会用到的what,还有一些dimension限定符类似：rotation,scale...通常只是在drawables被用到而且不能重用。
例子： 
> 译者注：all不用声明，所以默认是all 
 
* height_toolbar:所有toolbar的高度
* keyline_listtext:listitem的文本边缘对齐
* textsize_medium:所有文本的中等大小
* size_menu_icon:menu里面图标size
* height_menu_profileimage:menu的头像图片高度