# MediaService-SignalRChat-Sample

Azure Media Services に SignalR ベースのチャットシステムを載せたサンプルです。
最終的に完成する物は https://katsujim-mediaservice-sample.azurewebsites.net/ でご確認いただけます。

ご入力いただくもの

- ストリーミングURL： Media Services で発行されたURL （例： //amssamples.streaming.mediaservices.windows.net/3b970ae0-39d5-44bd-b3a3-3136143d6435/AzureMediaServicesPromo.ism/manifest ）
- チャットサーバーのURL： https://katsujim-signalr-functionapp.azurewebsites.net 

## 事前に準備するリソース

はじめに、Azure サブスクリプション（初めての方は[無料仕様版](https://azure.microsoft.com/ja-jp/free/)もご利用いただけます。）をご用意ください。
次に、[Azure ポータル](https://portal.azure.com)へアクセスし、以下に示すサービスを作成してください。

- Media Services
- App Services
- Functions（日本語では関数アプリと表記）
- SignalR Services

また、下記ボタンを利用いただきますと、上記リソースが自動的に作成されます。サブスクリプションやリソースグループ・各種リソースの名前を入力すると自動的にリソースがデプロイされます。

[![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Ftenjoufire%2FMediaService-SignalRChat-Sample%2Fmaster%2Ftemplate.json)

## Webアプリのデプロイ

フロントのWebアプリは[こちら](https://github.com/tenjoufire/MediaService-SignalRChat-Sample/tree/master/front)にあるindex.htmlファイルが実体です。実際にAzure上のWebアプリにデプロイする方法は複数用意されており、例えば、[FTPを使ったデプロイ](https://docs.microsoft.com/ja-jp/azure/app-service/deploy-ftp)や[継続的デプロイ](https://docs.microsoft.com/ja-jp/azure/app-service/deploy-continuous-deployment)がご利用いただけます。チャットのログを残す際は、index.html ファイルの中にある {YOUR_APPLICATION_INSIGHTS_INSTRUMENTATIONKEY} を、デプロイ先のWebアプリに紐づいた Application Insights のキーを入れてください。

## Functions のデプロイ

チャットの実装は SignalR Service と Functions を利用しており、Functions の実体は[こちら](https://github.com/tenjoufire/MediaService-SignalRChat-Sample/tree/master/back)にあるプロジェクトが実体です。

GitHubからソースコードをダウンロードした後に Visual Studio もしくは Visual Studio Code で Functions のプロジェクトを開き、準備した Azure 上の Functions App へデプロイしてください。ローカルでの Functions 開発やデプロイに関する詳しい情報は [Visual Studio 版](https://docs.microsoft.com/ja-jp/azure/azure-functions/functions-develop-vs)や [Visual Studio Code 版](https://docs.microsoft.com/ja-jp/azure/azure-functions/functions-develop-vs-code?tabs=csharp)をご確認ください。

## 各種アプリ構成の設定

