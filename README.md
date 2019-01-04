
## 用Android Studio导入并运行DL注意事项

### 1.请用Android studio 1.0以上版本
### 2.根目录下的脚本是无法运行的，请运行对应子项目
### 3.也可以用命令行运行：
     cd DynamicLoadApk
     gradlew :main-host:build
     
### 4.为了方便上传插件APK到手机，提供了uploadDebug task:
     cd DynamicLoadApk
     gradlew :main-plugin-a:uploadDebug
     
#### 上传路径在根目录下build.gradle修改
    def dlPath = '/sdcard/DynamicLoadHost'

	
### 其他：

如果按照上面的自动上传项目 APK 无法实现，我们可以手动进行实现：

    gradlew :main-plugin-a:build

然后到输出 apk 的目录下面，使用 adb 将 apk 上传到指定的目录即可：

	adb push main-plugin-a-debug.apk /sdcard/DynamicLoadHost

然后重新开宿主 app 就可以看到插件了