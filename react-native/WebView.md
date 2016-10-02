# Implementasi WebView di React Native Mode Release
Apakah Anda menggunakan WebView di React Native? Berjalan dengan baik di mode Debug, namun tidak dapat berjalan di mode Relase? Berikut solusinya. Berikut adalah tutorialnya, dengan asumsi:
- Nama project-nya adalah RNProject
- Lokasi file HTML berada dalam folder web (```RNProject/web```)
- File HTML yang akan digunakan adalah index.html

## Android
Jika Anda belum tahu cara install versi Release untuk Android, maka Anda dapat membaca dari https://facebook.github.io/react-native/docs/signed-apk-android.html . Dan berikut adalah solusinya jika WebView tidak bekerja di mode Release pada Android:
- Buat folder assets dalam folder RNProject/android/app/src/main/
- Copy folder web ke RNProject/android/app/src/main/assets
- Ubah koding Anda dari ```source={require(‘./web/index.html’)}``` ke ```source={{uri: ’file:///android_asset/web/index.html’}}```

## iOS
Jika Anda belum tahu cara install versi Release untuk iOS, maka Anda dapat membaca dari https://facebook.github.io/react-native/docs/running-on-device-ios.html
Dan berikut adalah solusinya jika WebView tidak bekerja di mode Release pada iOS:
- Pastikan Anda sudah menginstall Xcode
- Buka file RNProject/ios/RNProject.xcodeproj , dengan cara double-click
- Buka finder. Lalu drag-and-drop folder web ke RNProject/RNProject di Xcode
- Pilih ```Create folder references```, dan pastikan ```Copy items if needed``` dicentang
- Ubah koding Anda dari ```source={require(‘./web/index.html’)}``` ke ```source={{uri: ’web/index.html’}}```
- Jika Build Failed, maka cobalah hapus folder RNProject/web
