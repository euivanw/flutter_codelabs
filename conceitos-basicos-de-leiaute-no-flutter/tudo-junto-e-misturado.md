# 11. Unindo todas as partes

Você está quase no final deste laboratório. Se você quiser testar seu conhecimento nas técnicas que aprendeu, porque não aplicar essas habilidades para construir uma interface do usuário em Flutter que exibe um cartão de visitas?

![](../.gitbook/assets/image%20%285%29.png)

Você vai quebrar em partes do leiaute do Flutter, que é como você cria interface de usuário no Flutter no mundo real.

Na parte 1, você vai implementar uma `Column` que contém o nome e o cargo. Então você vai envolver a `Column` em uma `Row` que contém um ícone, que está posicionado à esquerda do nome e do cargo.

![](../.gitbook/assets/image%20%281%29.png)

Na parte 2, você vai envolver a `Row` em uma `Column`, desta forma o código vai conter uma `Column` envolta em uma `Row`, que está envolta em outra `Column`. Então você vai ajustar o leiaute mais externo da `Column` e isto vai ficar incrível. Finalmente, você vai adicionar as informações do contato que ao extremo do lista de filhos da `Column`, para então exibir abaixo do nome, cargo e ícone.

![](../.gitbook/assets/image%20%283%29.png)

Na parte 3, você vai finalizar a construção do cartão de visitas adicionando mais ícones, que serão posicionados abaixo das informações de contato.

![](../.gitbook/assets/image%20%286%29.png)

## Parte 1

### Exercício: Crie o nome o cargo

Implemente uma `Column` que contém dois _widgets_ `Text`:

* O primeiro _widget_ `Text` tem o nome `Ivan Wilhelm` e a propriedade `style` definida como `Theme.of(context).textTheme.headline5`.
* O segundo _widget_ `Text` tem o cargo `Desenvolvedor Flutter`.

Para a `Column`, defina a propriedade `mainAxisSize` para `MainAsixSize.min` e a `crossAxisAlignment` para `CrossAxisAlignment.start`.

```dart
import 'dart:async';
import 'package:flutter/material.dart';
import 'package:flutter_test/flutter_test.dart';

class ExemploFinal extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    // Comece implementando a coluna aqui.
  }
}
```

### Exercício: Envolva a Column em uma Row

Envolva a `Column` que você implementou em uma `Row` que conterá os seguintes _widgets_:

* Um _widget_ `Icon` definido como `Icons.account_circle` e com tamanho de 50 pixels.
* Um _widget_ `Padding`  cria um espaço de 8 pixels em volta do _widget_ `Icon`.

Para fazer isto, você pode definir a propriedade `padding` como `const EdgeInsets.all(8.0)`.

```dart
Row(
  children: [
    Padding(
      padding: const EdgeInsets.all(8.0),
      child: Icon(Icons.account_circle, size: 50),
    ),
    Column( ... ), // <--- A coluna implementada no exercicio anterior
  ],
);
```

```dart
// Solução do exercício anterior

import 'dart:async';
import 'package:flutter/material.dart';
import 'package:flutter_test/flutter_test.dart';

class ExemploFinal extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Column(
      mainAxisSize: MainAxisSize.min,
      crossAxisAlignment: CrossAxisAlignment.start,
      children: <Widget>[
        Text(
          'Ivan Wilhelm',
          style: Theme.of(context).textTheme.headline5,
        ),
        Text('Desenvolvedor Flutter'),
      ],
    );
  }
}
```

## Parte 2

### Exercício: Ajuste o leiaute

Envolva a `Row` em uma `Column` que tem a propriedade `mainAxisSize` definida como `MainAxisSize.min` e a propriedade `crossAxisAlignment` definida como `CrossAxisAlignment.stretch.` A `Column` contém os seguintes _widgets_:

* Um _widget_ `SizedBox` com altura 8.
* Uma `Row` vazia onde você vai adicionar as informações de contato no próximo exercício.
* Um segundo _widget_ `SizedBox` com altura 16.
* Uma segunda `Row` vazia onde você vai adicionar quatro ícones \(Parte 3\).

A lista de _widgets_ da `Column` deve ser formatada conforme a seguir, desta forma, as informações de contato e os ícones serão exibidos abaixo do nome e do cargo:

