#  AndroidReview (Adnroid面试复习) #

## 一、项目简介 ##

为了更好地准备面试Android开发这一职位，于是就到应用市场查找相关的复习App,结果发现只有寥寥无几的几款，而且很不好用，AndroidReview因此而诞生。

AndroidReview是一款面向Android开发者的一款面试复习App，里面包含知识点复习和面试题目测试两大模块。使用者不管在何时何地都可以通过该App复习巩固Android知识点。如果你有比较好的资源(博文或者测试题目)也可以联系我更新到该应用哦。（QQ群在下面^_^）**[APK点我下载](https://github.com/envyfan/AndroidReview/blob/master/apk.apk?raw=true)**

**特点：**
* 知识点归类明细，并且每一篇博文都通过作者阅读后采集进后台，不是简单地采集博文。

* 博文采用了缓存机制，会根据不同网络环境调整缓存存活时间，给使用者一个良好的体验。（缓存策略思路来自OSChina客户端）。

* 随机读取题库题目，保证每次读取题库题目题序都是乱序。

* 提供测试题目收藏，便于使用者随时翻阅感兴趣的题目。

* 对于资料收集者可从Bmob云后台服务动态增删改查任意题目、博文、知识点数据。

## 二、第三方引用 ##

1、[下拉刷新android-Ultra-Pull-To-Refresh](https://github.com/liaohuqiu/android-Ultra-Pull-To-Refresh)

2、[mob移动云服务](http://www.bmob.cn/)

3、[logger调试日志插件](https://github.com/orhanobut/logger)

4、[应用崩溃异常提示crashwoodpecker](https://github.com/drakeet/CrashWoodpecker)

## 三、运行截图 ##

![](https://github.com/envyfan/AndroidReview/blob/master/pic/pics.png?raw=true)

## 四、导入说明 ##

为了避免移动云数据不被删改，所以在上传该项目的时候已经把ApplicationID删除了，如果你想运行该项目，那么需要到Bmob中创建一个应用，并且建立好数据表后把ApplicationID替换到AppContext中即可。
* **Step 1：申请Bmob账号并且创建一个应用**
 该步骤可参考Bmob官方文档：
 http://docs.bmob.cn/android/faststart/index.html?menukey=fast_start&key=start_android

* **Step 2：创建数据表**
一共需要创建Unit(单元)、Point(知识点)、Content(内容)、Test(测试题目)、Suggest(建议)五个表格。进入应用管理界面依次根据下面描述的字段创建好五个表格即可。
![](https://github.com/envyfan/AndroidReview/blob/master/pic/ss.png?raw=true)

1. **Unit表：**
>String name(单元名称)

2. **Point表：**
>Number color(知识点卡片背景颜色)
String name(知识点名称)
Pointer<Unit> (外键)

3. **Content表:**
>String content(内容正文)
Pointer<Point>(外键)
String source(来源)
String title(标题)
String author(作者)
String small(正文简介)

4. **Test表:**
>Number testId(测试题目Id)
Number testType(测试题目类型)
String question(测试题目问题)
String answerA(测试题目选项如果有则填，无则留空)
String answerB(测试题目选项如果有则填，无则留空)
String answerC(测试题目选项如果有则填，无则留空)
String answerD(测试题目选项如果有则填，无则留空)
String answerE(测试题目选项如果有则填，无则留空)
String answerF(测试题目选项如果有则填，无则留空)
String answerG(测试题目选项如果有则填，无则留空)
String answer(正确答案)

5. **Suggest表:**
>String msg(建议正文)
String mail_qq(QQ)

**注意：**
>1、创建表后系统会默认提供objectId、createdAt、updatedAt、ACL字段，这些字段都是Bmob自动创建，不要对它们进行编辑。
2、Pointer类型是Bmob的外键类型，在创建该字段的时候需要主要设置，不要弄错了。
3、表名注意首字母要大写

* **Step 3：替换ApplicationId**

	把com.vv.androidreview.base.system.AppContext下的ApplicationId替换成你在Bmob中创建应用的ApplicationId
```java
@Override
    public void onCreate() {
        super.onCreate();
        instance = this;
        Bmob.initialize(this, "这里换成你的Bmob ApplicationID");
        //初始化Log系统
        Logger.init("MyDemo")               // default PRETTYLOGGER or use just init()
              .setMethodCount(1)            // default 2
              .hideThreadInfo();           // default shown
    }
```
## 五、致谢 ##
知识点复习大部分博文都来自鸿洋、郭林等大神的博客，非常感谢像他们一样的开发者在网上分享自己的技术经验，让我们受益匪浅。另外也非常感谢oschina这个开源项目，在里面我学习到了很多东西，包括基类的封装、使用缓存策略、网络环境判断等等。

## 六、声明 ##
应用中展示的所有内容均搜集自互联网，若内容有侵权请联系作者进行删除处理。本应用仅用作分享与学习，若转载须征得本人同意。
**交流QQ群：206944327**
