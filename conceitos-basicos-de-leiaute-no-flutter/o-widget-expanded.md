# 5. O Widget Expanded

Similar ao _widget_ `Flexibe`, o _widget_ `Expanded` pode envolver um _widget_ para forçá-lo a preencher todo o espaço extra disponível.

> **Dica: Qual a diferença entre `Flexibe` e `Expanded`?**
>
> Use `Flexibe` para redimensionar _widgets_ em uma `Row` ou em uma `Column`. Desta forma, você pode ajustar o espaçamento dos filhos do _widget_ mantendo a relação de tamanho com os seus _widgets_ pai. 
>
> Use `Expanded` para modificar as restrições de tamanho de um _widget_ filho e desta forma preencher todo o espaço vazio.
>
> Para aprender mais sobre restrições e como elas afetam a forma que o Flutter determina o tamanho e a posição dos seus _widgets_, veja [Entendendo as restrições](https://flutter.dev/docs/development/ui/layout/constraints).

### Exemplo: Preenchendo o espaço extra

O seguinte exemplo demonstra como o _widget_ `Expanded` força seus _widgets_ filhos a preencherem o espaço extra.

1. Copie o código abaixo e cole no [DartPad](https://dartpad.dev/embed-flutter.html?id=c4dfa9058f803dea1cff4fca2532977a).
2. Clique no botão **Run**.
3. Envolva o segundo _widget_ `BlueBox` com um _widget_ `Expanded`. Por exemplo: `Expanded(child: BlueBox(),),`
4. Clique no botão **Format** para formatar o código e rode novamente.

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

