# MediaService-SignalRChat-Sample

Azure Media Services に SignalR ベースのチャットシステムを載せたサンプルです。

## 事前に準備するリソース

はじめに、Azure サブスクリプション（初めての方は[無料仕様版](https://azure.microsoft.com/ja-jp/free/)もご利用いただけます。）をご用意ください。
次に、[Azure ポータル](https://portal.azure.com)へアクセスし、以下に示すサービスを作成してください。

- Media Services
- App Services
- Functions（日本語では関数アプリと表記）
- SignalR Services

## Webアプリのデプロイ

フロントのWebアプリは[こちら](https://github.com/tenjoufire/MediaService-SignalRChat-Sample/tree/master/front)にあるindex.htmlファイルが実体です。実際にAzure上のWebアプリにデプロイする方法は複数用意されており、例えば、[FTPを使ったデプロイ](https://docs.microsoft.com/ja-jp/azure/app-service/deploy-ftp)や[継続的デプロイ](https://docs.microsoft.com/ja-jp/azure/app-service/deploy-continuous-deployment)がご利用いただけます。




## テンプレートデプロイ（実装中）

以下のボタンはまだ未完成です。正しくリソースがデプロイされません。

[![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Ftenjoufire%2FMediaService-SignalRChat-Sample%2Fmaster%2Ftemplate.json)
