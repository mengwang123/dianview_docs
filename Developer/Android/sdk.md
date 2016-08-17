# 点乐视频广告SDK对接文档

###接入说明

a.本SDK支持android 2.3及以上

b.如果有接入需求或对我们SDK感兴趣，请联系dev.support@dianview.com

### 集成SDK流程

###1.获取SDK
在DianView官网(http://www.dianview.com)注册开发者账号，成功注册账号后可下载DianView视频广告SDK
###2. 接入SDK
####2.1 使用Android Studio 导入SDK

a. 将<font color=red>videolibrary-release.arr</font>文件和<font color=red>libvideolibrary.so</font>文件复制到您工程的libs目录中

b.在build.gradle中compile申明（详情参考demo中build.gradle配置）
   
    repositories {
      flatDir {
         dirs 'libs'
       }
     }


    dependencies {
      compile(name: 'videolibrary-release', ext: 'aar')
      compile 'com.android.support:support-v4:24.0.0'
    }

c.在AndroidManifest.xml注册相应的组件以及权限(详情请参考demo)
  
  组件注册：

        <service android:name="com.dianjoy.video.DianViewService" android:process=":playgame" />
        
        <activity
            android:name="com.dianjoy.video.DianViewActivity"
            android:launchMode="singleTask"
            android:screenOrientation="landscape"
            android:configChanges="keyboardHidden|orientation"/>

  权限注册：

    <uses-permission android:name="android.permission.INTERNET" />
    <uses-permission android:name="android.permission.GET_TASKS" />
    <uses-permission android:name="android.permission.READ_PHONE_STATE" />
    <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
    <uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
    <uses-permission android:name="android.permission.ACCESS_WIFI_STATE" />
    <uses-permission android:name="android.permission.CHANGE_NETWORK_STATE" />

####2.2 接口说明

 a.初始化接口(详情请参考demo)：
   
    /**
     * 初始化接口
     * @param mContext     上下文
     * @param app_id       DianView开发者平台(http://www.dianview.com/)获取app_id
     * @param channel_id   渠道号（可传空）
     * @param callback     DianViewListener
     */
    public static void init(Context,mContext, String app_id,String channel_id,DianViewListener callback)

    说明:请在应用启动的时候调用此接口



b.查看是否有可以播放的视频(详情请参考demo)：
   
    /**
     * 是否有视频可以播放
     * @param mContext      上下文
     * @param placement_id  广告位id
     * @return   true：有可以播放视频 ,false:没有可以播放视频
     */
    public static boolean canShow(Context mContext, String placement_id)

e.播放视频（详情请参考demo）
   
     /**
     * 视频播放
     * @param mContext
     * @param placement_id   广告位Id
     * @param type           横屏或者竖屏播放   ScreenOrientationTpye.PORTRAIT(竖屏播放),ScreenOrientationTpye.LANDSCAPE（横屏播放）,ScreenOrientationTpye.AUTO(自适应)
     * @param playListener   视频播放回调
     */
    public static void play(Context mContext, String placement_id,ScreenOrientationTpye type,DianViewVideoPlayListener playListener)


f.视频播放回调接口(DianViewVideoPlayListener)
    
    /**
     * 视频播放成功
     */
    public abstract void onVideoPlaySuccess();

    /**
     * 视频播放中用户主动跳过
     */
    public abstract void onVideoPlaySkip();

    /**
     *视频播放失败
     */
    public abstract void onVideoPlayFail();

     /**
     * 视频奖励成功
     */
    public abstract void onVideoPlayAwardSuccess();
    /**
     * 视频奖励失败
     */
    public abstract void onVideoPlayAwardFail();


####2.3 使用Eclipse 导入SDK

a.将<font color=red>videolibrary-release.jar、android-support-v4.jar</font>文件和<font color=red>libvideolibrary.so</font>文件复制到您工程的libs目录中并且导入library工程（开发时需要设置library工程作为依赖）

b.组件以及权限注册同上

c.接口调用同上

###3.混淆配置
  
    -dontwarn com.dianjoy.video.**
    -keep class **.R$* { *;  }
    -keep class com.dianjoy.video.**{*;} 

###4.注意事项
 
<font color=red>注意事项：对接完成后，请测试完整流程：初始化-->视频播放-->广告下载，以确保以上流程可以正确运行</font>



  


