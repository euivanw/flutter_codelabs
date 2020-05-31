# 4. O Widget Flexible

Como você viu, as propriedades `mainAxisAlignment` e `crossAxisAlignment` determinam como a `Row` e a `Column` posicionam _widgets_ em ambos os eixos. A `Row` e a `Column` primeiramente dispõem os _widgets_ com tamanho fixo. _Widgets_ com tamanhos fixos são considerados **inflexíveis** porque eles não podem se redimensionarem após serem dispostos.

O _widget_ `Flexible` envolve um _widget_, desta forma o _widget_ se torna redimensionável. Quando o _widget_ `Flexible` envolve um _widget_, o _widget_ se torna filho do _widget_ `Flexible` e é considerado flexível. Após os _widgets_ inflexíveis serem dispostos, os _widgets_ são redimensionados de acordo com as suas propriedades `flex` e `fit`.:

* **`flex`**: Compara a sua própria propriedade `flex` com a dos outros antes de determinar qual fração do total do espaço remanescente cada _widget_ `Flexible` irá receber.
* **`fit`**: Determina se um _widget_ `Flexible` preenche todo o espaço extra ou não.

### Exemplo: Mudando a propriedade `fit`

O exemplo a seguir demonstra a propriedade `fit`, que pode ter um dos seguintes valores:

* `FlexFit.loose`: O tamanho escolhido do `widget` é utilizado. \(Padrão\)
* `FlexFit.tight`: Força o `widget` a preencher todo o espaço extra disponível.

Neste exemplo, mude a propriedade `fit` para fazer os _widgets_ `Flexibe` preencherem todo o espaço extra.

1. Copie o código abaixo e cole no [DartPad](https://dartpad.dev/embed-flutter.html?id=817baa1ba2123f15abda92598c4343cc).
2. Clique no botão **Run**.
3. No código, altere o valor de `fit` em ambos os _widgets_ para `FlexFit.tight` e rode novamente.

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
        Flexible(
          fit: FlexFit.loose,
          flex: 1,
          child: BlueBox(),
        ),
        Flexible(
          fit: FlexFit.loose,
          flex: 1,
          child: BlueBox(),
        ),
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

### Exemplo: Testando os valores de `flex`

No exemplo a seguir, a `Row` contém um _widget_ `BlueBox` e dois _widgets_ `Flexibe` que envolvem os dois _widgets_ `BlueBox`. Os _widgets_ `Flexibe` contém a propriedade `flex` com o valor definido em 1 \(valor padrão\).

Quando as propriedades `flex` são comparadas entre si, o rateio entre os seus valores de `flex` determinam qual fração do total de espaço disponível cada _widget_ `Flexibe` irá receber.

{% hint style="info" %}
espacoDisponivel \* \(flex / somaTotalDeTodosOsValoresDeFlex\)
{% endhint %}

Neste exemplo, a soma dos valores de `flex` \(2\) determina, que ambos os _widgets_ `Flexibe` irão receber a metade do espaço total disponível. O _widget_ `BlueBox` \(ou o _widget_ com tamanho fixo\) permanece com o mesmo tamanho.

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
        Flexible(
          fit: FlexFit.tight,
          flex: 1,
          child: BlueBox(),
        ),
        Flexible(
          fit: FlexFit.tight,
          flex: 1,
          child: BlueBox(),
        ),
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

> **Dica**: Antes de ir para o próximo exemplo, tente mudar as propriedades `flex` para outros valores, como 2 e 1.

