# ptiny.helloworld
=======
##概要 abstract
gradleわかんねー
kotlineもっとわかんねー
今さら新しいこと覚えたくないんじゃーjavaで書かせろ！！
という人のための最小限の変更でhelloworld

##開発環境 setup
wget https://dl.google.com/android/cli/latest/linux_x86_64/install_root.sh
sudo bash ./install_rootsh
export ANDROID_HOME=/opt/android-sdk #お好みで
export PATH=$ANDROID_HOME/platform-tools/:$PATH
sudo mkdir -p $ANDROID_HOME
sudo chown $USER:$USER $ANDROID_HOME -R
android sdk install platform-tools platforms/android-36

##生成 create
###概要
testの消去
kotlinの消去
javaのpackage、layout、theme、dependenciesの変更
###具体例
`
$ android --no-metrics create --min-sdk=21 --application-id=ptiny.helloworld --namespace=ptiny.helloworld --name "Hello World"
$ rm -rf app/src/{androidTest/,test/,main/java/}
$ vi app/build.gradle.kts
dependencies {
  implementation("androidx.appcompat:appcompat:1.6.1")
  implementation("com.google.android.material:material:1.9.0")
  implementation("androidx.constraintlayout:constraintlayout:2.1.4")
}
$ mkdir -p app/src/main/java/ptiny/helloworld/
$ vi app/src/main/java/ptiny/helloworld/MainActivity.java
$ cat app/src/main/java/ptiny/helloworld/MainActivity.java
package ptiny.helloworld;

import androidx.appcompat.app.AppCompatActivity;
import androidx.appcompat.widget.Toolbar;
import android.os.Bundle;

public class MainActivity extends AppCompatActivity {
	
	@Override
	protected void onCreate(Bundle savedInstanceState) {
		super.onCreate(savedInstanceState);
		setContentView(R.layout.activity_main);
	}
}
$ mkdir -p app/src/main/res/layout/
$ vi app/src/main/res/layout/activity_main.xml
$ cat app/src/main/res/layout/activity_main.xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical">

    <androidx.appcompat.widget.Toolbar
        android:id="@+id/toolbar"
        android:layout_width="match_parent"
        android:layout_height="?attr/actionBarSize"
        android:background="?attr/colorPrimary"
        app:title="Hello World" />
    
    <TextView
        android:id="@+id/text"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Hello World!!" />

</LinearLayout>
$ vi app/src/main/res/values/themes.xml
 cat app/src/main/res/values/themes.xml
<?xml version="1.0" encoding="utf-8"?>
<resources>

    <style name="Theme.HelloWorld" parent="Theme.AppCompat.Light.DarkActionBar" />
</resources>
`

##備考
android createはネットワック繋がってないと落ちる！
android --no-metricsしないと統計情報が送られる！！
邪悪、邪悪な企業っすな・・・
俺制作の部分はBSD-2で自動生成部分はgoogleの指定に従ってくれや
let's enjoy!!
