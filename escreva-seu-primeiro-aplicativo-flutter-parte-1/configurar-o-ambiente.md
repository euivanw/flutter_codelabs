# 2. Configurar o ambiente

Você irá precisar de dois aplicativos - o [SDK do Flutter](https://flutter.dev/docs/get-started/install) e [um editor](https://flutter.dev/docs/get-started/editor). \(Este laboratório assume que você está utilizando o [Visual Studio Code](https://code.visualstudio.com), mas você pode utilizar qualquer editor de sua preferência.\)

Você pode executar este laboratório utilizando um dos seguintes dispositivos:

* Um dispositivo [Android](https://flutter.dev/docs/get-started/install/macos#set-up-your-android-device) ou [iOS](https://flutter.dev/docs/get-started/install/macos#deploy-to-ios-devices) físico conectado ao seu computador e com o modo de desenvolvedor habilitado
* O [simulador do iOS](https://flutter.dev/docs/get-started/install/macos#set-up-the-ios-simulator) \(requer a instalação do Xcode\)
* O [emulador do Android](https://flutter.dev/docs/get-started/install/macos#set-up-the-android-emulator) \(requer a configuração do Android Studio\)
* Um navegador \(O Chrome é obrigatório para debugar\)

Se você quiser compilar seu aplicativo para executá-lo na web, você deve habilitar esta funcionalidade \(que atualmente está em beta\). Para habilitar o suporte a web, use as seguintes instruções:

```bash
flutter channel beta
flutter upgrade
flutter config --enable-web
```

Você irá precisar executar o comando `flutter config` apenas uma vez. Após habilitado o suporte a web, cada aplicativo Flutter que você criar também irá compilar para web. Na sua IDE, na área de dispositivos ou na linha de comando utilizando `flutter devices` você deve ver agora **Chrome** e **Web server** listados. O dispositivo **Chrome** automaticamente inicia o Chrome. Utilize o dispositivo **Chrome** durante o desenvolvimento e você poderá usar o DevTools, e use o dispositivo **Web server** quando você quiser testar o seu aplicativo em outros navegadores. Para mais informações veja [Construindo uma aplicação web com Flutter](https://flutter.dev/docs/get-started/web) e [Escreva seu primeiro aplicativo Flutter para web](https://flutter.dev/docs/get-started/codelab-web).

