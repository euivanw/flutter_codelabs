# 9. O Widget Icon

O _widget_ `Icon` exibir um símbolo gráfico que representa um aspecto da interface do usuário. O Flutter fornece pacotes de ícones pré-carregados para aplicações [Material](https://api.flutter.dev/flutter/material/MaterialApp-class.html) e [Cupertino](https://api.flutter.dev/flutter/cupertino/CupertinoApp-class.html).

### Exemplo: Criando um ícone

O exemplo a seguir exibe o _widget_ `Icons.widget` da [biblioca de ícones do Material](https://api.flutter.dev/flutter/material/Icons-class.html) nas cores vermelho e azul.

1. Copie o código abaixo e cole no [DartPad](https://dartpad.dev/embed-flutter.html?id=54fa77a90f160c74382f1517d6167fda).
2. Clique no botão **Run**.
3. Adicione outro ícone da [biblioteca de ícones do Material](https://api.flutter.dev/flutter/material/Icons-class.html) com o tamanho igual a 50.
4. Mude a cor do ícone para `Colors.amber` da [paleta de cores do Material](https://api.flutter.dev/flutter/material/Colors-class.html) e rode novamente.

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
        Icon(
          Icons.widgets,
          size: 50,
          color: Colors.blue,
        ),
        Icon(
          Icons.widgets,
          size: 50,
          color: Colors.red,
        ),
      ],
    );
  }
}
```

