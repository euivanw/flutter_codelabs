# 4. Ativar rastreamento de progresso de login

Esta tela de login tem três campos. A seguir, você vai ativar a habilidade de rastrear o progresso do usuário no preenchimento dos campos do formulário e atualizar a interface do aplicativo quando o formulário está completo.

> **Nota**: Este exemplo não valida a precisão das entradas do usuário. Isto é algo que você pode adicionar mais tarde utilizado validação de formulário, se você gostar.

#### 1. Adicione o método para atualizar `_progressoFormulario`.

Na classe `_FormularioLoginState`, adicione um novo método chamado _`_`_`atualizaProgressoFormulario()`:

```dart
void _atualizaProgressoFormulario() {
  var progresso = 0.0;
  var controles = [
    _primeiroNomeTextController,
    _sobrenomeTextController,
    _nomeDeUsuarioTextController,
  ];

  for (var controller in controles) {
    if (controller.value.text.isNotEmpty) {
      progresso += 1 / controles.length;
    }
  }

  setState(() {
    _progressoFormulario = progresso;
  });
}
```

Este método atualiza a variável `_progressoFormulario` baseado no número de campos preenchidos.

#### 2. Chame o método `_atualizaProgressoFormulario()` quando o formulário muda.

No método `build()` da classe `_FormularioLoginState`, adicione a função de retorno para argumento `onChanged` do _widget_ `Form`. Adicione o código abaixo, marcado como _NOVO_:

```dart
...
return Form(
  onChanged: () => _atualizaProgressoFormulario(), // NOVO
  child: Column(
...
```

#### 3. Atualize a propriedade `onPressed` \(novamente\).

No passo 1, você modificou a propriedade `onPressed` do botão **Acessar** para exibir a tela de boas-vindas. Agora, atualize o botão para mostrar a tela de boas-vindas somente quando o formulário estiver completamente preenchido:

```dart
FlatButton(
  color: Colors.blue,
  textColor: Colors.white,
  onPressed: _progressoFormulario == 1 ? _mostrarTelaBoasVindas : null, // ATUALIZADO
  child: Text('Acessar'),
),
```

#### 4. Execute o aplicativo.

O botão **Acessar** está inicialmente desabilitado, mas fica habilitado quando os três campos de texto tiverem algum conteúdo.

#### Observações

* Chamando o método `setState()` do _widget_, diz ao Flutter que ele precisa ser atualizado na tela. Então, o Flutter se desfaz do _widget_ imutável anterior \(e seus filhos\), cria um \(com a sua árvore de _widgets_ filhos que o acompanha\) e o renderiza na tela. Para que este trabalho fique perfeito, o Flutter precisa ser rápido. A nova árvore de _widgets_ precisa ser criada e renderizada na tela em menos de 1/60 de segundos, para criar uma transição visual suave - especialmente para a animação. Por sorte, o Flutter é rápido.
* O campo `_progressoFormulario` é definido com um valor de ponto flutuante e, é atualizado no método `_atualizaProgressoFormulario`. Quando os três campos estiverem preenchidos, o valor do campo `_progressoFormulario` será `1.0`. Quando o campo `_progressoFormulario` for igual a `1.0`, a função de retorno `onPressed` é definida para o método `_mostrarTelaBoasVindas`. O botão é habilitado quando a argumento `onPressed` for não nulo.
* Note que o método `_atualizaProgressoFormulario` chama a função `setState()`. Esta, chama uma função anônima e ela tem a seguinte sintaxe:

```dart
nomeDoMedodo(() {...}};
```

* Onde, `nomeDoMetodo` é uma função nomeada que tem uma função de retorno anônima como um argumento.
* A sintaxe do Dart do último passo que exibe a página de boas-vindas é:

```dart
onPressed: _progressoFormulario == 1 ? _mostrarTelaBoasVindas : null,
```

* Esta é a atribuição condicional do Dart e tem a seguinte sintaxe: `condicao ? empressao1 : expressao2`. Se a expressão `_progressoFormulario == 1` __for verdadeira, então a expressão completa resulta no valor do lado esquerdo do `:`, que neste caso é o método __`_mostrarTelasBoasVindas`.

