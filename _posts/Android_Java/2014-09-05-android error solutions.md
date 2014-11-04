---
layout: post
title: android error solutions
category: 游戏技术
tags: android／java
keywords: 
description: 
---


* <div style="color:#F00">Wrong orientation? No orientation specified, and the default is horizontal, yet this layout has multiple children where at least one has layout_width="match_parent"</div>
   在其后加上这个即可：android:orientation="horizontal"
* <div style="color:#F00">Error in an XML file: aborting build.</div>
   原来是<color name=”mycolor”>#7fff00</color>
双引号要改成英文的双引号：\<color name="mycolor">#7fff00\</color>
 
* <div style="color:#F00">自定义控件编译不通过</div>
   <siwi.map.android.ActionBar这一行老是出错，将自定义控件放到R.java文件所在的package中,就可以解决
* <div style="color:#F00">自定义控件无限崩溃</div>
 因为要设置主题，在AndroidManifest.xml中的<application android:theme="@style/Theme.GreenDroid">，崩溃是因为将主题设置为android:theme="@android:style/Theme.NoTitleBar.Fullscreen"
* <div style="color:#F00">百度地图运行时显示error code:162</div>
  原因是工程目录libs/armeabi/下的liblocSDK3.so未加载成功，将liblocSDK3.so加载过来即可。
* <div style="color:#F00">加入actionbarsherlock后Dex Loader：Unable to execute dex: Multiple dex files</div>
  将libs下的jar文件删除。
* <div style="color:#F00">Use View.isInEditMode() in your custom views to skip code when shown in Eclipse</div>
  将错误代码段用
  
      if(!isInEditMode()){
      //造成错误的代码段
      }
   包起来，这样在Eclipse中显示时将跳过此代码段而不再出现错误。
   
* <div style="color:#F00">your content must have a listview whose id attribute is android R.id.list</div>
  往actionbar中添加listview报这个错,在对应的listview的xml中将id修改为android:id="@id/android:list"（自己定义的adapter也是一样的，然后findViewById(android.R.id.list)即可）
原来是用的SherlockListFragment，改成SherlockFragment即可。
* <div style="color:#F00">adb shell总是提示：error:device not found</div>
  原来是adb版本的问题,找到一个包含四个文件的adb，解决。
