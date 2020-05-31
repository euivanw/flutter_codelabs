# 8. O Widget Text

O _widget_ `Text` exibe texto e pode configurar fontes, tamanhos e cores diferentes.

### Exemplo: Alinhando texto

O exemplo a seguir exibe o texto "Hey!" três vezes, mas com tamanhos de fontes e cores diferentes. A `Row` especifica as propriedades `crossAxisAlignment` e `textBaseline`.

1. Copie o código abaixo e cole no [DartPad](https://dartpad.dev/embed-flutter.html?id=05d920fd86eb3c253c2a6a8be0fabb01).
2. Clique no botão **Run**.
3. Mude o `CrossAxisAlignment.center` para `CrossAxisAlignment.baseline` e rode novamente.

```dart
import 'dart:async';
import 'package:flutter/material.dart';
import 'package:flutter_test/flutter_test.dart';

class MyWidget extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Row(
      crossAxisAlignment: CrossAxisAlignment.center,
      textBaseline: TextBaseline.alphabetic,
      children: [
        Text(
          'Hey!',
          style: TextStyle(
            fontSize: 30,
            fontFamily: 'Futura',
            color: Colors.blue,
          ),
        ),
        Text(
          'Hey!',
          style: TextStyle(
            fontSize: 50,
            fontFamily: 'Futura',
            color: Colors.green,
          ),
        ),
        Text(
          'Hey!',
          style: TextStyle(
            fontSize: 40,
            fontFamily: 'Futura',
            color: Colors.red,
          ),
        ),
      ],
    );
  }
}
```

