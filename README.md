# ptiny.helloworld<br>
=======<br>
## 概要 abstract<br>
gradleわかんねー<br>
kotlineもっとわかんねー<br>
今さら新しいこと覚えたくないんじゃーjavaで書かせろ！！<br>
という人のための最小限の変更でhelloworld<br>
<br>
## 開発環境 setup<br>
wget https://dl.google.com/android/cli/latest/linux_x86_64/install_root.sh<br>
sudo bash ./install_rootsh<br>
export ANDROID_HOME=/opt/android-sdk #お好みで<br>
export PATH=$ANDROID_HOME/platform-tools/:$PATH<br>
sudo mkdir -p $ANDROID_HOME<br>
sudo chown $USER:$USER $ANDROID_HOME -R<br>
android sdk install platform-tools platforms/android-36<br>
<br>
## 生成 create<br>
### 概要<br>
testの消去<br>
kotlinの消去<br>
javaのpackage、layout、theme、dependenciesの変更<br>
### 具体例<br>
`<br>
$ android --no-metrics create --min-sdk=21 --application-id=ptiny.helloworld --namespace=ptiny.helloworld --name "Hello World"<br>
$ rm -rf app/src/{androidTest/,test/,main/java/}<br>
$ vi app/build.gradle.kts<br>
dependencies {<br>
  implementation("androidx.appcompat:appcompat:1.6.1")<br>
  implementation("com.google.android.material:material:1.9.0")<br>
  implementation("androidx.constraintlayout:constraintlayout:2.1.4")<br>
}<br>
$ mkdir -p app/src/main/java/ptiny/helloworld/<br>
$ vi app/src/main/java/ptiny/helloworld/MainActivity.java<br>
$ cat app/src/main/java/ptiny/helloworld/MainActivity.java<br>
package ptiny.helloworld;<br>
<br>
import androidx.appcompat.app.AppCompatActivity;<br>
import androidx.appcompat.widget.Toolbar;<br>
import android.os.Bundle;<br>
<br>
public class MainActivity extends AppCompatActivity {<br>
	<br>
	@Override<br>
	protected void onCreate(Bundle savedInstanceState) {<br>
		super.onCreate(savedInstanceState);<br>
		setContentView(R.layout.activity_main);<br>
	}<br>
}<br>
$ mkdir -p app/src/main/res/layout/<br>
$ vi app/src/main/res/layout/activity_main.xml<br>
$ cat app/src/main/res/layout/activity_main.xml<br>
<?xml version="1.0" encoding="utf-8"?><br>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"<br>
    xmlns:app="http://schemas.android.com/apk/res-auto"<br>
    android:layout_width="match_parent"<br>
    android:layout_height="match_parent"<br>
    android:orientation="vertical"><br>
<br>
    <androidx.appcompat.widget.Toolbar<br>
        android:id="@+id/toolbar"<br>
        android:layout_width="match_parent"<br>
        android:layout_height="?attr/actionBarSize"<br>
        android:background="?attr/colorPrimary"<br>
        app:title="Hello World" /><br>
    <br>
    <TextView<br>
        android:id="@+id/text"<br>
        android:layout_width="wrap_content"<br>
        android:layout_height="wrap_content"<br>
        android:text="Hello World!!" /><br>
<br>
</LinearLayout><br>
$ vi app/src/main/res/values/themes.xml<br>
 cat app/src/main/res/values/themes.xml<br>
<?xml version="1.0" encoding="utf-8"?><br>
<resources><br>
<br>
    <style name="Theme.HelloWorld" parent="Theme.AppCompat.Light.DarkActionBar" /><br>
</resources><br>
`<br>
<br>
## 備考<br>
android createはネットワック繋がってないと落ちる！<br>
android --no-metricsしないと統計情報が送られる！！<br>
邪悪、邪悪な企業っすな・・・<br>
俺制作の部分はBSD-2で自動生成部分はgoogleの指定に従ってくれや<br>
let's enjoy!!<br>
