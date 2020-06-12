# 4. Criar a estrutura para às três abas do aplicativo

O aplicativo final apresenta três abas:

* Lista de produtos
* Busca de produtos
* Carrinho de compras

Neste passo você vai atualizar a página principal com às três abas usando o `CuppertinoTabScaffold`. Você também vai adicionar a fonte de dados que fornece a lista de itens para venda com fotos e preços.

No passo anterior, você criou a classe `PaginaPrincipalLojaCupertino` usando um `CupertinoPageScaffold`. Use esta estrutura para páginas que não tem abas. Como o aplicativo final tem três abas, precisamos trocar o `CupertinoPageScaffold` por um `CupertinoTabScaffold`.

As abas do Cupertino tem uma estrutura separa por conta do iOS, as abas inferiores são persistidas acima das rotas similares ao invés de estarem dentro das páginas.

![](https://codelabs.developers.google.com/codelabs/first-flutter-app-pt2/img/a3c16fc17be25f6c.png)Atualize o arquivo `lib/app.dart`.

Substitua a classe `PaginaPrincipalLojaCupertino` pelo código a seguir que cria a estrutura para às três abas:

```dart
class PaginaPrincipalLojaCupertino extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return CupertinoTabScaffold(
      tabBar: CupertinoTabBar(
        items: const <BottomNavigationBarItem>[
          BottomNavigationBarItem(
            icon: Icon(CupertinoIcons.home),
            title: Text('Produtos'),
          ),
          BottomNavigationBarItem(
            icon: Icon(CupertinoIcons.search),
            title: Text('Busca'),
          ),
          BottomNavigationBarItem(
            icon: Icon(CupertinoIcons.shopping_cart),
            title: Text('Carrrinho'),
          ),
        ],
      ),
      tabBuilder: (context, index) {
        CupertinoTabView returnValue;
        switch (index) {
          case 0:
            returnValue = CupertinoTabView(
              builder: (context) {
                return CupertinoPageScaffold(
                  child: ProdutosTab(),
                );
              },
            );
            break;
          case 1:
            returnValue = CupertinoTabView(
              builder: (context) {
                return CupertinoPageScaffold(
                  child: BuscaTab(),
                );
              },
            );
            break;
          case 2:
            returnValue = CupertinoTabView(
              builder: (context) {
                return CupertinoPageScaffold(
                  child: CarrinhoTab(),
                );
              },
            );
            break;
        }
        return returnValue;
      },
    );
  }
}
```

#### Observações:

* Uma `CupertinoTabBar` necessita de pelo menos dois itens ou um erro será lançado.
* O `TabBuilder` é responsável por garantir que a aba definida seja construída. Neste caso, ele chama o construtor da classe para criar cada uma das respectivas abas, envolvendo todos os três `CupertinoTabBiew` e o `CupertinoPageScaffold`.

![](https://codelabs.developers.google.com/codelabs/first-flutter-app-pt2/img/a3c16fc17be25f6c.png)Adicione as classes com os esboços do conteúdo das novas abas.

Crie um arquivo chamado `lib/produtos_tab.dart` para a primeira aba que compila corretamente, mas somente exibe uma tela em branco. Use o conteúdo a seguir:

```dart
import 'package:flutter/cupertino.dart';
import 'package:provider/provider.dart';

import 'modelo/modelo_estado_app.dart';

class ProdutosTab extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Consumer<ModeloEstadoApp>(
      builder: (context, model, child) {
        return const CustomScrollView(
          slivers: <Widget>[
            CupertinoSliverNavigationBar(
              largeTitle: Text('Loja Cupertino'),
            ),
          ],
        );
      },
    );
  }
}
```

#### Observações:

* A aba da lista de produtos é um _widget_ _stateless_.
* A classe `Consumer`, do pacote `provider` auxilia com o gerenciamento de estados. Veremos mais sobre isto no futuro.
* Há duas variantes da barra de navegação do iOS. O tipo estático curto comum visto desde iOS 1 e o título grande rolável introduzido no iOS 11. Esta página implementa a última dentro de um `CustomScrollView` com um _widget_ `CupertinoSliversNavigationBar`.

![](https://codelabs.developers.google.com/codelabs/first-flutter-app-pt2/img/a3c16fc17be25f6c.png)Adicione o esboço da página de busca

Crie um arquivo chamado `lib/busca_tab.dart` que compila corretamente, mas só exibe uma tela em branco. Use o conteúdo a seguir:

```dart
import 'package:flutter/cupertino.dart';

class BuscaTab extends StatefulWidget {
  @override
  _BuscaTabState createState() {
    return _BuscaTabState();
  }
}

class _BuscaTabState extends State<BuscaTab> {
  @override
  Widget build(BuildContext context) {
    return const CustomScrollView(
      slivers: <Widget>[
        CupertinoSliverNavigationBar(
          largeTitle: Text('Busca'),
        ),
      ],
    );
  }
}
```

#### Observações:

* A aba de busca é um _widget_ _statefull_, pois, conforme o usuário realiza as buscas, a lista de resultados é alterada.

![](https://codelabs.developers.google.com/codelabs/first-flutter-app-pt2/img/a3c16fc17be25f6c.png)Adicione o esboço da página do carrinho de compras.

Crie um arquivo chamado `lib/carrinho_tab.dart` que compila corretamente, mas só exibe uma tela em branco. Use o conteúdo a seguir:

```dart
import 'package:flutter/cupertino.dart';
import 'package:provider/provider.dart';

import 'modelo/modelo_estado_app.dart';

class CarrinhoTab extends StatefulWidget {
  @override
  _CarrinhoTabState createState() {
    return _CarrinhoTabState();
  }
}

class _CarrinhoTabState extends State<CarrinhoTab> {
  @override
  Widget build(BuildContext context) {
    return Consumer<ModeloEstadoApp>(
      builder: (context, model, child) {
        return const CustomScrollView(
          slivers: <Widget>[
            CupertinoSliverNavigationBar(
              largeTitle: Text('Carrinho de Compras'),
            ),
          ],
        );
      },
    );
  }
}
```

#### Observações:

* A aba do carrinho de compras é um _widget statefull_ porque ela armazena a lista de compras e as informações do cliente.
* Esta página também usa um `CustomScrollView`.

![](https://codelabs.developers.google.com/codelabs/first-flutter-app-pt2/img/a3c16fc17be25f6c.png)Atualize o arquivo `lib/app.dart`.

Atualize as declarações dos _imports_ no arquivo `lib/app.dart` para incluir os três novos _widgets_:

```dart
import 'package:flutter/cupertino.dart';
import 'package:flutter/services.dart';

import 'busca_tab.dart'; //NOVO
import 'carrinho_tab.dart'; //NOVO
import 'produtos_tab.dart'; //NOVO
```

Na segunda parte deste passo, que iremos fazer na próxima página, você vai adicionar o código para o gerenciamento e compartilhamento de estado entre as abas.

