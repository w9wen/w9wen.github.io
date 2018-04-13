---
title: "[Xamarin.Forms] 安裝Media Plugin跨平台存取相機或相簿"
categories: Xamarin Xamarin.Forms Plugin
---

在Xamarin.Forms的Core專案要實現跨平台存取照相機、攝影機或相簿，要安裝設定MediaPlugin，請參考[MediaPlugin by James Montemagno](https://github.com/jamesmontemagno/MediaPlugin)。

### 為各平台建立權限

#### Xamarin.Android
1. 打開專案屬性編輯Android Manifest，將WRITE_EXTERNAL_STORAGE 以及 READ_EXTERNAL_STORAGE打勾，而在Marshmallow上(不是每個API都需要，但Marshmallow使用者眾，就安裝好了)執行時要提示使用者使用Native時，便需要安裝PermissionPlugin，請在方案上按右鍵，使用Nuget管理員安裝在三個專案中，並在Xamarin.Android的MainActivity中override OnRequestPermissionsResult，程式碼如下
  ``` csharp
  public override void OnRequestPermissionsResult(int requestCode, string[] permissions, [GeneratedEnum] Permission[] grantResults)
     {
         base.OnRequestPermissionsResult(requestCode, permissions, grantResults);
         PermissionsImplementation.Current.OnRequestPermissionsResult(requestCode, permissions, grantResults);
     }
  ```
2. 安裝設定CurrentActivity Plugin
  請參考[[Xamarin.Forms] 安裝CurrentActivity Plugin藉以存取Xamarin.Android Activity](/xamarin/xamarin.forms/plugin/install-currentactivity-plugin-access-xamarin-android-activity/)
3. 聲明裝置必須性，在AssemblyInfo.cs加入以下程式碼
 ``` csharp
 [assembly: UsesFeature("android.hardware.camera", Required = false)]
 [assembly: UsesFeature("android.hardware.camera.autofocus", Required = false)]
 ```
4. 為了指定存取檔案資料夾，統一在AndroidManifest.xml的`<application>`進行以下配置

  ``` xml
  <provider android:name="android.support.v4.content.FileProvider"
          android:authorities="${applicationId}.fileprovider"
          android:exported="false"
          android:grantUriPermissions="true">

    <meta-data android:name="android.support.FILE_PROVIDER_PATHS"
                   android:resource="@xml/file_paths"></meta-data>
  </provider>
  ```
還沒完，我累了~~~😫，這是跨平台必經過程嗎?不過，先苦後甘
4.建立一個App存取檔案專屬的路徑，在Resrouces下建立一個名為"xml"的資料夾，底下增加一個名為"file_paths"的xml檔案，內容如下
  ```xml
  <?xml version="1.0" encoding="utf-8" ?>
  <paths xmlns:android="http://schemas.android.com/apk/res/android">
    <external-files-path name="my_images" path="Pictures" />
    <external-files-path name="my_movies" path="Movies" />
  </paths>
  ```
結束....🔚~~~Android

#### Xamarin.iOS
這倒簡單了，就只需要在info.plist增加相機、相簿的權限宣告即可，請參考[New iOS 10 Privacy Permission Settings](https://blog.xamarin.com/new-ios-10-privacy-permission-settings/)。

### 安裝Media Plugin
在方案中幫所有的Xamarin專案安裝Xam.Plugin.Media
  ![install-mediaplugin.01](/images/2018/04/install-mediaplugin-01.png)

### 使用跨平台Plugin存取Native

1. Mdeia.plugin 初始化
  ``` csharp
  await CrossMedia.Current.Initialize();
  ```
2. 檢查相機與相簿模組
  ```csharp
  if (!CrossMedia.Current.IsCameraAvailable || !CrossMedia.Current.IsTakePhotoSupported)
  {
      await DisplayAlert("多媒體模組", "相機或相簿不支援", "確定");
      return;
  }  
  ```
3. 檢查提示使用者開放存取權限
  ```csharp
  if (cameraStatus != PermissionStatus.Granted || storageStatus != PermissionStatus.Granted)
  {
      var results = await CrossPermissions.Current.RequestPermissionsAsync(new[] { Permission.Camera, Permission.Storage });
      cameraStatus = results[Permission.Camera];
      storageStatus = results[Permission.Storage];
  }  
  ```
4. 在存取權限的情況下，取得相機或相簿，詳細設定可以參考Media Plugin的文件
  ```csharp
  if (cameraStatus == PermissionStatus.Granted && storageStatus == PermissionStatus.Granted)
  {
     var file = await CrossMedia.Current.TakePhotoAsync(new StoreCameraMediaOptions
     {
         DefaultCamera = CameraDevice.Front, // Android無法執行
         //AllowCropping = true,
         //SaveToAlbum = true
         //SaveMetaData = true,
         //PhotoSize = PhotoSize.Medium,
         //CompressionQuality = 92
         //Directory = "Sample",
         //Name = "test.jpg"
     });

     //var file = await CrossMedia.Current.PickPhotoAsync(new PickMediaOptions { });

     if (file == null)
         return;

     //await DisplayAlert("File Location", file.Path, "OK");

     ImageShow.Source = ImageSource.FromStream(() =>
     {
         var stream = file.GetStream();
         return stream;
     });
  }
  else
  {
     await DisplayAlert("使用者權限", "無法存取相機或相簿", "確定");
     //On iOS you may want to send your user to the settings screen.
     //CrossPermissions.Current.OpenAppSettings();
  }
  ```

### iOS 看 Android Phone
  ![  install-mediaplugin-04](/images/2018/04/install-mediaplugin-04.PNG)
  ![  install-mediaplugin-05](/images/2018/04/install-mediaplugin-05.PNG)

### Android 看 iPhone
  ![](/images/2018/04/install-mediaplugin-02.png)
  ![install-mediaplugin-02](/images/2018/04/install-mediaplugin-03.png)
