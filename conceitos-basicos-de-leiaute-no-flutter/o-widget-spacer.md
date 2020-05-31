# 7. O Widget Spacer

Similar ao `SizedBox`, o _widget_ `Spacer` também pode criar um espaço entre _widgets_.

> **Dica: Qual a diferença entre `SizedBox` e `Spacer`?**
>
> Use o `Spacer` quando você quer criar espaço usando a propriedade `flex`.
>
> Use o `SizedBox` quando você quer criar espaço usando um número específico de pixels lógicos.

### Exemplo: Criando mais espaço

O exemplo a seguir separa os dois primeiros _widgets_ `BlueBox` usando o _widget_ `Spacer` com o valor flex igual a 1.

1. Copie o código abaixo e cole no [DartPad](https://dartpad.dev/embed-flutter.html?id=5a2f539d258eaab33f6f0b19a0ab21c8).
2. Clique no botão **Run**.
3. Adicione outro _widget_ `Spacer` \(com a propriedade flex igual a 1\) entre o segundo e o terceiro _widget_ `BlueBox` e rode novamente.

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
        Spacer(flex: 1),
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

