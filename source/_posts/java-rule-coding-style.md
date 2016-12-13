---
title: Java 编码规范
date: 2016-12-05 09:58:31
authors:
  - EvanWang
categories:
  - Java
  - Coding Rule
tags:
  - Java
  - Coding Rule
---

# 格式规范

## 文档排版规范

- 文档层面的结构包括：`括号风格`, `缩进`, `列限制`, `换行`, `空格`, `空行`

## 具体结构规范

- 具体结构包括：`枚举`, `变量`, `数组`, `switch`, `注解`, `注释`, `修饰符`

## CodeStyle 配置

- 统一用 [Android Studio CodeStyle 配置](https://djlinkiot.github.io/2016/11/26/android-studio-code-style-check-style/) 来规范所有格式

<!-- more -->

## 注意事项

- 使用快捷键进行代码格式自动化：
  - Windows：`CTRL + ALT + L`
  - Mac：`OPTION + COMMAND + L`
- 范围型的常量用枚举类定义，而不要直接用整型或字符，这样可以减少范围值的有效性检查

# 命名规范

## 包名

- 包名全部小写
- 公司（或个人）项目的域名倒序，“.”分隔，单个包名建议不超过12个字母。
    例如，google的gson项目，包名为 `com.google.gson`
- 连续的单词只是简单地连接起来，不使用下划线
- 在部门内部应该规划好包名的范围，防止产生冲突。部门内部产品使用部门的名称加上模块名称。产品线的产品使用产品的名称加上模块的名称。
  - 格式：
    > com.公司名.产品名.模块名称  
    > com.公司名.部门名称.项目名称
  - 实例：
    > com.djlink.iot.sdk     //djlink iot部门 SDK项目  
    > com.djlink.cloud.order   //djlink 云平台产品 预约模块

## 类名

- 首字母大写的驼峰式（ `UpperCamelCase` ）风格命名
- 类名通常是名词或名词短语，意义完整的英文描述

### 测试类

- 以它要测试的类的名称开始，以 `Test` 结束。
- 示例：
  > `HashTest` 或 `HashIntegrationTest`

### 管理类

- 文件管理、设备管理、用户管理这种具有管理某一类事物的功能的类
- 建议规则：语义名词 + `Manager`
- 示例：
  > 文件管理：`FileManager`，设备管理：`DeviceManager`，用户管理：`UserManager`

### 工具类

- 处理一些特定场景问题的类
- 建议规则：场景名词/动词 + `Util`
- 示例：
  > 下载工具类：`DownloadUtil`，日期工具类：`DateUtil`，字符串处理工具类：`StringUtil`

## 接口名

- 首字母大写的驼峰式（ `UpperCamelCase` ）风格命名
- 接口名称有时可能是形容词或形容词短语
  > 例如 `Runnable`， `Cloneable`
- 如果语义不是很清晰，尽量用 `I` 开头，避免产生歧义

### 回调接口

- 其命名规则：`On + 名称 + Callback`

### 监听接口（观察者模式）

- 其命名规则：`On + 名称 + Listener` 或者 `名称 + Observer`

## 方法名

- 首字母小写的驼峰式（ `lowerCamelCase` ）风格命名
- 方法名通常是动词或动词短语
- 下划线可能出现在JUnit测试方法名称中用以分隔名称的逻辑组件。一个典型的模式是：`test<MethodUnderTest>_<state>`，例如 `testPop_emptyStack`。并不存在唯一正确的方式来命名测试方法。
- 示例： 
  ```Java
  private void calculateRate();
  public void addNewOrder();
  ```
  
### Getter 和 Setter 方法

- 存取私有属性的方法，统一采用 getter 和 setter
- 格式：
  ```Java
  get + 非布尔属性名()
  is + 布尔属性名()
  set + 属性名()
  ```

## 常量名

- 常量名命名模式为 `CONSTANT_CASE`，全部字母大写，用下划线分隔单词。
- 使用 `final static` 修饰
- 示例：
  ```Java
  public final static int MAX_VALUE = 1000;
  public final static String DEFAULT_START_DATE= "2001-12-08";
  ```

## 成员变量

- **非静态非public成员变量** 都以 `字母m` 开头的驼峰式（ `lowerCamelCase` ）风格命名
- **静态成员变量** 都以 `字母s` 开头的驼峰式（ `lowerCamelCase` ）风格命名
- **其他变量** 都以 小写字母 开头的驼峰式（ `lowerCamelCase` ）风格命名
- 引用 **非静态成员变量** 时，使用 `this` 引用。引用 **静态成员变量** 时，使用 `类名` 引用
- 示例：
  ```java
  public class MyClass {
    
    public static final int SOME_CONSTANT = 42; //public constant
    public static int sPublicField;  //public static
    public int publicField;   //public
    private static MyClass sSingleton;  //private static
    int mPackagePrivateField;      //package
    protected int mProtectedField; //protect
    private int mPrivateField;     //protect
   
    public void setPrivateField (int privateField) {
      this.mPrivateField = privateField;
    }

    public void setPublicField (int publicField) {
        MyClass.sPublicField = publicField;
    }
  }
  ```

## 局部变量 / 参数名

- 首字母小写的驼峰式（ `lowerCamelCase` ）风格命名
- 比起其它类型的名称， `参数名` 同 `局部变量名` 可以有更为宽松的缩写
- 虽然缩写更宽松，但还是要避免用 `单字符` 进行命名，除了临时变量和循环变量
- 即使局部变量是 `final` 和不可改变的，也不应该把它示为常量，自然也不能用常量的规则去命名它。

## 泛型变量名

- 范型变量可用以下两种风格之一进行命名：
  - 单个的大写字母，后面可以跟一个数字 (如：`E`, `T`, `X`, `T2`)
  - 以类命名方式，后面加个大写的 `T` (如：`RequestT`, `FooBarT`)

## 建议

- 常用组件类命名以组件名加上组件类型名结尾
  > Application 类型的，命名以 App 结尾 —— MainApp  
Frame 类型的，命名以 Frame 结尾 —— TopFrame  
Panel 类型的，建议命名以 Panel 结尾 —— CreateCircuitPanel  
Bean 类型的，命名以 Bean 结尾 —— DataAccessBean  
EJB 类型，命名以 EJB 结尾 —— DBProxyEJB  
Applet 类型，命名以 Applet 结尾 —— PictureShowApplet


- 函数名/变量名缩写

  如果函数名超过 `15个字母`，可采用以去掉元音字母的方法或者以行业内约定俗成的缩写方式缩写函数名
  > 示例：getCustomerInformation() 改为 getCustomerInfo()

- 准确确定成员函数的访问限定符（public、protect、private）

  非必须使用 `public` 的，请使用 `protect`。非必须使用`protected`，请使用 `private`
  ```Java
  protected void setUserName();
  private void calculateRate();
  ```

- 含有集合意义的属性命名，尽量包含其复数的意义

  > customers, orderItems

## 关于驼峰式命名法（CamelCase）

[驼峰式命名法](https://zh.wikipedia.org/wiki/%E9%A7%9D%E5%B3%B0%E5%BC%8F%E5%A4%A7%E5%B0%8F%E5%AF%AB) 分大驼峰式命名法 (`UpperCamelCase`) 和小驼峰式命名法 (`lowerCamelCase`)。 

有时，我们有不只一种合理的方式将一个英语词组转换成驼峰形式，如缩略语或不寻常的结构(例如 `”IPv6”`或 `”iOS”`)。Google指定了以下的转换方案。

名字从 `散文形式(prose form)` 开始:

1. 把短语转换为 `纯ASCII码`，并且移除任何单引号。例如：”Müller’s algorithm”将变成”Muellers algorithm”。
1. 把这个结果切分成单词，在空格或其它标点符号(通常是连字符)处分割开。
    - 推荐：如果某个单词已经有了常用的驼峰表示形式，按它的组成将它分割开(如”AdWords”将分割成”ad words”)。 需要注意的是”iOS”并不是一个真正的驼峰表示形式，因此该推荐对它并不适用。
1. 现在将所有字母都小写(包括缩写)，然后将单词的第一个字母大写：
    - 每个单词的第一个字母都大写，来得到大驼峰式命名。
    - 除了第一个单词，每个单词的第一个字母都大写，来得到小驼峰式命名。
1. 最后将所有的单词连接起来得到一个标识符。

示例：

```java
Prose form                Correct               Incorrect
------------------------------------------------------------------
"XML HTTP request"        XmlHttpRequest        XMLHTTPRequest
"new customer ID"         newCustomerId         newCustomerID
"inner stopwatch"         innerStopwatch        innerStopWatch
"supports IPv6 on iOS?"   supportsIpv6OnIos     supportsIPv6OnIOS
"YouTube importer"        YouTubeImporter
                          YoutubeImporter* (不推荐)
```

> Note：在英语中，某些带有连字符的单词形式不唯一。例如：`”nonempty”` 和 `”non-empty”` 都是正确的，因此方法名 `checkNonempty` 和`checkNonEmpty` 也都是正确的。

# 注释规范

## 规则

- 注释量：一般情况，源程序有效注释量必须在`20%`左右
- 注释原则：有助于对程序理解，语言必须准确、易懂、简洁

## 包的注释

- 写入一个名为 `package.html` 的说明网页放入当前路径，方便 `JavaDoc` 收集
- 注释内容：简述本包作用（整个项目中的位置）、详细描述本包的内容、产品模块名称和版本、公司版权
- 格式：

    ```html
    <html>
        <body>
            <p>一句话描述
            <p>详细描述
            <p>产品模块名称和版本
            <br>公司版权信息
        </body>
    </html>
    ```
- 示例：com/djlink/iot/sdk/cmd/package.html

    ```html
    <html>
        <body>
            <p>SDK中发送指令功能类，上层业务使用本包与设备发指令
            <p>采用xxx设计思路
            <p>MMSC v1.2.1
            <br>(C) 版权所有 200x-200y 北京鼎甲微联科技有限公司
        </body>
    </html>
    ```

## 文件注释

- 注释位置：写入文件头部，包名之前的位置
- 注意以 `/*` 开始避免变 `JavaDoc` 收集
    ```java
    /*
     *  注释内容
     */

    package com.djlink.iot.sdk.cmd;
    ```
- 文件注释内容：描述信息、创建日期、创建人、修改日期、修改人、版权说明 (可选)
    ```java
    /*
     *  版权：Copyright xxx. All Rights Reserved.
     *  描述：<描述该文件功能>
     *  创建人：<修改人名 邮箱>
     *  创建时间：yyyy-MM-dd
     *  修改人：<修改人名 邮箱>
     *  修改时间：yyyy-MM-dd
     *  修改内容：<修改内容>
     */
    ```
    每次修改后在文件头部写明修改信息。
    ```Java
    /*
     *  版权：Copyright xxx. All Rights Reserved.
     *  描述：<描述该文件功能>
     *  创建人：<修改人名 邮箱>
     *  创建时间：yyyy-MM-dd
     *  修改人：<修改人名x 邮箱>
     *  修改时间：yyyy-MM-dd
     *  修改内容：<修改内容x>
     *  修改人：<修改人名y 邮箱>
     *  修改时间：yyyy-MM-dd
     *  修改内容：<修改内容y>
     */
    ```

## 类和接口的注释

- 注释位置：该注释放在 `package` 关键字之后，`class` 或者 `interface` 关键字之前。方便 `JavaDoc` 收集。
    ```java
    package com.djlink.iot.sdk.cmd;

    /**
     *  注释内容
     */
    public class CommandManager
    ```
- 注释内容：类的注释主要是一句话功能简述、功能详细描述。
  > 说明：可根据需要列出: 版本号、生成日期、作者、内容、功能、与其它类的关系等。如果一个类存在BUG，请如实说明这些BUG。
  ```java
    /**
     * （一句话功能简述）
     * （功能详细描述）
     *  @author [作者]
     *  @version [版本号，YYYY-MM-DD]
     *  @see [相关类/方法]
     *  @since [产品/模块版本]
     *  @deprecated
     */
    ```
  > 说明：可根据需要列出: 版本号、生成日期、作者、内容、功能、与其它类的关系等。如果一个类存在BUG，请如实说明这些BUG。
  ```java
    /**
     *  版权：Copyright xxx. All Rights Reserved.
     *  描述：<描述该文件功能>
     *  创建人：<修改人名 邮箱>
     *  创建时间：yyyy-MM-dd
     *  修改人：<修改人名 邮箱>
     *  修改时间：yyyy-MM-dd
     *  修改内容：<修改内容>
     */
    ```

## 成员变量和方法的注释

- 注释位置：写在类属性、公有和保护方法上面。
  ```java
  /**
   *  注释内容
   */
  private String logType;

  /**
   *  注释内容
   */
  public void write();
  ```
- 成员变量注释内容：成员变量的意义、目的、功能，可能被用到的地方。
- 成员方法（public & protected）注释内容：  
  列出方法的一句话功能简述、功能详细描述、输入参数、输出参数、返回值、违例等。
  - 格式：
  ```java
    /**
     * （一句话功能简述）
     * （功能详细描述）
     *  @param [参数1] [参数1说明]
     *  @param [参数2] [参数2说明]
     *  @return [返回类型说明]
     *  @exception/throws [违例类型][违例说明]
     *  @see [类、类#方法、类#成员]
     *  @deprecated
     */
    ```
  > 说明：@since 表示从哪个版本开始就有这个方法；  
  @exception 或 throws 列出可能仍出的异常；  
  @deprecated 表示不建议使用该方法

  - 示例：
  ```java
    /**
     *  根据日志类型和时间读取日志。
     *
     *  分配对应日志类型的 LogReader，指定类型、查询时间段、条件和反复器缓冲数，读取日志记录。
     *  查询条件为 null 或 0 表示无限制，反复器缓冲数为 0 读不到日志
     *  查询时间为左包含原则，即 [startTime, endTime]
     *
     *  @param logTypeName 日志类型名（在配置文件中定义）
     *  @param startTime 查询日志的开始时间
     *  @param endTime 查询日志的结束时间
     *  @param logLevel 查询日志的级别
     *  @param userName 查询该用户的日志
     *  @param bufferNum 日志反复器缓冲记录数
     *  @return 结果集，日志反复器
     *  @since CommonLog1.0
     */
    ```
- 对于方法内部用 `throw 语句` 抛出的异常，必须在方法的注释中标明。  
对于所调用的其他方法所抛出的异常，选择主要的在注释中说明。  
对于`非 RuntimeException`，即throws子句声明会抛出异常，**必须** 在方法的注释中标明。
  > 说明：异常注释用 `@exception` 或 `@throws` 表示，在 `JavaDoc` 中两者等价，但推荐用 `@exception` 标注 `Runtime` 异常。`@throws`标注 `非Runtime` 异常。异常的注释必须说明该异常的含义及什么条件下抛出该异常。

## 代码中的注释

- 注释应与其描述的代码相近，对代码的注释应放在其上方或右方（对单条语句的注释）相邻位置，不可放在下面，如放于上方则需与其上面的代码用空行隔开。
- 注释与所描述内容进行同样的缩排
  > 说明：可使程序排版整齐，并方便注释的阅读与理解
  ```java
  public void example() {
  //注释
    CodeBlock One

      //注释
    CodeBlock One
  }
  ```
  > 应该为如下布局：
  ```java
  public void example() {
    //注释
    CodeBlock One

    //注释
    CodeBlock One
  }
  ```

- 注释与其上面的代码用空行隔开
  > 示例：如下例子，显得代码过于紧凑
  ```java
  //注释
  code one
  //注释
  code two
  ```
  > 应如下书写
  ```java
  //注释
  code one

  //注释
  code two
  ```

- 对 `变量的定义` 和 `分支语句`（条件分支、循环语句等）必须编写注释
  > 说明：这些语句往往是程序实现某一特定功能的关键，对于维护人员来说，良好的注释帮助更好的理解程序，有时甚至优于看设计文档

- 若覆盖基类的方法，则可以不写方法注释，但必须用@Override标出，例如：
  ```java
  @Override
  protected void onCreate(Bundle savedInstanceState) {}
  ```

- `switch … case` 的每个条件，如果没有用明确语义的 `enum` 或者 `string`，需要添加简短说明，例如：
  ```java
  switch (type) {
  case 1:// Android apps
        break;
  case 2:// Android games
        break;
  case 3:// iOS apps
        break;
  default:// Not a valid package
        break;
  }
  ```

- 对于 `switch` 语句下的 `case` 语句，如果因为特殊情况需要处理完一个 `case` 后进入下一个 `case` 处理，必须在该 `case` 语句处理完，下一个 `case` 语句前加上明确的注释。
  ```java
  switch (type) {
  case 1:   // Android apps
      // 再进入下一个case处理
  case 2:   // iOS apps
        break;
  default:
        break;
  }
  ```
  
- 边写代码边注释，修改代码同时修改相应的注释，以保证注释与代码的一致性。不再有用的注释要删除。

- 注释的内容要清楚、明了，含义准确，防止注释二义性
  > 错误的注释不但无益，反而有害

- 避免在注释中使用缩写，特别是不常用的缩写
  > 在使用缩写时或之前，应对缩写进行必要的说明

- 对于未完成的方法，使用TODO加以标记，例如：
  ```java
  void write(byte[] buf, File file) {
    // TODO: Write buf to file
  }
  ```

- 若代码存在严重问题或仅用于调试，使用 `FIXME` 加以标记（注：存在 `FIXME` 标记的代码不能作为正式版发布）
  ```java
  boolean login(String name, String pwd) {
        //FIXME: Remove this line before publishing
        System.out.println("name=" + name + ", password=" + pwd);
        if (users.containsKey(name) && users.get(name).equals(pwd))
        return true;
        return false;
    }
  ```

## 建议

- 快速生成注释的快捷键：( IntelliJ / Eclipse )
  > Mac: `⌥ + ⌘ + J`  
  > Windows/Linux: `Ctrl + Alt + J`
- 避免在一行代码或表达式的中间插入注释
  > 除非必要，不应在代码或表达中间插入注释，否则容易使代码可理解性变差。
- 通过对函数或过程、变量、结构等正确的命名以及合理地组织代码的结构，使代码成为自注释的
  > 清晰准确的函数、变量等的命名，可增加代码可读性，并减少不必要的注释。
- 在代码的功能、意图层次上进行注释，提供有用、额外的信息。
  > 注释的目的是解释代码的目的、功能和采用的方法，提供代码以外的信息，帮助读者理解代码，防止没必要的重复注释信息。

- 在程序块的结束行右方加注释标记，以表明某程序块的结束。
  > 当代码段较长，特别是多重嵌套时，这样做可以是代码更清晰，更便于阅读。
  - 示例：参见如下例子
  ```java
  if (...) {
    code1

    while(index < MAX_INDEX) {
      code2
    } //end of while (index < MAX_INDEX)  // 指明该条 while 语句结束
  } //end of if (...)    // 指明是哪条 if 语句结束
  ```

- 注释应该考虑程序易读及外观排版的因素，使用的语言若是中、英兼有的，建议多使用中文，除非能用非常流利准确的英语表达。
  > 注释语言不统一，影响程序易读性和外观排版，处于维护的考虑，建议使用中文

- 方法内的单行注释使用 `//`
  > 调试程序的时候可以方便的使用 `/* ... */` 注释掉一长段程序

- 注释尽量使用中文注释和中文标点。方法和类描述的第一句话尽量使用简洁明了的话概况以下功能，然后加以句号。接下来的部分可以详细描述。
  > JavaDoc 工具收集简介的时候使用选取第一句话

- 顺序实现流程的说明使用 `1、2、3、4` 在每个实现步骤部分的代码前面进行注释。
  > 示例：如下是对设置属性的流程注释
  ```java
    //1. 判断输入参数是否有效
    ...
    //2. 设置本地变量
    ...
  ```

- 一些复杂的 `代码` 和 `算法` 需要说明
  > 示例：对闰年算法的说明
  ```java
    //1. 如果能被4整除，是闰年
    //2. 如果能被100整除，不是闰年
    //3. 如果能被400整除，是闰年
  ```

# 编码规范

## 规则

- 方法功能明确 —— 精确（而不是近似）地实现方法设计。一个函数仅完成一件功能，即使简单功能也应该编写方法实现。
  > 虽然为仅用一两行就可完成的功能去编方法好像没有必要，但用方法可使功能明确化，增加程序的可读性，亦可方便维护、测试。

- 类功能明确 —— 精确（而非近似）地实现类的设计。一个类仅实现一组相近的功能。
  > 划分类的时候，应该尽量把逻辑处理、数据和显示分离，实现类功能的单一性。

- 参数合法性检查 —— 规定对接口方法参数的合法性检查应由方法的调用者负责还是由接口方法本身负责，缺省是 `由方法调用者负责`。
  > 对于模块间接口方法的参数的合法性检查这一问题，往往有两个极端现象，即：要么是调用者和被调用者对参数均不作合法性检查，结果就遗漏了合法性检查这一必要的处理过程，造成问题隐患。要么就是调用者和被调用者均对参数进行合法性检查，这种情况虽然不会造成问题，但产生了冗余代码，降低了效率。

- 类成员排序规范

  关于这个并没有硬性要求，不过好的排序方式，能够提高可读性和易学性。这里给出一些排序建议：
  
> 1. 常量
> 1. 字段
> 1. 构造函数
> 1. 被重写的函数（不区分修饰符类型）
> 1. 被 private 修饰的函数
> 1. 被 public 修饰的函数
> 1. 被定义的内部类或者接口



- 所有的数据类必须重载 `toString()` 方法，返回该类有意义的内容。方便调试与日志打印。
  > 父类如果实现了比较合理的 `toString()`，子类可以继承不必再重写。
  ```java
  public TopoNode {
    private String nodeName;
    
    public String toString() {
      return "NodeName: " + nodeName;
    }
  }
  ```

- 注解使用规范

  - `@Override`： 子类实现或者重写父类方法时，必须使用`@Override`对函数进行标注。
  - `@SuppressWarnings`： 注解`@SuppressWarnings`应该用在消除那些明确不可能发生的警告上，示例如下：

  ```java
  //明确的类型安全（type-safe）转换
  @SuppressWarnings("unchecked")
  public static <R> FeedbackUseCase<R> createdUseCase() {
      return (FeedbackUseCase<R>) new FeedbackUseCase();
  }

  //请先确保能够非常正确地使用Handler
  @SuppressWarnings("handlerLeak")
  private Handler mHandler = new Handler() {
      @Override
      public void handleMessage(Message msg) {
          super.handleMessage(msg);
      }
  };
  ```
  更多关于注解的使用技巧与规范请参考[这里](http://source.android.com/source/code-style.html#use-standard-java-annotations)。


- 数组声明的时候使用 `int[] index`，而不要使用 `int index[]`
  > 使用 `int index[]` 格式使程序的可读性较差
  >
  > 如下程序可读性差：
  ```java
  public int getIndex() [] {
      ...
  }
  ```
  > 如下程序可读性好：
  ```java
  public int[] getIndex() {
      ...
  }
  ```
- 注意运算符的优先级，并用括号明确表达式的操作顺序，避免使用默认优先级。
  > 防止阅读程序时产生误解，防止因默认的优先级与设计思想不符而导致程序出错。
  
- 避免使用不易理解的数字，用有意义的标识来替代。涉及物理状态或者含有物理意义的常量，不应直接使用数字，必须用有意义的静态变量来代替。
  > 示例：如下的程序可读性差
  ```java
  if (state == 0) {
      state = 1;
      //... 
  }
  ```
  > 应改为如下形式:
  ```java
  private final static int TRUNK_IDLE = 0;
  private final static int TRUNK_BUSY = 1;
  private final static int TRUNK_UNKNOWN = -1;

  if (state == TRUNK_IDLE) {
      state = TRUNK_BUSY;
      //... 
  }
  ```
  
- 数据库操作、IO操作等需要使用结束 `close()` 的对象必须在 `try - catch - finally` 的 `finally` 中调用 `close()`

  ```java
  try {
      //... ...
  } catch (IOException ioe) {
      //... ...
  } finally {
      try {
          out.close();
      } catch (IOException ioe) {
          //... ...
      }
  }
  ```


- 异常捕获后，如果不对该异常进行处理，则应该记录日志或者 `ex.printStackTrace()`
  
  ```java
  try {
      //... ...
  } catch (IOException ioe) {
      ioe.printStackTrace();
  }
  ```
  
- 自己抛出的异常必须要填写详细的描述信息，便于问题定位。
  
  ```java
  throw new IOException("Writing data error! Data: " + data.toString());
  ```

- 运行期异常使用 `RuntimeException` 的子类来表示，不用在可能抛出异常的方法声明上加 `throws` 子句。非运行期异常是从 `Exception` 继承而来，必须在方法声明上加 `throws` 子句。
  
- 在程序中使用异常处理还是使用错误返回码处理，根据是否有利于程序结构来确定，并且异常和错误码不应混合使用，**推荐使用异常**。
  > 一个系统或者模块应该统一规划异常类型和返回码的含义。  
  >
  > 但是不能用异常来做一般流程的方式，**不要过多地使用异常**，异常的处理效率比条件分支低，而且异常的跳转流程难以预测。
 
## 建议

- `@Override` 能用则用。只要是合法的，就把 `@Override` 注解给用上。

- 记录异常不要保存 exception.getMessgae()，而要记录 exception.toString()
  > NullPointException 抛出异常时常常描述为空，这样往往看不出是出了什么错。
  
- 一个方法不应抛出太多类型的异常
  > 如果程序中需要分类处理，则将异常根据分类组织成继承关系。如果确实有很多异常类型首先考虑用异常描述来区别，`throws/exception` 子句标明的异常最好不要超过三个

- 异常捕获尽量不要直接 `catch(Exception ex)`，应该把异常细分处理。
  
- 如果多段代码重复做同一件事情，那么在方法的划分上可能存在问题
  > 若此段代码各语句之间有实质性关联并且是完成同一件功能的，那么可考虑把此段代码构造成一个新的方法。

- 集合中的数据如果不适用了应该及时释放，尤其是可重复使用的集合。
  > 由于集合保存了对象的句柄，虚拟机的垃圾收集器就不会回收。
  
- 源程序中关系较为紧密的代码应尽可能相邻
  > 便于程序阅读和查找。

- 不要使用难懂的技巧性很高的语句，除非很有必要时
  > 高技巧语句不等于高效率的程序，实际上程序的效率关键在于算法。
  

# 参考

- [Google Java编程风格指南](http://www.hawstein.com/posts/google-java-style.html)
- [华为java编程规范](http://wenku.baidu.com/link?url=VdW3Q-oxZZGwr_CQzyZnjdNyNlez5IbAAIPpu8448rM8_FyDWKECTjlKrj5cuX3DANoCRQC2Ge8opkHXafBIy4v8fyll4GQDKLMbsGORwAq)
- [Android-Open-Source-Project Code Style](https://source.android.com/source/code-style.html)
   （[中文版](http://blog.sina.com.cn/s/blog_48d491300100zwzg.html#use-todo-comments)）