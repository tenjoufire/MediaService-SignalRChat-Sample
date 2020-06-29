# MediaService-SignalRChat-Sample

Azure Media Services に SignalR ベースのチャットシステムを載せたサンプルです。
最終的に完成する物は https://katsujim-mediaservice-sample.azurewebsites.net/ でご確認いただけます。

ご入力いただくもの

- ストリーミングURL： Media Services で発行されたURL （例： //amssamples.streaming.mediaservices.windows.net/3b970ae0-39d5-44bd-b3a3-3136143d6435/AzureMediaServicesPromo.ism/manifest ）
- チャットサーバーのURL： https://katsujim-signalr-functionapp.azurewebsites.net 

## 事前に準備するリソース

はじめに、Azure サブスクリプション（初めての方は[無料試用版](https://azure.microsoft.com/ja-jp/free/)もご利用いただけます。）をご用意ください。
次に、[Azure ポータル](https://portal.azure.com)へアクセスし、以下に示すサービスを作成してください。

- App Services
- Functions（日本語では関数アプリと表記）
- SignalR Services
- Media Services (必須ではありません、ご自身でご用意された動画を利用する場合は作成してください。)

また、下記ボタンを利用いただきますと、上記リソース（Media Services を除く）が自動的に作成されます。サブスクリプションやリソースグループ・各種リソースの名前を入力すると自動的にリソースがデプロイされます。

[![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Ftenjoufire%2FMediaService-SignalRChat-Sample%2Fmaster%2Ftemplate.json)

## Webアプリのデプロイ

フロントの Web アプリは[こちら](https://github.com/tenjoufire/MediaService-SignalRChat-Sample/tree/master/front)にある index.html ファイルが実体です。実際に Azure 上の Web アプリにデプロイする方法は複数用意されており、例えば、[FTP を使ったデプロイ](https://docs.microsoft.com/ja-jp/azure/app-service/deploy-ftp)や[継続的デプロイ](https://docs.microsoft.com/ja-jp/azure/app-service/deploy-continuous-deployment)がご利用いただけます。チャットのログを残す際は、index.html ファイルの中にある {YOUR_APPLICATION_INSIGHTS_INSTRUMENTATIONKEY} を、デプロイ先の Web アプリに紐づいた Application Insights のキーを入れてください。

## Functions のデプロイ

チャットの実装は SignalR Service と Functions を利用しており、Functions の実体は[こちら](https://github.com/tenjoufire/MediaService-SignalRChat-Sample/tree/master/back)にあるプロジェクトが実体です。

GitHubからソースコードをダウンロードした後に Visual Studio もしくは Visual Studio Code で Functions のプロジェクトを開き、準備した Azure 上の Functions App へデプロイしてください。ローカルでの Functions 開発やデプロイに関する詳しい情報は [Visual Studio 版](https://docs.microsoft.com/ja-jp/azure/azure-functions/functions-develop-vs)や [Visual Studio Code 版](https://docs.microsoft.com/ja-jp/azure/azure-functions/functions-develop-vs-code?tabs=csharp)をご確認ください。

## 各種アプリ構成の設定

### Functions の構成設定

はじめに、 SignalR サービス -> Keys -> Primary CONNECTION STRING から SignalR の接続文字列をコピーしてください。次に Functions App の左のメニューから「構成」をクリックし、アプリケーション設定の画面へアクセスしてください。ここで、新しいアプリケーション設定を選択し、

- 名前： AzureSignalRConnectionString
- 値： SignalR サービスでコピーした接続文字列を貼り付け

を入力し、「OK」を押してください。

### CORS の設定

Functions App の左のメニューから「CORS」をクリックし、デフォルトで入力されている値をすべて削除してください。その後、Web アプリのURLを許可される元のドメインに追加し、資格情報の要求にある「Access-Control-Allow-Credentials を有効にする」にチェックをつけて、保存してください。
