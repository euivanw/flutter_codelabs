# 3. Tamanho do eixo e Alinhamento

Até agora, os _widgets_ `BlueBox` estão esmagados e juntos \(na esquerda ou no topo da saída da UI\). Você pode alterar como os _widgets_ `BlueBox` são espaçados usando as propriedades `axis size` e `alignment`.

### A propriedade `mainAxisSize`

A `Row` e a `Column` ocupam diferentes eixos principais. O eixo principal da `Row` é horizontal e o da `Column` é vertical. A propriedade `mainAxisSize` determina quanto espaço uma `Row` ou uma `Column` podem ocupar em seus eixos principais. A propriedade `mainAxisSize` possui dois possíveis valores:

* `MainAxisSize.max`: A `Row` e a `Column` ocupam todo o espaço de seus eixos principais. Se a largura combinada dos seus _widgets_ filhos for menor que o total de espaço de seus eixos principais, os seus filhos são dispostos com espaço extra.
* `MainAxisSize.min`: A `Row` e a `Column` ocupam somente o espaço necessário para seus filhos em seus eixos principais. Seus filhos são dispostos sem espaço extra e no meio de seus eixos principais.

> **Dica**: `MainAxisSize.max` é a o valor padrão da propriedade `mainAxisSize`. Se você não informar outro valor, o valor padrão é usado, conforme mostrado no exemplo anterior.

### Exemplo: Modificando o tamanho do eixo

O exemplo a seguir define de forma explícita a propriedade `mainAxisSize` para usar seu valor padrão, `MainAxisSize.max`.

1. Copie o código abaixo e cole no [DartPad](https://dartpad.dev/embed-flutter.html?id=928d699ea0869e75d072e6e9c4e63397).
2. Clique no botão **Run**.
3. No código, altere a propriedade `mainAxisSize` de `MainAxisSize.max` para `MainAxisSize.min` e clique no botão **Run** novamente.

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

### A propriedade `crossAxisAlignment`

A propriedade `crossAxisAligment` determinar como a `Row` e a `Column` podem posicionar seus filhos em seus eixos cruzados. O eixo cruzado da `Row` é vertical e o eixo cruzado da `Column` é horizontal. A propriedade `crossAxisAligment` tem cinco valores possíveis:

* `CrossAxisAligment.start`: Posiciona os filhos perto do início do seu eixo cruzado. \(Superior para a `Row` e esquerda para a `Column`\)
* `CrossAxisAligment.end`: Posiciona os filhos perto do final do seu eixo cruzado. \(Inferior para a `Row` e direita para a `Column`\)
* `CrossAxisAligment.center`: Posiciona os filhos no meio do seu eixo cruzado. \(Metade para a `Row` e centro para a `Column`\)
* `CrossAxisAligment.stretch`: Estica os filhos no eixo cruzado. \(Do superior para o inferior na `Row` e da esquerda para a direita na `Column`\)
* `CrossAxisAligment.baseline`: Alinha seus filhos pelas suas linha base. \(Apenas a classe `Text` e necessita que a propriedade `textBaseline` seja definida para `TextBaseline.alphabetic`. Veja o exemplo na seção [`O Widget Text`](https://ivanwhm.gitbook.io/laboratorios-de-codigo-do-flutter/conceitos-basicos-de-leiaute-no-flutter/o-widget-text).\)

### Exemplo: Modificando o alinhamento cruzado do eixo

O exemplo a seguir define de forma explícita a propriedade `crossAxisAlignment` para usar seu valor padrão, `CrossAxisAlignment.center`.

Para demonstrar o alinhamento cruzado do eixo, a propriedade `mainAxisAligment` é definida como `MainAxisAlignment.spaceAround` e a `Row` agora também contém o _widget_ `BiggerBlueBox` que é mais alto que os _widgets_ `BlueBox`.

1. Copie o código abaixo e cole no [DartPad](https://dartpad.dev/embed-flutter.html?id=d160e264a865479586ec7940f45cf8b2).
2. Clique no botão **Run**.
3. No código, altere a propriedade `crossAxisAlignment` de `CrossAxisAlignment.center` para `CrossAxisAlignment.start` e clique no botão **Run** novamente.

```dart
import 'dart:async';
import 'package:flutter/material.dart';
import 'package:flutter_test/flutter_test.dart';

class MyWidget extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Row(
      mainAxisAlignment: MainAxisAlignment.spaceAround,
      crossAxisAlignment: CrossAxisAlignment.center,
      children: [
        BlueBox(),
        BiggerBlueBox(),
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

class BiggerBlueBox extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Container(
      width: 50,
      height: 100,
      decoration: BoxDecoration(
        color: Colors.blue,
        border: Border.all(),
      ),
    );
  }
}
```

