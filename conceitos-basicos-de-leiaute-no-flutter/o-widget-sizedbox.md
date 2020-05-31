# 6. O Widget SizedBox

O _widget_ `SizedBox` pode ser utilizado de uma das duas formas quando cria uma dimensão exata. Quando o `SizedBox` envolve um _widget_, ele redimensiona o _widget_ usando as propriedades `height` \(altura\) e `width` \(largura\). Quando ele não envolve um _widget_, ele usa as propriedades `height` e `width` para criar um espaço vazio.

### Exemplo: Redimensionando um _widget_

O exemplo a seguir, envolve o _widget_ `BlueBox` central dentro de um _widget_ `SizedBox` e define a largura do _widget_ `BlueBox` em 100 pixels lógicos.

1. Copie o código abaixo e cole no [DartPad](https://dartpad.dev/embed-flutter.html?id=716612f4ae2d979cc5a2868e06c14e58).
2. Clique no botão **Run**.
3. Adicione a propriedade `height` igual a 100 pixels lógicos dentro do _widget_ `SizedBox` e rode novamente.

```dart
import 'dart:async';
import 'package:flutter/material.dart';
import 'package:flutter_test/flutter_test.dart';

class MyWidget extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Row(
      mainAxisSize: MainAxisSize.max,
      children: [
        BlueBox(),
        SizedBox(
          width: 100,
          child: BlueBox(),
        ),
        BlueBox(),
      ],
    );
  }
}

class BlueBox extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Container(
      width: 50,
      height: 50,
      decoration: BoxDecoration(
        color: Colors.blue,
        border: Border.all(),
      ),
    );
  }
}
```

### Exemplo: Criando um espaço

O exemplo a seguir contém três _widgets_ `SizedBox` e um _widget_ `SizedBox` que separa o primeiro _widget_ `BlueBox` do segundo. O _widget_ `SizedBox` contém a propriedade _widget_ igual a 50 pixels lógicos.

1. Copie o código abaixo e cole no [DartPad](https://dartpad.dev/embed-flutter.html?id=1c690c529316fbe7af0b4c9edb8da512).
2. Clique no botão **Run**.
3. Crie mais espaço adicionando outro _widget_ `SizedBox` \(com 25 pixels lógicos de largura\) entre o segundo e o terceiro _widget_ `SizedBox` e rode novamente.

```dart
import 'dart:async';
import 'package:flutter/material.dart';
import 'package:flutter_test/flutter_test.dart';

class MyWidget extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Row(
      children: [
        BlueBox(),
        SizedBox(width: 50),
        BlueBox(),
        BlueBox(),
      ],
    );
  }
}

class BlueBox extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Container(
      width: 50,
      height: 50,
      decoration: BoxDecoration(
        color: Colors.blue,
        border: Border.all(),
      ),
    );
  }
}
```

