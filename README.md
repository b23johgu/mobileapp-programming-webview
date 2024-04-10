
# Rapport

Appen fick ett nytt namn i res/values/strings.xml
```
    <string name="app_name">CoolSchoolApp</string>
```
Appen fick tillgång till internet i AndroidManifest.xml
```
    <uses-permission android:name="android.permission.INTERNET"/>
```
TextWiew elementet byttes ut till ett Webwiew element i activity_main.xml samt fick ett id; "my_webview".
```
<WebView
        android:id="@+id/my_webview"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="@string/app_name"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/appBarLayout" />
```
Variablen myWebView av typen Webview skapades i MainActivity.java och instansierades i onCreate(). En WebViewClient skapades och kopplades till WebView och möjligheten att köra javascript aktiverades i den.
```
WebView myWebView;
```
```
@Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        Toolbar toolbar = findViewById(R.id.toolbar);
        setSupportActionBar(toolbar);

        myWebView = findViewById(R.id.my_webview);
        myWebView.setWebViewClient(new WebViewClient()); // Do not open in Chrome!
        myWebView.getSettings().setJavaScriptEnabled(true);
```
En html sida för den interna webbsidan skapades.

[Html page](/app/src/main/assets/his.html)

Funktionerna showInternalWebPage() och showExternalWebPage() initierades i MainActivity.java.
```
    public void showExternalWebPage(){
        myWebView.loadUrl("https://his.se");
    }

    public void showInternalWebPage(){
        myWebView.loadUrl("file:///android_asset/his.html");
    }
```
När man klickar på "External/Internal Web Page" i appens dropdownmeny kallas någon av funktionerna beroende på vad man klickat på.
```
        if (id == R.id.action_external_web) {
            showExternalWebPage();
            Log.d("==>","Will display external web page");
            return true;
        }
```
[Screenshot av External Web Page](/screenshots/screenhotexternalwebpage.png)
```

        if (id == R.id.action_internal_web) {
            showInternalWebPage();
            Log.d("==>","Will display internal web page");
            return true;
        }
```
[Screenshot av Internal Web Page](/screenshots/screenshotinternalwebpage.png)
