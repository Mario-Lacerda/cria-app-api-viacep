# **Desafio Dio - Criando um App Flutter do Zero Para o Consumo da API do ViaCEP**



O ViaCEP é uma API que fornece informações de CEPs de todo o Brasil. Neste tutorial, vamos criar um aplicativo Flutter para consumir a API do ViaCEP.



## Pré-requisitos

Para este tutorial, você precisará dos seguintes pré-requisitos:

- Flutter SDK

- Dart SDK

- Visual Studio Code ou outro editor de código

  

## Passo 1: Criar um novo projeto Flutter

Primeiramente, precisamos criar um novo projeto Flutter. Abra o Visual Studio Code e execute o seguinte comando no terminal:

```plaintext
flutter create viacep
```

Isso criará um novo diretório chamado `viacep`. Entre no diretório e abra o arquivo `pubspec.yaml`. Adicione a dependência da API do ViaCEP ao arquivo `pubspec.yaml`:

```plaintext
dependencies:
  viacep: ^1.0.0
```



## Passo 2: Implementar a tela inicial

Agora vamos implementar a tela inicial do aplicativo. Abra o arquivo `lib/main.dart` e adicione o seguinte código:

```plaintext
import 'package:flutter/material.dart';
import 'package:viacep/viacep.dart';

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'ViaCEP',
      home: HomePage(),
    );
  }
}

class HomePage extends StatefulWidget {
  @override
  _HomePageState createState() => _HomePageState();
}

class _HomePageState extends State<HomePage> {
  String _cep = '';

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('ViaCEP'),
      ),
      body: Column(
        children: [
          Padding(
            padding: const EdgeInsets.all(8.0),
            child: TextFormField(
              decoration: InputDecoration(
                labelText: 'CEP',
              ),
              onChanged: (cep) {
                setState(() {
                  _cep = cep;
                });
              },
            ),
          ),
          FutureBuilder<ViaCEP>(
            future: ViaCEP.getViaCEP(_cep),
            builder: (context, snapshot) {
              if (snapshot.hasData) {
                return Text(snapshot.data.logradouro);
              } else if (snapshot.hasError) {
                return Text(snapshot.error.toString());
              } else {
                return CircularProgressIndicator();
              }
            },
          ),
        ],
      ),
    );
  }
}
```

Neste código, criamos uma classe `HomePage` que é responsável por exibir a tela inicial do aplicativo. A tela inicial tem um campo de texto para o CEP e um botão para fazer a busca. Quando o usuário faz a busca, o aplicativo faz uma requisição à API do ViaCEP e obtém as informações do CEP. As informações do CEP são exibidas em uma caixa de texto abaixo do campo de texto.

## Passo 3: Executar o aplicativo

Agora que o aplicativo está implementado, vamos executá-lo. Execute o seguinte comando no terminal:

plaintext

![Done](chrome-extension://igpdmclhhlcpoindmhkhillbfhdgoegm/b3baca6de20012788f7d.svg)![Copy](chrome-extension://igpdmclhhlcpoindmhkhillbfhdgoegm/7120b68615ebe4b28075.svg)

```plaintext
flutter run
```

O aplicativo será aberto no seu emulador ou dispositivo Android. Você pode digitar um CEP no campo de texto e clicar no botão para fazer a busca. As informações do CEP serão exibidas na caixa de texto abaixo do campo de texto.

## Conclusão

Neste tutorial, aprendemos a criar um aplicativo Flutter para consumir a API do ViaCEP. A API do ViaCEP é uma ótima maneira de obter informações de CEP de todo o Brasil. Com o Flutter, podemos criar aplicativos móveis modernos e de alta qualidade para Android e iOS.

Para obter mais informações sobre a API do ViaCEP, consulte a documentação oficial. Para obter mais informações sobre o Flutter, consulte a documentação oficial.







# viacep

A new Flutter project.

## Getting Started

This project is a starting point for a Flutter application.

A few resources to get you started if this is your first Flutter project:

- [Lab: Write your first Flutter app](https://docs.flutter.dev/get-started/codelab)
- [Cookbook: Useful Flutter samples](https://docs.flutter.dev/cookbook)

For help getting started with Flutter development, view the
[online documentation](https://docs.flutter.dev/), which offers tutorials,
samples, guidance on mobile development, and a full API reference.
