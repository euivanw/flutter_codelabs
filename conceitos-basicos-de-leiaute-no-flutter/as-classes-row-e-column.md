# 2. As classes Row e Column

`Row` e `Column` são classes que contém e distribuem objetos. Os _widgets_ dentro de uma `Row` ou de uma `Column` são chamados de filhos \(_children_\) e a `Row` ou a `Column` são referenciados como seus pais \(_parents_\). A `Row` distribui seus _widgets_ horizontalmente e a `Column` distribui seus _widgets_ verticalmente.

### Exemplo: Criando uma `Column`

O exemplo a seguir mostra as diferenças entre uma `Row` e uma `Column`.

1. Copie o código abaixo e cole no [DartPad](https://dartpad.dev/embed-flutter.html?id=009a77697460e7ec6a3c142f0dfb1b5e).
2. Clique no botão **Run**.
3. No código, altere a `Row` para `Column` e clique no botão **Run** novamente.

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

