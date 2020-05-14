# 3. Obter o código inicial

Se você trabalhou na parte 1 deste laboratório, você já tem o código inicial, o projeto `nome_empresa`. Você pode ir para o próximo passo.

Se você não tem o projeto `nome_empresa`, não tema, você pode obtê-lo usando as seguintes instruções.

![](https://codelabs.developers.google.com/codelabs/first-flutter-app-pt2/img/a3c16fc17be25f6c.png) Crie um aplicativo simples através do modelo do Flutter usando as instruções da página [Criar um aplicativo](https://flutter.dev/docs/get-started/test-drive?tab=vscode). Informe `nome_empresa` \(ao invés de _`myapp`_\) como nome do projeto.

![](https://codelabs.developers.google.com/codelabs/first-flutter-app-pt2/img/a3c16fc17be25f6c.png) Exclua todo o código do arquivo `lib/main.dart`. Substitua com o código [deste arquivo](https://github.com/ivanwhm/flutter_codelabs_lab1/blob/master/lib/main.dart), que irá exibir uma lista infinita e carregada preguiçosamente de sugestões para nomes de empresas iniciais.

![](https://codelabs.developers.google.com/codelabs/first-flutter-app-pt2/img/a3c16fc17be25f6c.png) Atualize o arquivo `pubspec.yaml` adicionando o pacote English Words, conforme exibido a seguir:

```yaml
dependencies:
  flutter:
    sdk: flutter

  cupertino_icons: ^0.1.2
  english_words: ^3.1.0    # adicione esta linha
```

O pacote English Words gera pares de nomes de palavras de forma aleatória, que irão ser utilizadas como potenciais nomes de empresas iniciais.

![](https://codelabs.developers.google.com/codelabs/first-flutter-app-pt2/img/a3c16fc17be25f6c.png) Ao salvar as alterações no arquivo `pubspec.yaml`, o Visual Studio Code irá copiar o pacote para dentro do seu projeto. Você poderá ver por meio do console:

```bash
flutter packages get
Running "flutter packages get" in startup_namer...
Process finished with exit code 0
```

![](https://codelabs.developers.google.com/codelabs/first-flutter-app-pt2/img/a3c16fc17be25f6c.png) Execute o aplicativo. Role o quando você quiser, visualizando de forma contínua o fornecimento de sugestões de nomes.

