---
title: Anrdoid 编码规范
date: 2016-12-05 09:58:47
authors:
  - EvanWang
categories:
  - Android
  - Coding Rule
tags:
  - Android
  - Coding Rule
---

# 命名规范

## 通用规则

- 命名原则：尽可能的用最少的字符而又能完整的表达标识符的含义。
- 英文缩写原则：
  1. 较短的单词可通过去掉 **”元音”** 形成缩写
  1. 较长的单词可取单词的 **头几个字母** 形成缩写
  1. 此外还有一些 **约定俗成** 的英文单词缩写
- 一些常见的英文单词缩写：

<!-- more -->

| 名称 | 缩写 | 说明 |
| --- | --- | --- |
| icon | ic | app的图标、界面中小图标 |
| color | cl | 颜色值 |
| divider | di | 分隔线，包括 Listview 中的 divider，普通布局中的线 |
| selector | sl | view多种状态，包括 Listview 中的 selector，按钮的 selector |
| background | bg | 背景、布局的背景 |
| buffer | buf | IO缓冲区，临时缓存区 |
| error | err | 表示错误 |
| delete | del | 删除 |
| control | ctrl | 控制、控制器|
| escape | esc | 转义、离开 |
| document | doc | 文档相关 |
| infomation | info | 代表信息、内容 |
| message | msg | 代表消息、通信、交互 |
| image | img | 代表图像 |
| string | str | 代表字符串|
| Internationalization | I18N | 国际化 |
| initial | init | 用于初始化 |
| increment | inc | 数值的增加 |
| length | len | 长度|
| average | avg | 平均值 |
| position | pos | 位置、遍历的指针 |
| temp | tmp | 临时、临时变量 |
| password | pwd | 密码 |
| library | lib | 库、代码库、第三方库 |
| server | srv | 服务器相关 |
| window | wnd(win) | 界面窗口 |


## Java

主要参考 {% post_link java-rule-coding-style %}，下面是基于 `Android` 平台的一些补充。

### 包名

采用反域名命名规则，全部使用小写字母。一级包名为 `com` ，二级包名为 `组织`（可以是公司或个人），三级包名根据 `应用` 进行命名，四级包名为 `模块名` 或 `层级名`
，后面的都是细分的 `次级模块名`

| 包名 | 此包中包含 |
| ---- | ----- |
| com.xx.yy.ui | 页面相关包 |
| com.xx.yy.ui.activity | 页面用到的Activity类|
| com.xx.yy.ui.base | 页面中的基础共享类 ( `BaseActivity`、`BaseFragment`、`BaseAdapter`等 ) |
| com.xx.yy.ui.adapter | 页面用到的 `Adapter类` (适配器的类) |
| com.xx.yy.ui.view | 自定义View类 |
| com.xx.yy.utils | 公共工具方法类 |
| com.xx.yy.model | `model` 数据模型相关包 |
| com.xx.yy.model.bean | `bean` 实体类 |
| com.xx.yy.model.db | 数据库操作类 |
| com.xx.yy.app | Android组件，包括 `Application` |
| com.xx.yy.app.service | `Service` 服务 |
| com.xx.yy.app.receiver | `Receiver` 广播接收类 |

### 类名

| 类 | 描述 | 例如
| -- | -- | -- |
| Activity类 | `Activity` 为后缀 | 欢迎页面类 WelcomeActivity |
| Fragment类 | `Fragment` 为后缀 | 标签页面类 TabFragment |
| Adapter类 | `Adapter` 为后缀 | 新闻详情适配器 NewDetailAdapter |
| 公共方法类 | `Utils` 或 `Manager` 为后缀 | 线程池管理类：ThreadPoolManager、日志工具类：LogUtils |
| 数据库类 | `DBHelper` 为后缀 | 新闻数据库 NewDBHelper |
| Service类 | `Service` 为后缀 | 时间服务 TimeService |
| Receiver类 | `Receiver` 为后缀 | 时间通知 TimeReceiver
| ContentProvider | `Provider` 为后缀 | AccountProvider
| 共享基础类 | `Base` 为前缀 | BaseActivity, BaseFragment

### 方法

| 方法名 | 说明 |
| --- | --- |
| initXX() | 初始化相关方法,使用 `init` 为前缀标识，如初始化布局initView() |
| isXX() checkXX() hasXX() | 方法返回值为 `boolean` 型的请使用 `is`、 `check` 或 `has` 为前缀标识 |
| getXX() | 返回某个值的方法，使用 `get` 为前缀标识 |
| processXX() | 对数据进行处理的方法，尽量使用 `process` 为前缀标识 |
| loadXX() | 通过异步加载数据的方法，尽量使用 `load` 为前缀标识 |
| displayXX() | 弹出提示框和提示信息，使用 `display` 为前缀标识 |
| saveXX() | 与保存数据相关的，使用 `save` 为前缀标识 |
| resetXX() | 对数据重组的，使用 `reset` 为前缀标识 |
| clearXX() removeXXX() | 清除数据相关的，使用 `clear` 或 `remove` 为前缀标识 |
| drawXXX() | 绘制数据或效果相关的，使用 `draw` 为前缀标识 |
| doXX() | 一些细分内部的方法，使用 `do` 为前缀标识 |

### 局部变量

用统一的量词通过在结尾处放置一个量词，就可创建更加统一的变量，它们更容易理解，也更容易搜索。例如，请使用 `strCustomerFirst` 和 `strCustomerLast`，而不要使用 `strFirstCustomer` 和 `strLastCustomer`。

