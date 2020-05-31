# 10. O Widget Image

O _widget_ `Image` exibe uma imagem. Você pode referenciar imagens usando uma _URL_ ou pode incluir as imagens dentro do pacote do seu aplicativo. Devido ao DartPad não poder empacotar uma imagem, o exemplo a seguir irá usar uma imagem da internet.

### Exemplo: Exibindo uma imagem

O exemplo a seguir exibe uma imagem que está armazenada remotamente no [GitHub](https://github.com/flutter/website/tree/master/examples/layout/sizing/images). O construtor nomeado `Image.network` tem um parâmetro string que contém a _URL_ da imagem.

Neste exemplo, o construtor nomeado `Image.network` contém uma _URL_ encurtada.

1. Copie o código abaixo e cole no [DartPad](https://dartpad.dev/embed-flutter.html?id=b42464ac4e9bff23ab567721581183aa).
2. Clique no botão **Run**.
3. Mude a _URL_ encurtada para a _URL_ [https://github.com/flutter/website/blob/master/examples/layout/sizing/images/pic3.jpg?raw=true](https://github.com/flutter/website/blob/master/examples/layout/sizing/images/pic3.jpg?raw=true)
4. Troque a parte **pic3.jpg** da URL para **pic1.jpg** ou **pic2.jpg** e rode novamente.

```dart
import 'dart:async';
import 'package:flutter/material.dart';
import 'package:flutter_test/flutter_test.dart';

class MyWidget extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Row(
      mainAxisAlignment: MainAxisAlignment.center,
      children: [
        Image.network('https://urlzs.com/RsqCz'),
      ],
    );
  }
}
```

