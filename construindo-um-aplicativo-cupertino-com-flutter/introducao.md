# 1. Introdução

Bem-vindo\(a\) ao laboratório do pacote Cupertino do Flutter.

Neste laboratório você vai criar um aplicativo Cupertino usando Flutter. O _SDK_ do Flutter vem com duas bibliotecas _widgets_ de estilo \(além da [biblioteca básica de _widgets_](https://api.flutter.dev/flutter/widgets/widgets-library.html)\):

* Os [_widgets_ do Material](https://api.flutter.dev/flutter/material/material-library.html) implementam o _design_ Material para iOS, Android, web e desktop.
* Os [_widgets_ do Cupertino](https://api.flutter.dev/flutter/cupertino/cupertino-library.html) implementam a linguagem de _design_ do iOS atual baseado nos guias de interface humana da Apple

Por que escrever um aplicativo Cupertino? A linguagem de _design_ do Material foi criada para qualquer plataforma, não apenas para o Android. Quando você escreve um aplicativo Material em Flutter, ele terá a aparência visual em todos os dispositivos, inclusive no iOS. Se você quer que o seu aplicativo parece como os aplicativos padrão no estilo do iOS, então você deve usar a biblioteca do Cupertino.

Tecnicamente você pode rodar um aplicativo Cupertino no Android e iOS, mas \(devido a limitações de licença\) o Cupertino não vai exibir as fontes corretas no Android. Por este motivo, use um dispositivo iOS específico quando escrever aplicativos Cupertino.

Você vai implementar um aplicativo de compras no estilo Cupertino que contém três abas: uma para a lista de produtos, uma para a busca de produtos e uma para o carrinho de compras.

### O que você vai aprender neste laboratório:

* Como construir um aplicativo em Flutter com a aparência do iOS.
* Como criar múltiplas abas e navegar entre elas.
* Como usar a biblioteca `provider` para gerenciar o estado entre as telas.