| 量词列表 | 量词后缀说明 |
| -- | -- |
| First | 一组变量中的第一个 |
| Last |  一组变量中的最后一个 |
| Next | 一组变量中的下一个变量 |
| Prev | 一组变量中的上一个 |
| Cur  | 一组变量中的当前变量 |


### 字符串常量

Android SDK中诸如 `SharedPreferences`，`Bundle` 和 `Intent` 等，都采用**key-value** 的方式进行赋值，当使用这些组件的时候，**key** 必须被 `static final` 所修饰，并且命名应该符合以下规范：

| Element            | Field Name Prefix   |
| -----------------  | -----------------   |
| SharedPreferences  | `PREF_`             |
| Bundle             | `BUNDLE_`           |
| Fragment Arguments | `ARGUMENT_`         |
| Intent Extra       | `EXTRA_`            |
| Intent Action      | `ACTION_`           |

需要注意的是，当调用Fragment的 `getArguments()` 方法时，返回值同样是一个 `Bundle`，因为这也是一个常用函数，因此我们需要定义一个不同的前缀，示例如下：

```java
static final String PREF_EMAIL = "PREF_EMAIL";
static final String BUNDLE_AGE = "BUNDLE_AGE";
static final String ARGUMENT_USER_ID = "ARGUMENT_USER_ID";

static final String EXTRA_SURNAME = "com.myapp.extras.EXTRA_SURNAME";
static final String ACTION_OPEN_USER = "com.myapp.action.ACTION_OPEN_USER";
```


## JNI

待续

## Resource 资源

### 概述

