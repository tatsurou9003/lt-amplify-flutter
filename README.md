# amplify_flutter

LT 用の Flutter プロジェクト  
### 参考
https://docs.amplify.aws/gen1/flutter/start/getting-started/setup/
## Getting Started

```
Install Amplify CLI
npm install -g @aws-amplify/cli
```
```
Consoleを通して設定
amplify configure
```
```
Amplifyプロジェクト作成
amplify init
```

```
認証でCognitoUserPoolを選択する
amplify add api
```
## Amplifyプラグインを追加して接続
``` dart
Future<void> main() async {
  WidgetsFlutterBinding.ensureInitialized();
  await _configureAmplify();
  runApp(const MyApp());
}

Future<void> _configureAmplify() async {
  try {
    //amplify codegen models` from the root of your project.
    final api = AmplifyAPI(modelProvider: ModelProvider.instance);
    final auth = AmplifyAuthCognito();

    // Add the plugins and configure Amplify for your app.
    await Amplify.addPlugins([api, auth]);
    await Amplify.configure(amplifyconfig);

    safePrint('Successfully configured');
  } on Exception catch (e) {
    safePrint('Error configuring Amplify: $e');
  }
}
```
