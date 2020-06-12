# 7. Adicionar a busca de produtos

Neste passo você vai construir a aba de busca e adicionar a habilidade de buscar produtos.

![](https://codelabs.developers.google.com/codelabs/first-flutter-app-pt2/img/a3c16fc17be25f6c.png)Atualize o arquivo `lib/busca_tab.dart`.

Adicione os _imports_ para as classes que a aba de busca vai usar:

```dart
import 'package:flutter/cupertino.dart';
import 'package:provider/provider.dart';

import 'modelo/modelo_estado_app.dart';
import 'barra_busca.dart';
import 'linha_item_produto.dart';
import 'styles.dart';
```

![](https://codelabs.developers.google.com/codelabs/first-flutter-app-pt2/img/a3c16fc17be25f6c.png)Atualize o método `build()` da classe `_BuscaTabState`.

Inicialize o modelo e substitua o `CustomScrollView` por um componente individual para busca e listagem:

```dart
class _BuscaTabState extends State<BuscaTab> {
  @override
  Widget build(BuildContext context) {
    final model = Provider.of<ModeloEstadoApp>(context);
    final results = model.search(_termos);

    return DecoratedBox(
      decoration: const BoxDecoration(
        color: Styles.fundoScaffold,
      ),
      child: SafeArea(
        child: Column(
          children: [
            _construirCaixaBusca(),
            Expanded(
              child: ListView.builder(
                itemBuilder: (context, index) => LinhaItemProduto(
                  indice: index,
                  produto: results[index],
                  ultimoItem: index == results.length - 1,
                ),
                itemCount: results.length,
              ),
            ),
          ],
        ),
      ),
    );
  }
}
```

#### Observações:

* Estamos recriando a experiência de busca no estilo do iOS, mas temos bastante espaço para personalizar a experiência do usuário.

![](https://codelabs.developers.google.com/codelabs/first-flutter-app-pt2/img/a3c16fc17be25f6c.png)Adicione as variáveis de suporte, funções e métodos na classe `_BuscaTabState`.

Isto inclui os métodos `initState()`, `dispose()`, `_aoMudarTexto()` e `_construirCaixaBusca()`, conforme a seguir:

```dart
class _BuscaTabState extends State<BuscaTab> {
  TextEditingController _controller;
  FocusNode _focusNode;
  String _termos = '';

  @override
  void initState() {
    super.initState();
    _controller = TextEditingController()..addListener(_aoMudarTexto);
    _focusNode = FocusNode();
  }

  @override
  void dispose() {
    _focusNode.dispose();
    _controller.dispose();
    super.dispose();
  }

  void _aoMudarTexto() {
    setState(() {
      _termos = _controller.text;
    });
  }

  Widget _construirCaixaBusca() {
    return Padding(
      padding: const EdgeInsets.all(8),
      child: BarraBusca(
        controller: _controller,
        focusNode: _focusNode,
      ),
    );
  }
  ...
}
```

#### Observações:

* A classe `_BuscaTabState` é onde armazenamos o estado de uma busca em específico. Nesta implementação armazenamos os termos utilizados na busca e engatamos na `ModeloEstadoApp` para preencher a funcionalidade de busca. No caso onde implementarmos uma API, aqui é um bom lugar para realizar o acesso à rede relativo a busca.

![](https://codelabs.developers.google.com/codelabs/first-flutter-app-pt2/img/a3c16fc17be25f6c.png)Adicione a classe `BarraBusca`.

Crie um arquivo chamado `lib/barra_busca.dart`. A classe `BarraBusca` lida com a busca atual da lista de produtos. Alimente o arquivo com o conteúdo a seguir:

```dart
import 'package:flutter/cupertino.dart';
import 'package:flutter/widgets.dart';

import 'styles.dart';

class BarraBusca extends StatelessWidget {
  const BarraBusca({
    @required this.controller,
    @required this.focusNode,
  });

  final TextEditingController controller;
  final FocusNode focusNode;

  @override
  Widget build(BuildContext context) {
    return DecoratedBox(
      decoration: BoxDecoration(
        color: Styles.fundoPesquisa,
        borderRadius: BorderRadius.circular(10),
      ),
      child: Padding(
        padding: const EdgeInsets.symmetric(
          horizontal: 4,
          vertical: 8,
        ),
        child: Row(
          children: [
            const Icon(
              CupertinoIcons.search,
              color: Styles.iconePesquisaCor,
            ),
            Expanded(
              child: CupertinoTextField(
                controller: controller,
                focusNode: focusNode,
                style: Styles.textoPesquisa,
                cursorColor: Styles.cursorPesquisaCor,
                decoration: BoxDecoration(),
              ),
            ),
            GestureDetector(
              onTap: controller.clear,
              child: const Icon(
                CupertinoIcons.clear_thick_circled,
                color: Styles.iconePesquisaCor,
              ),
            ),
          ],
        ),
      ),
    );
  }
}
```

![](https://codelabs.developers.google.com/codelabs/first-flutter-app-pt2/img/a3c16fc17be25f6c.png)Rode o aplicativo. Selecione a aba de busca e informe "_shirt_" na caixa de busca. Você deve visualizar uma lista de 5 produtos que contém "_shirt_" no nome.

![](../.gitbook/assets/lab5_step7%20%281%29.png)

#### Problemas?

Se o seu aplicativo não estiver rodando corretamente, utilize o código dos links a seguir, para voltar aos trilhos.‌

* [lib/barra\_busca.dart](https://github.com/ivanwhm/flutter_codelabs_lab5/blob/f1cfc90764a7ef1c3ed40036e4438905754672a3/lib/barra_busca.dart)
* [lib/busca\_tab.dart](https://github.com/ivanwhm/flutter_codelabs_lab5/blob/f1cfc90764a7ef1c3ed40036e4438905754672a3/lib/busca_tab.dart)

