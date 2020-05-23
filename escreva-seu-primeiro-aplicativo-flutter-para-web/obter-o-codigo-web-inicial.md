# 2. Obter o código web inicial

Você vai começar com um aplicativo web simples que iremos fornecer a você.

### 1. Ativar o desenvolvimento web

Na linha de comando, cole os comandos a seguinte para garantir que você tem o último suporte web e que ele está habilitado. Você só precisa executar o comando `flutter config` uma vez para ativar o suporte web no Flutter. Se ver a mensagem "_flutter: command not found_", então você precisa verificar que tem o [Flutter SDK](https://flutter.dev/docs/get-started/install) instalado e que ele está configurado no `PATH` do seu sistema operacional.

```bash
$ flutter channel beta
$ flutter upgrade
$ flutter config --enable-web
```

Se você tiver problemas ao habilitar o desenvolvimento web, consulte o artigo [Construindo uma aplicação web com Flutter](https://flutter.dev/docs/get-started/web).

### 2. Execute o `flutter doctor`

O comando `flutter doctor` informa o estado da instalação. Você deveria ver algo parecido com o conteúdo abaixo:

```bash
$ flutter doctor

[✓] Flutter: is fully installed. (Channel dev, v1.9.5, on Mac OS X 10.14.6 18G87, locale en-US)
[✗] Android toolchain - develop for Android devices: is not installed.
[✗] Xcode - develop for iOS and macOS: is not installed.
[✓] Chrome - develop for the web: is fully installed.
[!] Android Studio: is not available. (not installed)
[✓] Connected device: is fully installed. (1 available)
```

Não tem problemas se o Android toolchain, Android Studio e as ferramentas do Xcode não tiverem instaladas, pois, nosso aplicativo tem a intenção de funcionar apenas na web. Caso você queira executar este aplicativo em dispositivos móveis, você vai precisar de instalação e configurações adicionais.

### 3. Liste os dispositivos

Para garantir que o suporte web está instalado, liste os dispositivos disponíveis. Você deveria ver algo parecido com o conteúdo abaixo:

```bash
$ flutter devices
2 connected devices:

Chrome     • chrome     • web-javascript • Google Chrome 78.0.3904.108
Web Server • web-server • web-javascript • Flutter Tools
```

O dispositivo **Chrome** automaticamente inicia o Chrome. O dispositivo **Web Server** inicia um servidor que irá hospedar o aplicativo, desta forma você pode carregá-lo em qualquer navegador. Utilize o dispositivo Chrome durante o desenvolvimento, pois desta forma você tem acesso ao DevTools e o dispositivo Web Server quando você quiser testar outros navegadores.

### 4. O aplicativo inicial está exibido abaixo

Abra o link abaixo para ter acesso ao **DartPad**, uma versão online do Dart. O link conterá o código inicial e você poderá visualizar uma prévia do aplicativo direto no navegador.

Link: [https://dartpad.dev/cdce94be4f861d16e4ec8c9b781d4128](https://dartpad.dev/cdce94be4f861d16e4ec8c9b781d4128)

### 5. Execute o exemplo

No DartPad, clique no botão **Run** para executar o exemplo. Perceba que você pode digitar nos campos de texto, porém o botão Acessar está desabilitado.

### 6. Copie o código

Selecione todo o conteúdo e copie-o para a área de transferência.

### 7. Crie um projeto Flutter

Utilizando o Visual Studio Code ou a linha de comando, [crie um projeto Flutter](https://flutter.dev/docs/get-started/test-drive) e defina seu nome como `login_exemplo`.

### 8. Substitua o conteúdo do arquivo `lib/main.dart` com o conteúdo da área de transferência. 

Observações

* O código completo deste exemplo fica no arquivo `lib/main.dart`
* Se você conhece Java ou JavaScript, a linguagem Dart deve lhe parecer familiar
* Toda a interface do aplicativo é criada em código Dart. Para mais informações, veja o artigo [Introdução a interface de usuário declarativa](https://flutter.dev/docs/get-started/flutter-for/declarative)
* A interface do aplicativo é aderente ao [Material Design](https://material.io/design/introduction/), um linguagem de design visual que roda em qualquer dispositivo ou plataforma. Você pode customizar os _widgets_ do Material Design, mas se você preferir algo mais, o Flutter também oferece a biblioteca de _widgets_ Cupertino, que implementa a linguagem visual do iOS atual. Ou, você pode criar a sua própria biblioteca de _widgets_ customizada.
* No Flutter, quase tudo é um [_Widget_](https://api.flutter.dev/flutter/widgets/Widget-class.html). O próprio aplicativo em si é um _widget_. A interface de usuário do aplicativo pode ser descrita como uma árvore de _widgets_.

