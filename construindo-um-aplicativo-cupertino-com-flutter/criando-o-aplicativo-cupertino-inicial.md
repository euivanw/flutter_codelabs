# 3. Criar o aplicativo Cupertino inicial

Crie o aplicativo inicial usando um `CupertinoPageScaffold`.

![](https://codelabs.developers.google.com/codelabs/first-flutter-app-pt2/img/a3c16fc17be25f6c.png)Crie um aplicativo Flutter usando as instruções Iniciando seu primeiro aplicativo Flutter. O nome do projeto será `flutter_codelabs_lab5` \(ao invés de `myapp`\). Você vai modificar o aplicativo inicial para criar o aplicativo final.

> **Dica**: Se você não tiver a opção **New Flutter Project** \(Novo aplicativo Flutter\) nas opções da sua _IDE_, verifique se você tem os [plugins do Flutter e do Dart](https://flutter.dev/docs/get-started/editor?tab=vscode#androidstudio) instalados.

![](https://codelabs.developers.google.com/codelabs/first-flutter-app-pt2/img/a3c16fc17be25f6c.png)Substitua o conteúdo do arquivo `lib/main.dart`

Exclua todo o código do arquivo `lib/main.dart`, que atualmente contém um aplicativo Material com um botão para contagem. Substitua pelo código a seguir, que inicializa um aplicativo Cupertino.

```bash
import 'package:flutter/cupertino.dart';

import 'app.dart';

void main() {
  return runApp(AppLojaCupertino());
}
```

#### Observações:

* Importe o pacote Cupertino. Isto fará com que os _widgets_ do Cupertino estejam disponíveis para o seu aplicativo.

![](https://codelabs.developers.google.com/codelabs/first-flutter-app-pt2/img/a3c16fc17be25f6c.png) Crie o arquivo `lib/styles.dart`

Adicione um arquivo no diretório `lib` chamado `styles.dart`. A classe `Styles` define a estilização de cor e fonte para customizar o aplicativo. 

```dart
import 'package:flutter/cupertino.dart';
import 'package:flutter/widgets.dart';

abstract class Styles {
  static const TextStyle linhaProdutoNomeDoItem = TextStyle(
    color: Color.fromRGBO(0, 0, 0, 0.8),
    fontSize: 18,
    fontStyle: FontStyle.normal,
    fontWeight: FontWeight.normal,
  );

  static const TextStyle linhaProdutoTotal = TextStyle(
    color: Color.fromRGBO(0, 0, 0, 0.8),
    fontSize: 18,
    fontStyle: FontStyle.normal,
    fontWeight: FontWeight.bold,
  );

  static const TextStyle linhaProdutoPrecoDoItem = TextStyle(
    color: Color(0xFF8E8E93),
    fontSize: 13,
    fontWeight: FontWeight.w300,
  );

  static const TextStyle textoPesquisa = TextStyle(
    color: Color.fromRGBO(0, 0, 0, 1),
    fontSize: 14,
    fontStyle: FontStyle.normal,
    fontWeight: FontWeight.normal,
  );

  static const TextStyle textoTempoEntrega = TextStyle(
    color: Color(0xFFC2C2C2),
    fontWeight: FontWeight.w300,
  );

  static const TextStyle tempoEntrega = TextStyle(
    color: CupertinoColors.inactiveGray,
  );

  static const Color linhaProdutoDivisor = Color(0xFFD9D9D9);

  static const Color fundoScaffold = Color(0xfff0f0f0);

  static const Color fundoPesquisa = Color(0xffe0e0e0);

  static const Color cursorPesquisaCor = Color.fromRGBO(0, 122, 255, 1);

  static const Color iconePesquisaCor = Color.fromRGBO(128, 128, 128, 1);
}
```

#### Observações:

* Podemos centralizar as definições de estilo da mesma forma que os programadores web centralizam seus estilos em arquivo _CSS_, agrupando todas as nossas definições em único arquivo. Isto tratá uma forma simples de reusar e redefinir estilos por todo o aplicativo.

![](https://codelabs.developers.google.com/codelabs/first-flutter-app-pt2/img/a3c16fc17be25f6c.png)Crie o arquivo `lib/app.dart` e adicione a classe `AppLojaCupertino`.

```dart
import 'package:flutter/cupertino.dart';
import 'package:flutter/services.dart';

class AppLojaCupertino extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    // Este aplicativo foi desenhado para funcionar na vertical,
    // desta forma, nós podemos limitar a orientação para retrato
    // em pé e deitado.
    SystemChrome.setPreferredOrientations([
      DeviceOrientation.portraitUp,
      DeviceOrientation.portraitDown,
    ]);

    return CupertinoApp(
      home: PaginaPrincipalLojaCupertino(),
    );
  }
}
```

#### Observações:

* Importe a [biblioteca de serviços](https://api.flutter.dev/flutter/services/services-library.html). Isto faz com que os serviços de plataforma, como área de transferência e configurações de orientação do dispositivo fiquem disponíveis para o seu aplicativo.
* Instancie um `CupertinoApp`, que provê tema, navegação, direção de texto e outros requerimentos padrão para criar um aplicativo que um usuário do iOS espera.
* Instancie um `PaginaPrincipalLojaCupertino` como a página principal.
* O aplicativo foi desenhado para funcionar apenas na vertical, desta forma a orientação do dispositivo será limitada ao modo retrato.

![](https://codelabs.developers.google.com/codelabs/first-flutter-app-pt2/img/a3c16fc17be25f6c.png)Adicione a classe `PaginaPrincipalLojaCupertino`.

Adicione classe `PaginaPrincipalLojaCupertino` a seguir no arquivo `lib/app.dart` para criar o leiaute da página principal.

```dart
class PaginaPrincipalLojaCupertino extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return const CupertinoPageScaffold(
      navigationBar: CupertinoNavigationBar(
        middle: Text('Loja Cupertino'),
      ),
      child: SizedBox(),
    );
  }
}
```

#### Observações:

* O pacote Cupertino fornece dois tipos de estrutura de página. A classe `CupertinoPageScaffold` suporta páginas simples e aceita o estilo de barra de navegação, cor de fundo e mantêm a estrutura da árvore de objetos do Cupertino. Você vai aprender sobre o segundo tipo no próximo passo.
* A página contém um título simples e a árvore de _widgets_ contém um único contêiner vazio.

![](https://codelabs.developers.google.com/codelabs/first-flutter-app-pt2/img/a3c16fc17be25f6c.png)Atualize o arquivo `pubspec.yaml`.

No topo da estrutura do projeto, edite o arquivo `pubspec.yaml`. Adicione as bibliotecas que você vai precisar e a lista de imagens.

```yaml
name: flutter_codelabs_lab5
description: Criando uma loja com widgets Cupertino.

publish_to: "none"

version: 1.0.0+1

environment:
  sdk: ">=2.7.0 <3.0.0"

dependencies:
  flutter:
    sdk: flutter

  cupertino_icons: ^0.1.3
  intl: ^0.16.1
  provider: ^4.1.1
  shrine_images: ^1.0.0

dev_dependencies:
  flutter_test:
    sdk: flutter
  pedantic: ^1.9.0

flutter:
  uses-material-design: true
  assets:
    - packages/shrine_images/0-0.jpg
    - packages/shrine_images/1-0.jpg
    - packages/shrine_images/2-0.jpg
    - packages/shrine_images/3-0.jpg
    - packages/shrine_images/4-0.jpg
    - packages/shrine_images/5-0.jpg
    - packages/shrine_images/6-0.jpg
    - packages/shrine_images/7-0.jpg
    - packages/shrine_images/8-0.jpg
    - packages/shrine_images/9-0.jpg
    - packages/shrine_images/10-0.jpg
    - packages/shrine_images/11-0.jpg
    - packages/shrine_images/12-0.jpg
    - packages/shrine_images/13-0.jpg
    - packages/shrine_images/14-0.jpg
    - packages/shrine_images/15-0.jpg
    - packages/shrine_images/16-0.jpg
    - packages/shrine_images/17-0.jpg
    - packages/shrine_images/18-0.jpg
    - packages/shrine_images/19-0.jpg
    - packages/shrine_images/20-0.jpg
    - packages/shrine_images/21-0.jpg
    - packages/shrine_images/22-0.jpg
    - packages/shrine_images/23-0.jpg
    - packages/shrine_images/24-0.jpg
    - packages/shrine_images/25-0.jpg
    - packages/shrine_images/26-0.jpg
    - packages/shrine_images/27-0.jpg
    - packages/shrine_images/28-0.jpg
    - packages/shrine_images/29-0.jpg
    - packages/shrine_images/30-0.jpg
    - packages/shrine_images/31-0.jpg
    - packages/shrine_images/32-0.jpg
    - packages/shrine_images/33-0.jpg
    - packages/shrine_images/34-0.jpg
    - packages/shrine_images/35-0.jpg
    - packages/shrine_images/36-0.jpg
    - packages/shrine_images/37-0.jpg
```

#### Observações:

* Isto irá adicionar inúmeros pacotes, incluindo o pacote [`shrine_images`](https://pub.dev/packages/shrine_images), que contém as imagens dos produtos para popular a loja.
* O pacote [`provider`](https://pub.dev/packages/provider) fornece uma forma simples de gerenciar o estado entre as telas.
* O pacote [`intl`](https://pub.dev/packages/intl) fornece facilitadores para internacionalização e localização.
* O pacote [`cupertino_icons`](https://pub.dev/packages/cupertino_icons) contem os ícones para os _widgets_ do Cupertino.

![](https://codelabs.developers.google.com/codelabs/first-flutter-app-pt2/img/a3c16fc17be25f6c.png)Rode o aplicativo. Você deve ver uma tela contendo uma barra de navegação do Cupertino e um título.

![](../.gitbook/assets/lab5_step3%20%281%29.png)

#### Problemas?

Se o seu aplicativo não estiver rodando corretamente, utilize o código dos links a seguir, para voltar aos trilhos.‌

* [pubspec.yaml](https://github.com/ivanwhm/flutter_codelabs_lab5/blob/a90d4a9f38f65422ac90a4d0426db6e1feb88242/pubspec.yaml)
* [lib/app.dart](https://github.com/ivanwhm/flutter_codelabs_lab5/blob/a90d4a9f38f65422ac90a4d0426db6e1feb88242/lib/app.dart)
* [lib/main.dart](https://github.com/ivanwhm/flutter_codelabs_lab5/blob/a90d4a9f38f65422ac90a4d0426db6e1feb88242/lib/main.dart)
* [lib/styles.dart](https://github.com/ivanwhm/flutter_codelabs_lab5/blob/a90d4a9f38f65422ac90a4d0426db6e1feb88242/lib/styles.dart)

