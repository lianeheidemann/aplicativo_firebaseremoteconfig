# aplicativo_firebaseremoteconfig

Flutter app de exemplo integrando **Firebase Remote Config** para controlar a UI remotamente (cor de fundo e imagem de propaganda).

## Funcionalidades

- Inicializa o Firebase (via `firebase_core`).
- Busca e ativa configurações do **Firebase Remote Config** na inicialização.
- Controla:
  - **Cor de fundo** (Remote Config key: `cor_fundo`)
  - **Imagem de propaganda** (Remote Config key: `propaganda`)
- Permite atualizar manualmente as configurações pelo botão de refresh.
- Botão para abrir um link externo (`https://www.google.com`).

## Tecnologias

- Flutter
- Firebase:
  - `firebase_core`
  - `firebase_remote_config`
- `url_launcher` para abrir URL externa

## Configuração do Firebase

O projeto utiliza o arquivo gerado pelo FlutterFire para as opções padrão:

- `lib/firebase_options.dart`

> Observação: no arquivo `firebase_options.dart` há suporte/validações para múltiplas plataformas, mas os valores concretos estão configurados para **Android** (via `android/app/google-services.json`).

### Android

- `android/app/google-services.json`

## Remote Config (chaves e comportamento)

As chaves abaixo são definidas com defaults em `lib/main.dart`:

- `cor_fundo`
  - Tipo esperado: **string** com cor em formato **hex** `#RRGGBB`
  - Default: `#FFFFFF`
  - Efeito: define a cor de fundo do `Scaffold`

- `propaganda`
  - Tipo esperado: **string** com valores conhecidos
  - Defaults: `default`
  - Efeitos:
    - `propaganda = "alternativa"` → usa `assets/images/propaganda_alt.png`
    - Qualquer outro valor → usa `assets/images/propaganda.png`

## Como executar localmente

1. Instale as dependências:

   ```bash
   flutter pub get
   ```

2. Configure seu projeto Firebase (se necessário):
   - Certifique-se de ter o `google-services.json` em `android/app/`.

3. Execute no Android:

   ```bash
   flutter run
   ```

## Como testar o Remote Config

No console do Firebase:

1. Vá em **Remote Config** → crie um fluxo/alteração.
2. Defina valores (exemplos):
   - `cor_fundo`: `#FF0000`
   - `propaganda`: `alternativa`
3. Publique e aguarde propagação.
4. Abra o app e, se necessário, toque no botão de refresh.

## Estrutura do projeto

- `lib/main.dart`
  - Implementa a lógica de carregamento do Remote Config (`setDefaults`, `fetchAndActivate`).
  - Monta a UI usando os valores recebidos.

- `assets/images/`
  - `propaganda.png`
  - `propaganda_alt.png`

- `firebase.json`
  - Configurações do Firebase para o projeto.

## Dependências (principais)

- `firebase_core`
- `firebase_remote_config`
- `url_launcher`

---

Feito para demonstrar um fluxo simples e funcional de **Remote Config** controlando parâmetros visuais do app.
