Android小技巧-实用API
====
本文是一篇译文,讲述的是Android开发中遇到的一些好用的小技巧,或者一些实用的API,很多人都知道,但也有人不知道,记录下来,如果能帮助到大家,也是极好的.由于不是严格的博文,所以翻译也不那么严格,有些工具和类我也会经常用,所以我会根据自己的想法去写.有些地方坐在并没有将这个工具的作用讲出来,我会补充上去.

## 正文  ##
1.[UrlQuerySanitizer](http://developer.android.com/reference/android/net/UrlQuerySanitizer.html)——使用这个工具可以方便对 URL 进行检查。

2.[Fragment.setArguments](http://developer.android.com/reference/android/app/Fragment.html#setArguments%28android.os.Bundle%29)——因为在构建 Fragment 的时候不能加参数，所以这是个很好的东西，可以在创建 Fragment 之前设置参数（即使在 configuration 改变的时候仍然会导致销毁/重建）。

3.[DialogFragment.setShowsDialog ()](http://developer.android.com/reference/android/app/DialogFragment.html#setShowsDialog%28boolean%29)—— 这是一个很巧妙的方式，DialogFragment 可以作为正常的 Fragment 显示！这里可以让 Fragment 承担双重任务。我通常在创建 Fragment 的时候把 onCreateView ()和 onCreateDialog ()都加上，就可以创建一个具有双重目的的 Fragment。

4.[FragmentManager.enableDebugLogging ()](http://developer.android.com/reference/android/app/FragmentManager.html#enableDebugLogging%28boolean%29)——在需要观察 Fragment 状态的时候会有帮助。

5.[LocalBroadcastManager](http://developer.android.com/reference/android/support/v4/content/LocalBroadcastManager.html)——这个会比全局的 broadcast 更加安全，简单，快速。像 otto 这样的 Event buses 机制对你的应用场景更加有用。

6.[PhoneNumberUtils.formatNumber ()](http://developer.android.com/reference/android/telephony/PhoneNumberUtils.html#formatNumber%28java.lang.String%29)——顾名思义，这是对数字进行格式化操作的时候用的。

7.[Region.op()](http://developer.android.com/reference/android/graphics/Region.html#op%28android.graphics.Region,%20android.graphics.Region,%20android.graphics.Region.Op%29)——我发现在对比两个渲染之前的区域的时候很实用，如果你有两条路径，那么怎么知道它们是不是会重叠呢？使用这个方法就可以做到。

8.[Application.registerActivityLifecycleCallbacks](http://developer.android.com/reference/android/app/Application.html#registerActivityLifecycleCallbacks%28android.app.Application.ActivityLifecycleCallbacks%29)——虽然缺少官方文档解释，不过我想它就是注册 Activity 的生命周期的一些回调方法（顾名思义），就是一个方便的工具。

9.[versionNameSuffix](http://tools.android.com/tech-docs/new-build-system/user-guide#TOC-Build-Types)——这个 gradle 设置可以让你在基于不同构建类型的 manifest 中修改版本名这个属性，例如，如果需要在在 debug 版本中以”-SNAPSHOT”结尾，那么就可以轻松的看出当前是 debug 版还是 release 版。

10.[CursorJoiner](http://developer.android.com/reference/android/database/CursorJoiner.html)——如果你是只使用一个数据库的话，使用 SQL 中的 join 就可以了，但是如果收到的数据是来自两个独立的 ContentProvider，那么 CursorJoiner 就很实用了。

11.[Genymotion](http://www.genymotion.com/)——一个非常快的 Android 模拟器，本人一直在用。

12.[-nodpi](http://developer.android.com/guide/practices/screens_support.html#qualifiers)——在没有特别定义的情况下，很多修饰符(-mdpi,-hdpi,-xdpi等等)都会默认自动缩放 assets/dimensions，有时候我们需要保持显示一致，这种情况下就可以使用 -nodpi。

13.[BroadcastRecevier.setDebugUnregister (http://developer.android.com/reference/android/content/BroadcastReceiver.html#setDebugUnregister%28boolean%29)——又一个方便的调试工具。

14.[Activity.recreate ()](http://developer.android.com/reference/android/app/Activity.html#recreate%28%29)——强制让 Activity 重建。

15.[PackageManager.checkSignatures ()](http://developer.android.com/reference/android/content/pm/PackageManager.html#checkSignatures%28java.lang.String,%20java.lang.String%29)——如果同时安装了两个 app 的话，可以用这个方法检查。如果不进行签名检查的话，其他人可以轻易通过使用一样的包名来模仿你的 app。

16.[Activity.isChangingConfigurations ()](http://developer.android.com/reference/android/app/Activity.html#isChangingConfigurations%28%29)——如果在 Activity 中 configuration 会经常改变的话，使用这个方法就可以不用手动做保存状态的工作了。

17.[SearchRecentSuggestionsProvider](http://developer.android.com/reference/android/content/SearchRecentSuggestionsProvider.html)——可以创建最近提示效果的 provider，是一个简单快速的方法。

18.[ViewTreeObserver](http://developer.android.com/reference/android/view/ViewTreeObserver.html)——这是一个很棒的工具。可以进入到 VIew 里面，并监控 View 结构的各种状态，通常我都用来做 View 的测量操作（自定义视图中经常用到）。

19.[org.gradle.daemon=true](https://www.timroes.de/2013/09/12/speed-up-gradle/)——这句话可以帮助减少 Gradle 构建的时间，仅在命令行编译的时候用到，因为 Android Studio 已经这样使用了。

20.[DatabaseUtils](http://developer.android.com/reference/android/database/DatabaseUtils.html)——一个包含各种数据库操作的使用工具。

21.[android:weightSum (LinearLayout)](http://developer.android.com/reference/android/widget/LinearLayout.html#attr_android:weightSum)——如果想使用 layout weights，但是却不想填充整个 LinearLayout 的话，就可以用 weightSum 来定义总的 weight 大小。

22.[android:duplicateParentState (View)](http://developer.android.com/reference/android/view/View.html#attr_android:duplicateParentState)——此方法可以使得子 View 可以复制父 View 的状态。比如如果一个 ViewGroup 是可点击的，那么可以用这个方法在它被点击的时候让它的子 View 都改变状态。

23.[android:clipChildren (ViewGroup)](http://developer.android.com/reference/android/view/ViewGroup.html#attr_android:clipChildren)——如果此属性设置为不可用，那么 ViewGroup 的子 View 在绘制的时候会超出它的范围，在做动画的时候需要用到。

24.[android:fillViewport (ScrollView)](http://developer.android.com/reference/android/widget/ScrollView.html#attr_android:fillViewport)——在这片文章中有详细介绍文章链接，可以解决在 ScrollView 中当内容不足的时候填不满屏幕的问题。

25.[android:tileMode (BitmapDrawable)](http://developer.android.com/guide/topics/resources/drawable-resource.html#Bitmap)——可以指定图片使用重复填充的模式。

26.[android:enterFadeDuration/android:exitFadeDuration (Drawables)](http://developer.android.com/reference/android/R.attr.html#exitFadeDuration)——此属性在 Drawable 具有多种状态的时候，可以定义它展示前的淡入淡出效果。

27.[android:scaleType (ImageView)](http://developer.android.com/reference/android/widget/ImageView.html#attr_android:scaleType)——定义在 ImageView 中怎么缩放/剪裁图片，一般用的比较多的是“centerCrop”和“centerInside”。

28.[Merge](http://developer.android.com/training/improving-layouts/reusing-layouts.html#Merge)——此标签可以在另一个布局文件中包含别的布局文件，而不用再新建一个 ViewGroup，对于自定义 ViewGroup 的时候也需要用到；可以通过载入一个带有标签的布局文件来自动定义它的子部件。

29.[AtomicFile](http://developer.android.com/reference/android/util/AtomicFile.html)——通过使用备份文件进行文件的原子化操作。这个知识点之前我也写过，不过最好还是有出一个官方的版本比较好。

30.[ViewDragHelper](https://developer.android.com/reference/android/support/v4/widget/ViewDragHelper.html) ——视图拖动是一个比较复杂的问题。这个类可以帮助解决不少问题。如果你需要一个例子，DrawerLayout就是利用它实现扫滑。Flavient Laurent 还写了一些关于这方面的[优秀文章](http://flavienlaurent.com/blog/2013/08/28/each-navigation-drawer-hides-a-viewdraghelper/)。

31.[PopupWindow](https://developer.android.com/reference/android/widget/PopupWindow.html)——Android到处都在使用PopupWindow ，甚至你都没有意识到（标题导航条ActionBar，自动补全AutoComplete，编辑框错误提醒Edittext Errors）。这个类是创建浮层内容的主要方法。

32.[Actionbar.getThemrContext()](https://developer.android.com/reference/android/app/ActionBar.htmlgetThemedContext%28%29)——导航栏的主题化是很复杂的（不同于Activity其他部分的主题化）。你可以得到一个上下文（Context），用这个上下文创建的自定义组件可以得到正确的主题。

33.[ThumbnailUtils](https://developer.android.com/reference/android/media/ThumbnailUtils.html)——帮助创建缩略图。通常我都是用现有的图片加载库（比如，Picasso 或者 Volley），不过这个ThumbnaiUtils可以创建视频缩略图。译者注：该API从V8才开始支持。

34.[Context.getExternalFilesDir()](https://developer.android.com/reference/android/content/Context.htmlgetExternalFilesDir%28java.lang.String%29)———— 申请了SD卡写权限后，你可以在SD的任何地方写数据，把你的数据写在设计好的合适位置会更加有礼貌。这样数据可以及时被清理，也会有更好的用户体验。此外，Android 4.0 Kitkat中在这个文件夹下写数据是不需要权限的，每个用户有自己的独立的数据存储路径。译者注：该API从V8才开始支持。

35.[SparseArray](https://developer.android.com/reference/android/util/SparseArray.html)——Map的高效优化版本。推荐了解姐妹类SparseBooleanArray、SparseIntArray和SparseLongArray。

36.[PackageManager.setComponentEnabledSetting()](https://developer.android.com/reference/android/content/pm/PackageManager.htmlsetComponentEnabledSetting%28android.content.ComponentName,%20int,%20int%29)——可以用来启动或者禁用程序清单中的组件。对于关闭不需要的功能组件是非常赞的，比如关掉一个当前不用的广播接收器。

37.[SQLiteDatabase.yieldIfContendedSafely()](https://developer.android.com/reference/android/database/sqlite/SQLiteDatabase.htmlyieldIfContendedSafely%28%29)——让你暂时停止一个数据库事务， 这样你可以就不会占用太多的系统资源。

38.[Environment.getExternalStoragePublicDirectory()](https://developer.android.com/reference/android/os/Environment.html#getExternalStoragePublicDirectory%28java.lang.String%29)——还是那句话，用户期望在SD卡上得到统一的用户体验。用这个方法可以获得在用户设备上放置指定类型文件（音乐、图片等）的正确目录。

39.[View.generateViewId()](https://developer.android.com/reference/android/view/View.htmlgenerateViewId%28%29)——每次我都想要推荐动态生成控件的ID。需要注意的是，不要和已经存在的控件ID或者其他已经生成的控件ID重复。

40.[ActivityManager.clearApplicationUserData()](https://developer.android.com/reference/android/app/ActivityManager.htmlclearApplicationUserData%28%29)—— 一键清理你的app产生的用户数据，可能是做用户退出登录功能，有史以来最简单的方式了。

41.[Context.createConfigurationContext()](http://developer.android.com/reference/android/content/Context.htmlcreateConfigurationContext%28android.%E2%80%94%E2%80%94ontent.res.Configuration%29) ——自定义你的配置环境信息。我通常会遇到这样的问题：强制让一部分显示在某个特定的环境下（倒不是我一直这样瞎整，说来话长，你很难理解）。用这个实现起来可以稍微简单一点。

42.[ActivityOptions](http://developer.android.com/reference/android/app/ActivityOptions.html) ——方便的定义两个Activity切换的动画。 使用ActivityOptionsCompat 可以很好解决旧版本的兼容问题。

43.[AdapterViewFlipper.fyiWillBeAdvancedByHostKThx()](http://developer.android.com/reference/android/widget/AdapterViewFlipper.htmlfyiWillBeAdvancedByHostKThx%28%29)——仅仅因为很好玩，没有其他原因。在整个安卓开源项目中（AOSP the Android ——pen Source Project Android开放源代码项目）中还有其他很有意思的东西（比如
[GRAVITY_DEATH_STAR_I](http://developer.android.com/reference/android/hardware/SensorManager.htmlGRAVITY_DEATH_STAR_I)）。不过，都不像这个这样，这个确实有用

44.[ViewParent.requestDisallowInterceptTouchEvent()](http://developer.android.com/reference/android/view/ViewParent.htmlrequestDisallowInterceptTouchEvent%28boolean%29) ——Android系统触摸事件机制大多时候能够默认处理，不过有时候你需要使用这个方法来剥夺父级控件的控制权（顺便说一下，如果你想对Android触摸机制了解更多，这个演讲会令你惊叹不已。）