```dart
     ],
    ), // <--- Parênteses de fechamento da Row
    SizedBox(),
    Row(), // Primeira Row vazia
    SizedBox(),
    Row(), // Segunda Row vazia
   ],
  ); // <--- Parênteses de fechamento da Column que envolve a Row
```

```dart
// Solução do exercício anterior

import 'dart:async';
import 'package:flutter/material.dart';
import 'package:flutter_test/flutter_test.dart';

class ExemploFinal extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Row(
      children: <Widget>[
        Padding(
          padding: const EdgeInsets.all(8.0),
          child: Icon(
            Icons.account_circle,
            size: 50.0,
          ),
        ),
        Column(
          mainAxisSize: MainAxisSize.min,
          crossAxisAlignment: CrossAxisAlignment.start,
          children: <Widget>[
            Text(
              'Ivan Wilhelm',
              style: Theme.of(context).textTheme.headline,
            ),
            Text('Desenvolvedor Flutter'),
          ],
        ),
      ],
    );
  }
}
```

### Exercício: Entre com as informações de contato

Entre com dois _widgets_ `Text` dentro da primeira `Row` vazia:

* O primeiro _widget_ `Text` contém o endereço `Rua XV de Novembro, 123`.
* O segundo _widget_ `Text` contém o número de telefone `(47) 36843-87388`.

Para a primeira `Row` vazia, defina a propriedade `mainAxisAlignment` como `MainAxisAlignment.spaceBetween`.

```dart
// Solução do exercício anterior

import 'dart:async';
import 'package:flutter/material.dart';
import 'package:flutter_test/flutter_test.dart';

class ExemploFinal extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Column(
      mainAxisSize: MainAxisSize.min,
      crossAxisAlignment: CrossAxisAlignment.stretch,
      children: <Widget>[
        Row(
          children: <Widget>[
            Padding(
              padding: const EdgeInsets.all(8.0),
              child: Icon(
                Icons.account_circle,
                size: 50.0,
              ),
            ),
            Column(
              mainAxisSize: MainAxisSize.min,
              crossAxisAlignment: CrossAxisAlignment.start,
              children: <Widget>[
                Text(
                  'Ivan Wilhelm',
                  style: Theme.of(context).textTheme.headline5,
                ),
                Text('Desenvolvedor Flutter'),
              ],
            ),
          ],
        ),
        SizedBox(
          height: 8.0,
        ),
        Row(),
        SizedBox(
          height: 16.0,
        ),
        Row(),
      ],
    );
  }
}
```

## Parte 3

### Exercício: Adicione quatro ícones

Entre com os seguintes _widgets_ `Icon` dentro da segunda `Row` vazia:

* `Icons.accessibility`
* `Icons.timer`
* `Icons.phone_android`
* `Icons.phone_iphone`

Para a segunda `Row` vazia, defina a propriedade `mainAxisAlignment` como `MainAxisAlignment.spaceAround`.

```dart
// Solução final

import 'dart:async';
import 'package:flutter/material.dart';
import 'package:flutter_test/flutter_test.dart';

class ExemploFinal extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Column(
      mainAxisSize: MainAxisSize.min,
      crossAxisAlignment: CrossAxisAlignment.stretch,
      children: <Widget>[
        Row(
          children: <Widget>[
            Padding(
              padding: const EdgeInsets.all(8.0),
              child: Icon(
                Icons.account_circle,
                size: 50.0,
              ),
            ),
            Column(
              mainAxisSize: MainAxisSize.min,
              crossAxisAlignment: CrossAxisAlignment.start,
              children: <Widget>[
                Text(
                  'Ivan Wilhelm',
                  style: Theme.of(context).textTheme.headline5,
                ),
                Text('Desenvolvedor Flutter'),
              ],
            ),
          ],
        ),
        SizedBox(
          height: 8.0,
        ),
        Row(
          mainAxisAlignment: MainAxisAlignment.spaceBetween,
          children: <Widget>[
            Text('Rua XV de Novembro, 123'),
            Text('(47) 36843-87388'),
          ],
        ),
        SizedBox(
          height: 16.0,
        ),
        Row(
          mainAxisAlignment: MainAxisAlignment.spaceAround,
          children: <Widget>[
            Icon(Icons.accessibility),
            Icon(Icons.timer),
            Icon(Icons.phone_android),
            Icon(Icons.phone_iphone),
          ],
        ),
      ],
    );
  }
}

```