- Android 系统资源结构如下：(参考 [Google官方介绍](https://developer.android.google.cn/guide/topics/resources/providing-resources.html?hl=zh-cn) )
  ```text
  res/
  ├─ anim/      -> 定义 渐变动画的 XML 文件（属性动画也可以保存在此目录中，但是为了区分这两种类型，属性动画首选 animator/ 目录）
  ├─ animator/  -> 定义 属性动画的 XML 文件
  ├─ color/     -> 用于定义 颜色状态列表的 XML 文件
  ├─ drawable/  -> 用于定义 位图文件(.png、.9.png、.jpg、.gif) 或 可编译为图像资源的 XML 文件
  ├─ layout/    -> 用于定义 界面布局的 XML 文件
  ├─ menu/      -> 用于定义 应用菜单（如选项菜单、上下文菜单或子菜单）的 XML 文件
  ├─ mipmap/    -> 适用于不同启动器图标密度的可绘制对象文件
  ├─ raw/       -> 要以 原始形式保存的任意文件
  ├─ values/    -> 包含字符串、整型数和颜色等简单值的 XML 文件
  └─ xml/       -> 各种 XML 配置文件都必须保存在此处
  ```
  `res/` 下的文件夹为 **官方定义** 的资源文件夹，名字不能随意更改
- `anim/` 下 XML资源 的结构：
  ```xml
  ROOT
  ├─ <alpha>
  ├─ <rotate>
  ├─ <scale>
  ├─ <translate>
  ├─ <*Interpolator>
  ├─ <*Animation>
  └─ <set>
      ├─ <alpha>
      ├─ <rotate>
      ├─ <scale>
      ├─ <translate>
      └─ <set>
  ```
- `animator/` 下 XML资源 的结构：
  ```xml
  ROOT
  ├─ <animator>
  │   └─ <propertyValuesHolder>
  ├─ <objectAnimator>
  │   └─ <propertyValuesHolder>
  ├─ <selector>
  │   └─ <item android:animation="" android:state_xxx="true/false" />
  └─ <set>
      ├─ <animator>
      ├─ <objectAnimator>
      ├─ <propertyValuesHolder>
      └─ <set>
  ```
- `color/` 下 XML资源 的结构：
  ```xml
  ROOT
  └─ <selector>
      └─ <item android:color="" android:state_xxx="true/false" />
  ```
- `drawable/` 下 XML资源 的结构：
  ```xml
  ROOT
  ├─ <animated-rotate>
  │   └─ ROOT
  ├─ <animated-selector>
  │   ├─ <transition>
  │   │   └─ <animation-list>
  │   └─ <item android:drawable="" android:state_xxx="true/false" />
  ├─ <animated-vector>
  │   └─ <target />
  ├─ <animation-list>
  │   └─ <item android:drawable="" android:duration="" />
  ├─ <bitmap> <color> <nine-patch>
  ├─ <clip> <inset> <rotate> <scale>
  │   └─ ROOT
  ├─ <layer-list> <ripple> <transition>
  │   └─ <item android:drawable="" [width/height][direction][gravity] />
  ├─ <level-list>
  │   └─ <item android:drawable="" android:maxLevel="" android:minLevel=""/>
  ├─ <selector>
  │   └─ <item android:drawable="" android:state_xxx="true/false" />
  ├─ <shape>
  │   ├─ <corners />
  │   ├─ <gradient />
  │   ├─ <padding />
  │   ├─ <size />
  │   ├─ <solid />
  │   └─ <stroke />
  └─ <vector>
      ├─ <clip-path />
      ├─ <path />
      └─ <group>
          ├─ <clip-path />
          ├─ <path />
          └─ <group>
  ```

- `menu/` 下 XML资源 的结构：
  ```xml
  ROOT
  └─ <menu>
      ├─ <group>       -> menu组
      │   └─ <item />
      └─ <item />      -> menu项
  ```
- `values/` 下 XML资源 的结构：
  ```xml
  ROOT
  └─ <resources>
      ├─ <array>              -> 任意类型的数组（TypedArray）
      ├─ <boolean>            -> 布尔值
      ├─ <color>              -> 十六进制颜色值
      ├─ <declare-styleable>  -> 声明自定义属性
      ├─ <dimension>          -> 尺寸值
      ├─ <fraction>           -> 相对比例值
      ├─ <item type="id"/>    -> 预定义ID
      ├─ <integer>            -> 整数值
      ├─ <integer-array>      -> 整数数组
      ├─ <plurals>            -> 复数字符串
      ├─ <string>             -> 字符串
      ├─ <string-array>       -> 字符数组
      └─ <style>              -> 样式
  ```

- 命名规则：
  资源文件、元素应该采用 **小写字母_下划线**（匈牙利命名法）的组合形式命名。
- 命名空间隔离：
  - 资源文件、元素应该使用 **范围** 作为前缀，范围一般采用 **模块_界面**
  - 如果所开发的为 **通用组件**，为避免冲突，将资源目录下的文件名增加前缀，进行命名空间的隔离

### 资源文件

#### Anim/Animator 动画文件

- 文件名：`动画类型_动画方向.xml`

| State        | Suffix          |
|--------------|-----------------|
| fade_in      | 淡入             |
| fade_out     | 淡出             |
| push_down_in | 从下方推入        |
| push_down_out| 从下方推出        |
| push_left    | 推向左方          |
| slide_in_from_top | 从头部滑动进入|
| zoom_enter   | 变形进入         |
| slide_in     | 滑动进入         |
| shrink_to_middle | 中间缩小     |

- 每个项目最好导入一些常用的 `预定义动画`
- 如果要自己 **定制的复杂** 动画，推荐命名采用 `范围_动画类型`。
  例如：`refresh_progress.xml`、`market_cart_add.xml`、`market_cart_remove.xml`

#### Drawable 图片文件

- 文件名：`[模块_]图片类型_范围_状态.[png/9.png/jpg/gif/xml]`
- 图片类型：

| Image Type   |   类型   | Prefix            |        Example          |
|--------------| ------- | ------------------|-------------------------|
| Background   |  背景    | `bg_`             | bg_splash.png            |
| Button       |  按钮    | `btn_`            | btn_send_pressed.png    |
| Divider      |  分隔    | `div_`            | div_horizontal.png      |
| Icon         |  图标    | `ic_`             | ic_star.png             |
| Default      |  默认    | `def_`            | def_search_cell.png      |

- 常规 `icon`（图标）文件命名方式：

| Icon Type                      | Prefix             | Example                    |
| --------------------------------| ----------------   | -------------------------- |
| Icons                           | `ic_`              | ic_star.png                |
| Launcher icons                  | `ic_launcher`      | ic_launcher_calendar.png   |
| Menu icons & Action Bar icons   | `ic_menu`          | ic_menu_archive.png        |
| Tool bar icons                  | `ic_tool_bar`      | ic_tool_bar_back.png       |
| Status bar icons                | `ic_stat_bar`      | ic_stat_bar_msg.png        |
| Tab icons                       | `ic_tab`           | ic_tab_recent.png          |
| Dialog icons                    | `ic_dlg`           | ic_dlg_info.png            |
| Notification icons              | `ic_notif`         | ic_notif_clock.png         |

- 状态（后缀）：

| State        | 状态  | Suffix          | Example                   |
|--------------| ---- |-----------------|---------------------------|
| Normal       |  默认 | `_normal`       | btn_order_normal.png      |
| Pressed      |  按下 | `_pressed`      | btn_order_pressed.png     |
| Focused      |  焦点 | `_focused`      | btn_order_focused.png     |
| Disabled     | 不可用 | `_disabled`     | btn_order_disabled.png    |
| Selected     | 选中 | `_selected`     | btn_order_selected.png    |
| Selector     | 多种状态组合 | `_selector`     | btn_order_selector.png    |

- 需要注意的是，Selector 的一些状态是可以叠加的，所以可以产生 `btn_order_disabled_focused.9.png` 这类命名。
- 永远使用 [android-selector-chapek](https://github.com/inmite/android-selector-chapek) 这个插件来生成相应的 Selector Drawable XML 文件，而不应该手工创建。

#### Color 颜色文件

- 文件名：`[模块_]颜色类型_范围_状态.xml`
- 颜色类型：
  - 背景颜色，添加 `bg` 前缀
  - 文本颜色，添加 `txt` 前缀
  - 分割线颜色，添加 `div` 前缀
- 状态（后缀）：同 `drawable` 状态后缀


#### Layout 布局文件

- 文件名：`[模块_]布局类型_范围_功能.xml`
- 布局类型：

| Layout Type |   类型   | Prefix           |        Example          |
|------------| -------- | ---------------- |-------------------------|
| Activity   |  UI 基础类 Activity | `act_`  | act_main_list.xml      |
| Fragment   |  UI 基础类  Fragment | `frg_`  | frg_main_detail.xml    |
| Dialog     |  对话框 Dialog | `dlg_`      | dlg_login_loading.xml        |
| PopupWindow | 弹窗 PopupWindow | `ppw_`      | ppw_user_info.xml        |
| Item       |  List/Grid/RecyclerView 列表项  | `item_`     | item_shop_product.xml             |
| Include    |  layout 包含项    | `inc_`            | inc_search_head.xml      |
| Header/Footer    |  ListView的头尾布局    | `header_` `footer_`            | header_list_products.xml      |


#### Style、Theme 文件

- 应该谨慎使用`style`与`theme`，避免重复冗余的文件出现。可以有多个`styles.xml` 文件，如：`styles.xml`，`style_home.xml`，`style_item_details.xml`，`styles_forms.xml`等。

- **`res/values` 目录下的文件可以任意命名，但前提是该文件能够明确表达职责所属，因为起作用的并不是文件本身，而是内部的标签属性。**

#### Attr 文件

- 自定义属性

### 资源元素

#### id 布局中ID

- 原生控件

布局 ViewGroup

| 布局 | 缩写 | 含义 |
| --- | --- | --- |
| ViewGroup | vg | 抽象ViewGroup
| FrameLayout | fl | 帧布局 |
| TLayout | fl | 帧布局 |
| LinearLayout | ll | 线性布局 |
| RelativeLayout | rl | 相对布局 |


控件 View

| 控件 | 缩写 | 含义 | 控件 | 缩写 | 含义 |
| --- | --- |  --- |  --- | --- | --- |
| TextView | tv | 文本 | SurfaceView | surface | 异步视图
| Button | btn | 按钮 | VideoView | video | 视频视图 |
| ImageButton | ib | 图片按钮 | WebView | web | 网页视图 |
| ImageView | iv | 图片 | SearchView | search | 搜索框 |
| EditText | edt | 编辑框 | DatePicker  | datepk | 日期选择器 |
| CheckBox | cb | 复选 | TimePicker | timepk | 时间选择器 |
| RadioGroup | rg | 单选按钮组 | DigtalClock | dcl | 数字时钟 |
| RadioButton | rb | 单选按钮 | AnalogClock | acl | 模拟时钟 |
| ScrollView | sv | 滚动页 |  CalendarView | cld | 日历 |
| ListView  | lv | 列表页 | Chronometer | cmt | 秒表 |
| GridView  | gv | 网格页 | MediaController | mdCtrl | 多媒体控制 |
| ExpandableListView  | elv | 可扩展列表页 | ZoomControls | zmCtrl | 放大缩小框 |
| ToggleButton | tgb | 切换按钮 | TextSwitch | txtSwt | 文字切换器 |
| SeekBar | seek | 双向进度条 | ImageSwitch | imgSwt | 图片切换器 |
| ProgressBar | pgb | 进度条 | RatingBar | ratb | 评分条 |
| TableRow | tr | 标签列 | MapView | map | 地图视图 |
| TabHost | tab | 标签页 | SlidingDrawer | 滑动抽屉 |
| Spinner | spn | 下拉框 |

- 官方补充控件

布局 ViewGroup

| 控件 | 缩写 | 包 | 含义 |
| --- | --- |  --- | --- |
| GridLayout | gl | support-v7 | 网格布局 |
| TabLayout | tl | support-v7 | Tab布局 |
| ConstraintLayout | cl | constraint | 约束布局 |
| PercentFrameLayout | pfl | percent | 比例帧布局 |
| PercentRelativeLayout | prl | percent | 比例相对布局 |

组件 View

| 控件 | 缩写 | 包 | 含义 |
| --- | --- |  --- | --- |
| ViewPager | vp | support-v4 | 左右滑动页 |
| RecyclerView | rv | support-v7 | 可复用的列表页 |

#### color 色值

`colors.xml` 文件就像个“调色板”，只映射颜色的ARGB值，不应该存在其他类型的数值，更不要使用它为不同的按钮来定义ARGB值。

**不建议** 使用以下命名规则：

```xml
<resources>
  <color name="button_foreground">#FFFFFF</color>
  <color name="button_background">#2A91BD</color>
  <color name="comment_background_inactive">#5F5F5F</color>
  <color name="comment_background_active">#939393</color>
  <color name="comment_foreground">#FFFFFF</color>
  <color name="comment_foreground_important">#FF9D2F</color>
  ...
  <color name="comment_shadow">#323232</color>
```

使用这种定义方式，我们需要非常的谨慎，一不小心就会重复定义ARGB值，而且当改变基本色时，会造成很多冗余重复的操作。

相反地，我们应该根据颜色或者风格对ARGB赋值：

```xml
<resources>

  <!-- grayscale -->
  <color name="white"     >#FFFFFF</color>
  <color name="gray_light">#DBDBDB</color>
  <color name="gray"      >#939393</color>
  <color name="gray_dark" >#5F5F5F</color>
  <color name="black"     >#323232</color>

  <!-- basic colors -->
  <color name="green"     >#27D34D</color>
  <color name="blue"      >#2A91BD</color>
  <color name="orange"    >#FF9D2F</color>
  <color name="red"       >#FF432F</color>

</resources>
```

对 **同一色调，不同色域** 进行定义时，像 `brand_primary`、`brand_secondary`、 `brand_negative` 这样的命名也是不错的选择。

这样规范的颜色很容易修改或重构，App一共使用了多少种不同的颜色变会得非常清晰。


#### dimen 尺寸

我们应该像对待 `colors.xml` 一样对待 `dimens.xml` 文件，与定义颜色调色板无异，也应该定义一个规范字体大小的 “字号板”。

一个很好的建议：

```xml
<resources>

  <!-- font sizes -->
  <dimen name="font_larger">22sp</dimen>
  <dimen name="font_large">18sp</dimen>
  <dimen name="font_normal">15sp</dimen>
  <dimen name="font_small">12sp</dimen>

  <!-- typical spacing between two views -->
  <dimen name="spacing_huge">40dp</dimen>
  <dimen name="spacing_large">24dp</dimen>
  <dimen name="spacing_normal">14dp</dimen>
  <dimen name="spacing_small">10dp</dimen>
  <dimen name="spacing_tiny">4dp</dimen>

  <!-- typical sizes of views -->
  <dimen name="button_height_tall">60dp</dimen>
  <dimen name="button_height_normal">40dp</dimen>
  <dimen name="button_height_short">32dp</dimen>

</resources>
```

同样的，在定义 `margin` 和 `padding` 时，可以使用 `spacing_****` 作为前缀对其命名，而不是像对待 `String` 字符串那样直接写值。

这样写的好处是，使组织结构和修改风格甚至布局变得非常容易。

#### style 样式

- Style 与 Theme 的命名统一使用 **驼峰命名法**（首字母大写）

- 几乎每个项目都需要适当的使用 Style 文件，因为对于一个视图来说有一个重复的外观是很常见的。在应用中对于大多数文本内容，最起码你应该有一个`通用的 Style 文件`，例如：

  ```xml
  <style name="ContentText">
      <item name="android:textSize">@dimen/font_normal</item>
      <item name="android:textColor">@color/basic_black</item>
  </style>
  ```

  应用到 TextView 中:

  ```xml
  <TextView
      style="@style/ContentText"
      android:layout_width="wrap_content"
      android:layout_height="wrap_content"
      android:text="@string/price"
      />
  ```


#### string 文字

- 命名：`类型_[范围_]功能`

以下为几种常用的命名：

| 控件 | 缩写 |
| --- | --- |
| 页面标题 | title_页面 |
| 按钮文字 | btn_按钮事件 |
| 标签文字 | label_标签文字 |
| 选项卡文字 | tab_选项卡文字 |
| 消息框文字 | toast_消息 |
| 编辑框的提示文字 | hint_提示信息 |
| 图片的描述文字 | desc_图片文字 |
| 对话框文字 | dialog_文字|
| menu的item文字 | action_文字 |

- String命名的前缀应该能够清楚地表达它的功能职责，如，`registration_email_hint`，`registration_name_hint`

- 如果一个Sting不属于任何模块，这也就意味着它是通用的，应该遵循以下规范：

| Prefix             | Description                           |
| -----------------  | --------------------------------------|
| `error_`           | 错误提示                              |
| `msg_`             | 一般信息提示                          |
| `title_`           | 标题提示，如，Dialog标题              |
| `action_`          | 动作提示，如，“保存”，“取消”，“创建”  |


# 最佳实践

## 编码相关

### 常规

#### 方法函数中的参数排序规范

在Android日常开发中，很多情况下都需要使用 `Context`，所以经常被作为参数传入方法中，这里给出的建议是，如果函数签名中存在 `Context`，则作为第一个参数，如果存在 `Callback` 则作为最后一个参数，示例如下：

```java
public void loadUserAsync(Context context, int userId, UserCallback callback);
```

### Activity Fragment 相关

#### BaseActivity BaseFragment

- 每个 `Activity`，`Fragment` 都要对应继承 `BaseActivity`，`BaseFragment`（放在目录 `com.xx.yy.ui.base` 下）
- `BaseActivity` 统一继承 `support-v7` 中的 `AppCompatActivity`。
- `BaseFragment` 统一继承 `support-v4` 中的 `Fragment`
- 如果项目中引用 `RxJava`，建议继承 [RxLifecycle](https://github.com/trello/RxLifecycle) 中的 `RxAppCompatActivity` 和 `RxFragment`
- Activity `Theme` 统一继承 `Theme.AppCompat[.Light].NoActionBar`


#### 生命周期排序

Activity或者Fragment，重写生命周期函数时，应该按照组件的生命周期进行排序，如：

```java
public class MainActivity extends Activity {

    @Override
    public void onCreate() {}

    @Override
    public void onResume() {}

    @Override
    public void onPause() {}

    @Override
    public void onDestroy() {}
}
```

#### Activity 和 Fragment 打开方式

当通过 `Intent` 或者 `Bundle` 向 `Activity` 与 `Fragment` 传值时，应该遵循上面提到的 `key-value` 规范，公开一个被 `public static` 修饰的方法，方法的参数应该包含所有打开这个 `Activity` 或者 `Fragment` 的信息，示例如下：

- 通过 `.startActivity()` 函数，开启指定 **Activity**。

```java
public static void startActivity(AppCompatActivity startingActivity, User user) {
    Intent intent = new Intent(startingActivity, ThisActivity.class);
    intent.putParcelableExtra(EXTRA_USER, user);
    startingActivity.startActivity(intent);
  }
```

- 通过 `.newInstance()` 函数，加载指定 `Fragment`。

```java
public static UserFragment newInstance(User user) {
  UserFragment fragment = new UserFragment;
  Bundle args = new Bundle();
  args.putParcelable(ARGUMENT_USER, user);
  fragment.setArguments(args)
  return fragment;
}
```

需要注意一下两点：

1. 以上这些方法应该放在类的开头，至少应该放在 `onCreate()` 之前。
1. 如 `EXTRA_USER`，`ARGUMENT_USER` 等常量 `key`，应该放在本类中被`private` 所修饰，不应该暴露给其它外部类。


### Log

#### Log 输出规范

  使用 Log 类打印一些重要的信息对开发者而言是很重要的事情，切记不要使用 Toast 来做信息打印。

  `VERBOSE` 和 `DEBUG` 类型的 Log 不应该出现在 `Release` 版本中，`INFORMATION`、`WARNING` 和 `ERROR` 类型的 Log 可以留下来，因为这些信息的输出能够帮助我们快速地定位问题所在，当然前提是，需要隐藏重要的信息输出，如：用户手机号，邮箱等。

  只在 Debug 环境中输出日志的小技巧：

  > if (BuildConfig.DEBUG) Log.d(TAG, "The value of x is " + x)


### 数据库

- 除非确实有必要，否则不要盲目的引入数据库支持。这一点笔者也是赞同的，很多时候简单的缓存可以用 `SharedReference` 就可以了。不过反过来，如果你真的有一定的需要持久化的数据，不要犹豫，立马引入数据库的支持
- 如果引入了DB支持，那考虑使用 `ORM框架` 的支持，避免重复造轮子
- 关于 `Realm` ，这是一个很炫的东西，但是笔者自己老实说在Android和iOS平台引入之后，发现还是会存在一些问题Abderrazak Laanaya对Realm是持积极态度而Stepan Goncharov是保守态度。笔者自己的感觉是Realm确实很酷，但是一定要做好其引发未知Crash的心理准备

### 其他

- 使用 `AccountManager` 来建议登录名与Email地址等

### 权限相关

## Resource

### XML属性排序

对于如何排版一个布局文件，请尽量遵循以下规范：

- 每个属性独占一行，缩进四个空格
- `android:id` 作为第一个属性存在
- 如果存在 `style` 属性，则紧随 `id` 之后
- 如果不存在 `style` 属性，则 `android:layout_****` 紧随 `id` 之后
- 当布局中的一个元素不再包含子元素时，另起一行，使用自闭合标签 `/>`，方便调整和添加新的属性

示例如下：

```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    >

    <TextView
        android:id="@+id/name"
        style="@style/FancyText"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_alignParentRight="true"
        android:text="@string/name"
        />

    <include layout="@layout/reusable_part" />

</LinearLayout>
```


### Drawable

- 可拉伸，尤其带圆角的图片，都要用 `.9.png` 处理
- 图片尽量分拆成多个可重用的图片
- 多使用 `layer-list` 和 `selector`

### Dimen

- 文字大小的单位统一用 `sp`，元素大小的单位统一用 `dp`

### Anim

- 使用 `animation-list` 制作动画效果

### Color

- 颜色值统一在 `colors.xml` 中定义，然后在代码和布局文件中引用。
- 不要在代码和布局文件中引用系统的颜色，除了透明。

### String

- 应用中的字符串统一在 `strings.xml` 中定义，然后在代码和布局文件中引用
- `strings.xml` 中使用 `%1$s` 实现字符串的通配

### Style

- 使用 `styles`，复用样式定义，来减少布局 XML 中的重复属性
- 值得一提的是，`android:layout_****` 属性应该在XML中定义，同时其它属性 `android:****` 应放在 `style` 中。核心准则是保证`Layout属性` ( position, margin, size等 )和 `content属性` 在布局文件中，同时将所有的外观细节属性（color, padding, font）放在style文件中。

- 另外，在上面提到的准则中，有以下几点需要注意：
  - `android:id` 明显应该在layout文件中
  - Layout文件中的 `android:orientation` 属性对于一个 `LinearLayout` 布局来说，更具有意义
  - 由于使用 `android:text` 定义内容，所以这个属性应该放在Layout文件中
  - 有时候将 `android:layout_width` 和 `android:layout_height` 属性放到一个 `style.xml` 中作为一个通用的风格更有意义，但是默认情况下把这些属性放到Layout文件中比放到 `style.xml` 文件中更加直观。

### Layout

- Layout结构优化方面，应尽量避免深层次的布局嵌套，这不仅会引发性能瓶颈，还会带来项目维护上的麻烦。在书写布局之前应该对ViewTree充分的分析，善用 [`<merge>`标签](http://stackoverflow.com/questions/8834898/what-is-the-purpose-of-androids-merge-tag-in-xml-layouts) 减少层级嵌套，或者使用 [Hierarchy Viewer](http://developer.android.com/intl/zh-cn/tools/help/hierarchy-viewer.html) 等UI优化工具对Layout进行分析与优化。可参考 [Optimizing Your UI](http://developer.android.com/intl/zh-cn/tools/debugging/debugging-ui.html) 与 [Optimizing Layout Hierarchies](http://developer.android.com/intl/zh-cn/training/improving-layouts/optimizing-layout.html)。


### Designtime Attributes（tools 标签）

- 布局预览应使用 `tools:xxx` 相关属性，避免 `android:text` 等硬编码的出现，具体可参考 [Designtime Attributes](http://tools.android.com/tips/layout-designtime-attributes)

  示例如下：

  ```xml
  <TextView
      android:layout_width="wrap_content"
      android:layout_height="wrap_content"
      tools:text="Home Link"
      />
  ```
- 关于`tools:xxx` 相关属性的 [官方介绍](https://developer.android.com/studio/write/tool-attributes.html)

## 开发、构建与测试

### Build

- 现在的应用程序很容易突破 `65K` 的方法数量的限制，`Multidexing` 可以帮你解决这个问题
- 应该按照 `Feature` 打包，而不应该按照 `Layers` 打包
- 开发的时候设置 `minSdkVersion=21`，这样可以加速编译时间，特别是在设置了 `Multidexing` 的时候

### Debug

- 使用 Facebook 的 [Stetho](http://facebook.github.io/stetho/) 来方便调试应用

### Gradle

- 将密码以及其他关键数据放置到 `gradle.properties` 中
- 使用Maven依赖代替jar包导入

  如果在项目中明确使用jar文件，那么它们可能成为永久的版本，如`2.1.1`。而且很容易陷入频繁更新jar包的繁琐工作中，Maven很好的解决了这个问题，这也是 Gradle构建中推荐的方法。你可以指定版本的一个范围，如`2.1.+`,然后Maven会自动升级到制定的最新版本，例如：

  ```groovy
  dependencies {
        /*ReactiveX Library*/
        compile 'io.reactivex:rxjava:1.1.3'
        compile 'io.reactivex:rxandroid:1.1.0'
  }
  ```
- 签名配置

  发布release版本的时候，应该做好 **SigningConfigs** 的保密性：

  不要这样做，这种做法非常的不安全：

  ```groovy
  signingConfigs {
    release {
      storeFile file("myapp.keystore")
      storePassword "storePassword"
      keyAlias "storeKey"
      keyPassword "keyPassword"
    }
  }
  ```
  而是，建立一个不加入版本控制系统的`gradle.properties`文件，或者在本地的`local.properties`中记录。

  ```groovy
  KEYSTORE_PASSWORD=storePassword
  KEY_PASSWORD=keyPassword
  ```

  那个文件会被gradle自动引入，因此可以在`buld.gradle`文件中使用，例如：

  ```groovy
  signingConfigs {
    release {
      try {
        storeFile file("myapp.keystore")
        storePassword KEYSTORE_PASSWORD
        keyAlias "storeKey"
        keyPassword KEY_PASSWORD
      }
      catch (ex) {
        throw new InvalidUserDataException("You should define KEYSTORE_PASSWORD and KEY_PASSWORD in gradle.properties.")
      }
    }
  }
  ```

### Check

- 在CI工具里添加些 [静态的代码分析工具](http://www.sonarqube.org/)

### Log 日志

- Log(系统名称模块名称接口名称，详细描述)
- 使用如下的表达式来过滤日志：
  > ^(?!(NotificationManager|Timeline|SensorManager|Configs|libc-netbsd|art|stetho|Choreographer|CliptrayUtils|BubblePopupHelper|ViewRootImpl|libEGL|System.out|PhoneWindow))

## 组件化

- 将应用分为多个较小灵活地模块中，这样可以尽量保证可维护性较好、耦合度较低的CodeBase，也可以选择将小的模块发布到公开或者私有的仓库中，然后在主项目中引入。

- 引入 `Dagger2` 减少模块之间的耦合性。Dagger2 是一个依赖注入框架，使用代码自动生成创建依赖关系需要的代码。减少很多模板化的代码，更易于测试，降低耦合，创建可复用可互换的模块。参考之前的文章 [Google官方MVP + Dagger2架构详解](http://www.jianshu.com/p/01d3c014b0b1)

### 第三方库

- 使用任何的第三方库之前都要三思而行，从笔者自己的经验里，`抽象漏洞定理` 是一个颠仆不破的定理啊。虽然很多库宣扬的都是非常Nice，Demo也很诱人，但是你压根不知道它到底会带来怎样的 `Side Effect`。笔者是建议如果真的打算应用某个库到正式的大型项目中，一定要好好考量下它的社区和活跃度。以后流的泪，都是当时脑子进的水。
- 引用第三方库要慎重，避免应用大容量的第三方库，导致客户端包非常大。尽量使用那些较小的，往往只是完成单个功能的库，将来比较好替换
- 可以添加多一层 `Lib` 层，用来对大多数第三方库进行一层包裹 `Wrap`，方便日后更换或拓展 （[参考 ImageLoader 的封装](http://www.jianshu.com/p/e26130a93289)）
- 不要使用 Google 的 `Guava`

## 性能优化

### 内存优化

- 尽量避免 `static` 成员变量引用资源耗费过多的实例,比如 `Context`
- 线程也是造成内存泄露的一个重要的源头。线程产生内存泄露的主要原因在于线程生命周期的不可控。
- 使用 `WeakReference` 代替强引用，弱引用可以让您保持对对象的引用，同时允许 GC 在必要时释放对象，回收内存。对于那些创建便宜但耗费大量内存的对象，即希望保持该对象，又要在应用程序需要时使用，同时希望 GC 必要时回收时，可以考虑使用弱引用。
- 保证 `Cursor` 占用的内存被及时的释放掉，而不是等待 GC 来处理。并且 Android 明显是倾向于编程者手动的将 `Cursor` 手动 `close` 掉
- 在应用程序中要注意避免 `Memory Leaks`，不过 `onLowMemory()` 是会在整个系统的内存较低的情况下被触发，因此不能用于避免 OOM

### 图片优化

- 超级大胖子 `Bitmap` 及时的销毁 ( Activity的onDestroy时，将bitmap回收 ) 设置一定的 `采样率`，巧妙的运用软引用 drawable对应resid的资源，bitmap对应其他资源。

### 网络优化

- HTTP 用 `gzip` 压缩，设置连接超时时间和响应超时时间
- HTTP 请求按照业务需求，分为是否可以缓存和不可缓存，那么在无网络的环境中，仍然通过缓存的 HTTP `response` 浏览部分数据，实现离线阅读。
- 不要尝试着重复造轮子，可以使用 `Volley` 或者 `OkHTTP`，可以考虑使用 `Retrofit` 作为上层封装
- 记得监控当前连接类型，在 `WiFi` 下进行较大量的数据更新

### 异步优化

- 使用 `线程池`，分为核心线程池和普通线程池，下载图片等耗时任务放置在普通线程池，避免耗时任务阻塞线程池后，导致所有异步任务都必须等待
- 使用 `RxJava` 来代替 `AsyncTasks`，不过对于 `RetroLambda` 的使用还是持保留意见
- 对于 `EventBus` 的使用持谨慎态度，一不小心就可能把你的程序变得有些杂乱，可以考虑使用 `RxJava + LocalBroadcastManager` 作为替代
- 不要把太多东西塞入到 `Application线程` 中
- 使用 `JobScheduler` 来处理长期周期化运行的无状态任务

### 电量优化

- 系统的30%的电量消耗用在了图片、动画等，而70%用于分析、广告、地图以及GPS

### 序列化

- 使用 `Parcel` 在 Android 中引入 `AutoValue`。
- 尽量少用 `Serializable`：`Serializable` 虽然方便使用，但是效率低下。使用 `Parcel` 或者 `FlatBuffers`（一个高效地跨平台序列化框架）

## UI优化

- 使用 `Lint` 来辅助进行布局与层次优化，这样有助于发现冗余的布局
- `软键盘` 的弹出控制，不要让其覆盖输入框
- `Launch Screen` 是用户看到的第一个画面，要谨慎，不过也不能在没必要的时候强行加入一个Launch Screen
- 使用 [DataBinding](https://developer.android.com/topic/libraries/data-binding/index.html) 来减少UI代码的数目

### 适配优化

- 自适应屏幕，使用 `dp` 替代 `px`
- 使用 `android:layout_weight` 或者 `TableLayout`、`GridLayout`制作等分布局

### 布局优化

- `layout` 组件化，尽量使用 `merge` 及 `include` 复用
- 复杂布局使用 `RelativeLayout`
- 不要使用层次过深的 `ViewGroups` 继承
- 使用 [ConstraintsLayout](http://tools.android.com/tech-docs/layout-editor) 来扁平化视图层次

### ListView 性能优化

- 复用 `convertView`：在 `getItemView` 中，判断 convertView 是否为空，如果不为空，可复用。如果 convertView 中的 view 需要添加 listerner，代码一定要在 `if(convertView == null){}` 之外。
- 异步加载图片 item 中如果包含有 `webimage` ，那么最好异步加载
- 快速滑动时不显示图片，当快速滑动列表时（`SCROLL_STATE_FLING`），item 中的图片或获取需要消耗资源的 view，可以不显示出来；而处于其他两种状态（`SCROLL_STATE_IDLE` 和`SCROLL_STATE_TOUCH_SCROLL`），则将那些view显示出来

### TextView 排版

- 英文文档排版：`textview` 自动换行时要保持单词的完整性，解决方案是计算字符串长度，然后手动设定每一行显示多少个字母并加上‘n‘
- 数字、字母和汉字混排占位问题：将数字和字母全角化。由于现在大多数情况下我们的输入都是半角，所以 字母和数字的占位无法确定，但是一旦全角化之后，数字、字母的占位就和一个汉字的占位相同了，这样就可以避免由于占位导致的排版问题。

### 自定义View

- 应用开发中自定义View的时候，交互部分，千万不要写成线程不断刷新界面显示，而是根据 `TouchListener` 事件主动触发界面的更新

# 参考

## 开发规范

- [ribot/android-guidelines](https://github.com/ribot/android-guidelines)
- [Android Project Guidelines](https://github.com/bufferapp/android-guidelines/blob/master/project_style_guidelines.md)
- [RxSmart/Link-Android-Guideline](https://github.com/RxSmart/Link-Android-Guideline)
- [Android架构系列-开发规范](http://www.jianshu.com/p/c43b558c72b4)
- [Android技术积累: 开发规范](http://keeganlee.me/post/android/20150709)
- [Android进阶之路——安卓编程规范](http://www.jianshu.com/p/fbf9ea4b9d76#rd)
- [Android 编码规范（比较全）](http://www.jianshu.com/p/0a984f999592)
- [Android开发架构规范](http://www.jianshu.com/p/99239b9c1630)
- [数库科技 Android 开发准则](https://zhuanlan.zhihu.com/p/21258353?refer=kotandroid)
- [[干货] Android编程开发规范](http://www.jianshu.com/p/9b8aeca9b281)
- [Android 命名规范 （提高代码可以读性）](http://blog.csdn.net/vipzjyno1/article/details/23542617)

## 最佳实践

- [futurice/android-best-practices](https://github.com/futurice/android-best-practices)
- [2016里一些Android最佳实践列表——Opinionated](https://segmentfault.com/a/1190000005752066)
- [好的Android开发习惯](https://github.com/GeniusVJR/Good-Android-development-habits)