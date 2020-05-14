# 5. Adicionar um widget stateful

_Widgets_ _stateless_ são imutáveis, isto significa que suas propriedades não podem sofrer alterações - são todos valores finais.

_Widgets stateful_ mantém o estado que pode mudar durante o ciclo de vida de um **widget**. Implementar um _widget stateful_ requer pelo menos duas classes: 1\) uma `StatefulWidget` que cria uma instância de uma `State`. O objeto `StatefulWidget` é, por si só, imutável, mas o objeto `State` persiste ao longo da vida do _widget_.

Neste passo, você irá adicionar um _widget stateful_ chamado `PalavrasRandomicas` que cria a sua classe `State` `PalavrasRandomicasState`. Você irá usar a classe `PalavrasRandomicas` como filha do _widget_ _stateless_ `MyApp`.

Crie uma classe `minimal state`. Você pode ir em qualquer lugar fora da classe `MyApp`, mas a solução irá incluir no final do arquivo. Adicione o seguinte texto:

```dart
class PalavrasRandomicasState extends State<PalavrasRandomicas> {
  // TODO Adicionar o método build
}
```

Note a declaração `State<PalavrasRandomicas>`. Isto indica que você está utilizando a classe genérica `State` que foi especializada ao usar `PalavrasRandomicas`. A maior parte da lógica e estado de um aplicativo reside aqui - ele mantém o estado para o _widget_ `PalavrasRandomicas`. Esta classe salva a lista de pares de palavras geradas, que irá crescer infinitamente conforme o usuário rolar a página e favoritar pares de palavras \(na [parte 2](https://ivanwhm.gitbook.io/laboratorios-de-codigo-do-flutter/escreva-seu-primeiro-aplicativo-flutter-parte-2/introducao)\) quando o usuário adicionar ou removê-las da lista tocando no ícone de coração.

`PalavrasRandomicasState` depende da classe `PalavrasRandomicas`. Você irá adicioná-la em seguida.

![](https://codelabs.developers.google.com/codelabs/first-flutter-app-pt2/img/a3c16fc17be25f6c.png) Adicione o _widget stateful_ `PalavrasRandomicas` no arquivo `main.dart`. O _widget_ `PalavrasRandomicas` faz muito pouco além de criar a classe `State:`

```dart
class PalavrasRandomicas extends StatefulWidget {
  @override
  PalavrasRandomicasState createState() => PalavrasRandomicasState();
}
```

Após adicionar a classe de estado, a IDE reclama que na classe está faltando o método `build`. A seguir, você irá adicionar um método `build` básico, que irá gerar um par de palavras movendo o código gerado na classe `MyApp` para a classe `PalavrasRandomicasState`.

![](https://codelabs.developers.google.com/codelabs/first-flutter-app-pt2/img/a3c16fc17be25f6c.png) Adicione o método `build()` na classe `PalavrasRandomicasState`, como mostrado a seguir:

```dart
class PalavrasRandomicasState extends State<PalavrasRandomicas> {
  @override                                    // adicione desta linha
  Widget build(BuildContext context) {
    final parDePalavras = WordPair.random();
    return Text(parDePalavras.asPascalCase);
  }                                            // até esta linha
}
```

![](https://codelabs.developers.google.com/codelabs/first-flutter-app-pt2/img/a3c16fc17be25f6c.png) Remova a geração de palavras do código da classe `MyApp` fazendo as seguintes alterações:

```dart
class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    //final parDePalavras = WordPair.random(); //exclua esta linha
    return MaterialApp(
      title: 'Bem-vindo(a) ao Flutter',
      home: Scaffold(
        appBar: AppBar(
          title: const Text('Bem-vindo(a) ao Flutter'),
        ),
        body: Center(
          child: PalavrasRandomicas(), //substitua esta linha
        ),
      ),
    );
  }
}
```

Salve as alterações para a execução do _hot reload_. O aplicativo deve funciona como antes, exibindo um par de palavras cada vez que você acionar o _hot reload_ ou salvar o aplicativo.

> **Dica**: Se você visualizar o seguinte aviso ao acionar o _hot reload_, considere reiniciar o aplicativo:
>
> **Reloading...  
> Not all changed program elements ran during view reassembly; consider restarting.**
>
> Isto pode ser um falso positivo, porém reiniciar o aplicativo garante que as alterações na interface foram refletidas.

#### Problemas?

Se o seu aplicativo não estiver rodando corretamente, utilize o código dos links a seguir, para voltar aos trilhos.‌

* [​lib/main.dart](https://github.com/ivanwhm/flutter_codelabs_lab1/commit/f1a8397752ca0f4d85ae3c0e1966b4c6c810f425)

