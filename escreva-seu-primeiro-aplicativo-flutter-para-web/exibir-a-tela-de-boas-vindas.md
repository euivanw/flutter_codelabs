# 3. Exibir a tela de boas-vindas

A classe `FormularioLogin` é um _widget stateful_. Isto significa que este _widget_ armazena informações que podem mudar, como entradas de usuário ou dados de uma listagem. Partindo do pressuposto que os _widgets_  são imutáveis \(não podem ser modificados após serem criados\), o Flutter armazena informações do estado em uma classe complementar chamada de `State`. Neste laboratório, todas as suas alterações serão efetuadas na classe privada `_FormularioLoginState`.

> **Fato curioso**: O compilador do Dart garante a privacidade de qualquer identificador prefixado por um sublinhado. Para mais informações, consulte o [Guia de Estilo para um Dart Efetivo](https://dart.dev/guides/language/effective-dart/style#dont-use-a-leading-underscore-for-identifiers-that-arent-private).

Inicialmente, o seu novo arquivo `lib/main.dart`, adicione a seguinte definição de classe para o _widget_ `BoasVindasTela` após a classe `LoginTela`:

```dart
class BoasVindasTela extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: Center(
        child: Text(
          'Bem-vinda(o)!',
          style: Theme.of(context).textTheme.headline2,
        ),
      ),
    );
  }
}
```

A seguir, você irá habilitar o botão que mostra a tela e criar um método para exibi-la.

#### **1. Começando pelo início.**

Localize o método `build()` da classe `_FormularioLoginState`. É nesta parte do código que o botão acessar é construindo. Note como o botão é definido: É um `FlatButton` com uma cor de fundo azul, o texto branco que diz **Acessar** e quando pressionado, não faz nada.

#### **2. Atualize a propriedade `OnPressed`.**

Atualize a propriedade `OnPressed` para chamar o método \(ainda não existente\) que irá mostrar a tela de boas-vindas. Altere a linha `onPressed: null`, para o seguinte conteúdo:

```dart
onPressed: _mostrarTelaBoasVindas,
```

#### **3. Adicione o método `_mostrarTelaBoasVindas`.**

Corrija o erro reportado pelo analisador que diz que `_mostrarTelaBoasVindas` não está definido. Diretamente abaixo do método `build()`, adicione a seguinte função:

```dart
void _mostrarTelaBoasVindas() {
  Navigator.of(context).pushNamed('/bemvindo');
}
```

#### **4. Adicione a rota `/bemvindo`.**

Crie  conexão para exibir a nova tela. No método `build()` da classe `LoginApp`, adicione a seguinte rota, abaixo da rota `'/'`:

```dart
'/bemvindo': (context) => BoasVindasTela(),
```

#### **5. Execute o aplicativo.**

Agora, o botão Acessar deve estar habilitado. Clique nele para exibir a tela de boas-vindas. Perceba como a navegação entre as telas é animada. Você consegue este comportamento por padrão.

#### Observações

* A função `_mostrarTelaBoasVindas` é utilizada no método `build()` como uma função de retorno. Funções de retorno são frequentemente utilizadas em código Dart, e, neste caso, isto significa "chamar o método quando o botão é pressionado".
* O Flutter só tem um objeto `Navigator`. Este _widget_ gerencia as telas do Flutter \(também conhecidas como rotas e páginas\) dentro da pilha. A tela no topo da pilha é a tela exibida no momento presente. Incluir uma nova tela nesta pilha troca a visualização para a tela incluída. É por isto que a função `_mostrarTelaBoasVindas` adiciona a classe `BoasVindasTela` na pilha do `Navigator`. O usuário clica no botão e a tela de boas-vindas aparece. Da mesma forma, chamar o método `pop()` do `Navigator`, retorna para a tela anterior. Devido à navegação do Flutter ser integrada a navegação do navegador, isto acontece de forma implícita quando o usuário clica no botão de voltar do navegador.

