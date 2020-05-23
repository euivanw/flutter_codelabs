# 5. Adicionar animação no login

É hora de adicionar animação! No final deste passo, você vai criar uma animação para o `LinearProgressIndicator` que fica no topo da área de login. A animação deve ter o seguinte comportamento:

* Quando o aplicativo inicia, uma barra vermelha fina aparecerá por todo o topo da área de login.
* Quanto um campo de texto contém um texto, a barra vermelha se torna laranja e anima um terço da área de login.
* Quando dois campos de texto contém texto, a barra laranja se torna amarela e anima dois terços da área de login.
* Quando os três campos de texto contém texto, a barra amarela se torna verde e anima todo a área de login. O botão **Acessar** também ficará habilitado.

### 1. Adicione o _widget_ `IndicadorProgressoAnimado`.

Adicione todo o código abaixo no final do arquivo:

```dart
class IndicadorProgressoAnimado extends StatefulWidget {
  final double value;

  IndicadorProgressoAnimado({
    @required this.value,
  });

  @override
  State<StatefulWidget> createState() {
    return _IndicadorProgressoAnimadoState();
  }
}

class _IndicadorProgressoAnimadoState extends State<IndicadorProgressoAnimado> with SingleTickerProviderStateMixin {
  AnimationController _controle;
  Animation<Color> _animacaoCor;
  Animation<double> _curvaAnimacao;

  void initState() {
    super.initState();
    _controle = AnimationController(duration: Duration(milliseconds: 1200), vsync: this);

    var trocaCor = TweenSequence([
      TweenSequenceItem(
        tween: ColorTween(begin: Colors.red, end: Colors.orange),
        weight: 1,
      ),
      TweenSequenceItem(
        tween: ColorTween(begin: Colors.orange, end: Colors.yellow),
        weight: 1,
      ),
      TweenSequenceItem(
        tween: ColorTween(begin: Colors.yellow, end: Colors.green),
        weight: 1,
      ),
    ]);

    _animacaoCor = _controle.drive(trocaCor);
    _curvaAnimacao = _controle.drive(CurveTween(curve: Curves.easeIn));
  }

  void didUpdateWidget(oldWidget) {
    super.didUpdateWidget(oldWidget);
    _controle.animateTo(widget.value);
  }

  @override
  Widget build(BuildContext context) {
    return AnimatedBuilder(
      animation: _controle,
      builder: (context, child) => LinearProgressIndicator(
        value: _curvaAnimacao.value,
        valueColor: _animacaoCor,
        backgroundColor: _animacaoCor.value.withOpacity(0.4),
      ),
    );
  }
}
```

### 2. Use o novo _widget_ `IndicadorProgressoAnimado`.

Então, substitua o _widget_ `LinearProgressIndicator` do `Form` pelo novo _widget_ `IndicadorProgressoAnimado`.

```dart
child: Column(
  mainAxisSize: MainAxisSize.min,
  children: [
    IndicadorProgressoAnimado(              // NOVO
      value: _progressoFormulario,
    ),
```

Este _widget_ utiliza o `AnimatedBuilder` para animar o indicador de progresso para o último valor.

### 3. Execute o aplicativo.

Digite qualquer coisa nos três campos para visualizar a animação em funcionamento e então clique no botão **Acessar** trará a tela de boas-vindas.

### Observações

* Você pode utilizar um `AnimationController` para executar qualquer animação.
* `AnimatedBuild` recria a árvore de _widget_ quando o valor do `Animation` muda.
* Usando um `Tween`, você pode interpolar entre quase qualquer valor, neste caso, `Color`.