* <div style="color:#F00">adb遇到此提示opendir failed, Permission denied</div>
  adb的命令行权限是($),获得root权限即可，运行命令->su,若手机root过了,则命令行图标会变成(#)，解决。
* <div style="color:#F00">failed to copy 'sqlite3.exe' to '\system\sqlite3.exe': Read-only file system
</div>
  Android是基于Linux开发的，其所使用的文件系统当然也是Linux内核所能支持的，比如YAFFS或者Ext3等，在这些文件系统里，是没有盘符概念的，而且路径名是使用斜杠“/”来分隔的，这一点，Windows系统和它有着明显的区分：Windows文件系统中有盘符（F:/，C:/），并且路径是用反斜杠“/”来分隔。
因此上面的adb push命令的第二个参数 mnt/sdcard 是不伦不类的表示法，问题就出在这里。
解决办法：
将第二个参数，也就是\system\sqlite3.exe改成/system/sqlite3.exe即可。
这个命令还是很特别的，两个参数面向的平台可以是不同的，因此，如sele果在Linux系统下就不会出现这个问题了.[可参考此页](http://blog.csdn.net/jk0o0/article/details/6440255)
* <div style="color:#F00">java.lang.RuntimeException: Parcelable encountered IOException writing serializable object
</div>
  原因是传递的Parcelable对象里面的对象也要Parcelable或者Serializable
* <div style="color:#F00">android.view.InflateException: Binary XML file line #8: Error inflating class PullDownView
</div>
  在自定义空间要用全路径名,<PullDownView 改成<siwi.map.android.PullDownView即可。
* <div style="color:#F00">AndroidRuntime(5560):   at android.widget.Toast.<init>(Toast.java:94)
</div>
  若一个activity声明周期结束了,但是Toast是放在消息队列尾部执行,所以不知道activity声明周期是否结束了,然后Toast的UI就会直接当掉,所以最好在Toast前加入activity是否结束的判断标志。
* <div style="color:#F00">eclipse svn mkactivity request failed或者eclipse 405 Method Not Allowed
</div>
  URL的http改成https
* <div style="color:#F00">代码混淆时,引入ksoap2-android-assembly-2.4-jar-with-dependencies.jar报错
Proguard returned with error code 1. See console
Note: there were 4 duplicate class definitions.
Warning: library class android.content.res.XmlResourceParser extends or implements program class org.xmlpull.v1.XmlPullParser</div>
  在proguard.cfg中加入此句：
     
      -dontwarn org.xmlpull.v1.XmlPullParser
      -dontwarn org.xmlpull.v1.XmlSerializer
* <div style="color:#F00">subclipse svn提交，报错connection refused by the server
svn: E175002: OPTIONS request failed on '/svn/_Login/res/values'
</div>
  * 找到目录I:\Documents and Settings\Administrator\Application Data\Subversion下的servers文件,在142行([global])加入一行http-proxy-exceptions = 10.*, *.gmcc.net，然后再重新提交。
  * 重启eclipse.	
  * 重新定位资源库的位置。
* <div style="color:#F00">android.content.res.Resources$NotFoundException:String resource ID。出错行是dishNumber.setText(items.get(dish.get_dishID()).get_totalNum());
</div>
  因为值是int,所以报错,转成string即可，dishNumber.setText("" + items.get(dish.get_dishID()).get_totalNum());
* <div style="color:#F00">android.view.ViewRootImpl$CalledFromWrongThreadException: Only the original thread that created a view hierarchy can touch its views.
</div>
  UI更新要放到主线程中,比如adapter.notifyDataSetChanged();
* <div style="color:#F00">Could not find actionbarsherlock.apk!</div>
  在引用了此library的工程下,Project->Properties->Java Build Path->Projects,删除掉actionbarsherlock工程,因为这里是生成apk的地方。
* <div style="color:#F00">close() was never explicitly   called on database 
</div>
  原来是我在程序中new了两次SQLiteOpenHelper,删掉其中一个即可 
* <div style="color:#F00">百度地图定位出错：I/LocTestDemo(9106): error code : 61
</div>
  armeabi/liblocSDK3.so文件未导入进来，导入后clean即可。
* <div style="color:#F00">Execution default-generate-sources of goal com.jayway.maven.plugins.android.generation2:
android-maven-plugin:3.4.1:generate-sources failed: Could not find tool 'aapt'. Please
provide a proper Android SDK directory path as configuration parameter <\sdk><\path>...</path></sdk> in the plugin . As an alternative, you may add the
parameter to commandline: Dandroid.sdk.path=... or set environment variable
ANDROID_HOME. -> [Help 1]
</div>
In the last release of android sdk directory structure has changed. Build tools like aapt or dex has been moved from platform-tools to build-tools directory. 
Support for new directory structure was added in maven-android-plugin version 3.6.0 but you use version 3.4.1. Changing plugin version to 3.6.0 in pom.xml 
must help. Here is snippet from my pom.xml:([reference from this page](http://stackoverflow.com/questions/16927306/could-not-find-tool-aapt-please-provide-proper-android-sdk-directory-path-as-co))

      <plugin>
            <groupId>com.jayway.maven.plugins.android.generation2</groupId>
            <artifactId>android-maven-plugin</artifactId>
            <version>3.6.0</version>
            <configuration>
                <androidManifestFile>src/main/other/AndroidManifest.xml</androidManifestFile>
                <resourceDirectory>src/main/resources</resourceDirectory>
                <sourceDirectory>src/main/java</sourceDirectory>
                <sdk>
                    <platform>17</platform>
                    <path>/opt/android-sdk/</path>
                </sdk>
                <manifest>
                    <debuggable>true</debuggable>
                </manifest>
            </configuration>
            <extensions>true</extensions>
        </plugin>
* <div style="color:#F00">[ERROR]     Unresolveable build extension: Plugin com.dynamicobjx.buildtools:dynamicobjx-build-tools:1.3.1 or one of its dependencies could not be resolved: Could not find artifact com.dynamicobjx.buildtools:dynamicobjx-build-tools:jar:1.3.1 in central (http://repo1.maven.org/maven2) -> [Help 2]
</div>
   Apparently, maven3 started ignoring my repository configs and wasn’t seeing our repo definition of our internal repo. Pulling our buildtools module (via webdav) worked perfectly fine with maven 2 so this was really an unpleasant surprise to us to say the least.
Anyway, we’ve resolved this issue since then (took a few hours =/) and the fix that we had for this was moving the declaration of the module dependency to the declaration of the plugin:

      <plugin>
      <groupId>org.apache.maven.plugins\</groupId>
      <artifactId>maven-checkstyle-plugin\</artifactId>
      <version>2.6\</version>
      <dependencies>
      <dependency>
      <groupId>com.dynamicobjx.buildtools\</groupId>
      <artifactId>dynamicobjx-build-tools\</artifactId>  
      <version>1.3.1\</version>
      </dependency>
      </dependencies>
      </plugin>
And declaring our internal report in pluginRepositories:

      <pluginRepositories>
      <pluginRepository>
      <id>com.myrepo</id>
      <name>My Repo</name>
      <url>http://myrepo.com</url>
      </pluginRepository>
      </pluginRepositories>
Hopefully, this helps out anyone seeing the same errors.[referenced from this page](http://dynamicobjx.com/2011/07/05/maven3-unresolveable-build-extension/)
* <div style="color:#F00">@RequestMapping(value = "Jsp/UsersGroupReader.html", method = RequestMethod.GET, produces = MediaType.APPLICATION_JSON_VALUE)
  Error: The attribute produces is undefined for the annotation type RequestMapping
</div>
  将spring web的版本更新到spring 3.1.0.RELEASE以上即可解决。
* <div style="color:#F00">spring-android-webservice数据传输

      @ElementMap(entry="property", key="key", attribute=true, inline=true)
      private Map<Integer, MOrdersFormItem> _items = new HashMap<Integer, MOrdersFormItem>(); </div>
  改为
  
      @ElementMap(entry="property", key="key", attribute=true, inline=true)
private Map<Integer, MOrdersFormItem> _items; // 不能直接new
* <div style="color:#F00">spring-android-webservice数据传输
</div>
  对于自定义的类不能用@XmlElement(name="state"),只需直接定义set,get即可正常传输。
* <div style="color:#F00">android-spring-webservice服务端
</div>

        @RequestMapping(value = "download_image/{image_info}", method = RequestMethod.GET, headers="Accept=image/jpeg, image/jpg, image/png, image/gif")
          byte[] getPhoto(@PathVariable String image_info/*此变量命名必须和前面的{image_info}一样*/) {
        // image_info
        }
* <div style="color:#F00">java.lang.IllegalArgumentException: Service not registered: siwi.map.android.Home$2@423e76c8
</div>
  bindservice和unbindservice都要用同一个context，比如都用getApplicationContext
* <div style="color:#F00">resulted in 400 (Bad Request); invoking error handler
</div>
  传送的接口类最好用自动生成的constructor和get、set等，（而自动生成的constructor，即使class A未继承任何类,还是会自动生成super(),所以需要去掉。）
* <div style="color:#F00">spring ClassNotFoundException: com.mysql.jdbc.Driver
</div>
在pom.xml中加入此句

      <groupId>mysql</groupId>
      <artifactId>mysql-connector-java</artifactId>
      <version>5.1.6</version>
      </dependency>
* <div style="color:#F00">java.lang.ClassNotFoundException: org.springframework.security.ui.session.HttpSessionEventPublisher spring 2.0.5
</div>
  在3.0.1以上改成了org.springframework.security.web.session.HttpSessionEventPublisher
* <div style="color:#F00">I/O error: failed to connect to /59.51.20.29 (port 8080): connect failed: EHOSTUNREACH (No route to host);
</div>
  请检查网络连接
* <div style="color:#F00">Could not resolve dependencies for project org.springframework.android:spring-android-showcase-server:war:1.0.0.BUILD-SNAPSHOT: Could not find artifact hibernate:hibernate3:jar:3.2.3.GA in springsource-repo<http://repo.springsource.org/release>
</div>
  <http://mvnrepository.com/artifact/org.springframework/spring-orm>
  
      <dependency>
      <groupId>org.springframework</groupId>
      <artifactId>spring-orm</artifactId>
      <version>${org.springframework-version}</version>
      </dependency>
* <div style="color:#F00">The type org.hibernate.LockMode cannot be resolved. It is indirectly referenced from required .class files
</div>
  import org.springframework.orm.hibernate3.support.HibernateDaoSupport;
但没有把 hibernate 包加到项目中；
而在用
this.getHibernateTemplate().update(book);时，内部会用到事务，从而用到
org.hibernate.lockmode这个类。而这个类就放在hibernate jar包中；
所以就出现了上面的错误；<http://hippoppower-sina-com.iteye.com/blog/666010>
* <div style="color:#F00">严重: Servlet.service() for servlet appServlet threw exception
org.hibernate.MappingException: org.hibernate.dialect.MySQLDialect does not support sequences at org.hibernate.dialect.Dialect.getSequenceNextValString(Dialect.java:604)</div>
  WUser.hbm.xml将\<generator class="sequence"/>改为\<generator class="native"/>
* <div style="color:#F00">HttpServletRequest request的request.getReader()读取一次,读取一次后再重复读取一次,第二次读取的便是空的
</div>
----

 
 
 






