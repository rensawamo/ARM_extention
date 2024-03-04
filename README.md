## Bicep および  ARM テンプレートを拡張する


### ARM テンプレート
Azure Resource Manager (ARM) テンプレートは、Azureのリソースをデプロイおよび管理するための宣言型の言語で記述されたファイル。JSON形式で書かれており、インフラストラクチャをコードとして定義することで、一貫性と再現性のある環境構築を実現する。ARMテンプレートを使用することで、複数のリソースを関連付けて、依存関係を考慮しながら一括でデプロイ、管理、および構成することができる。


#### ストレージアカウント
Azure Storageサービスの最上位に位置する管理単位で、Azure上でデータを保存するための基本的なコンテナ。ストレージアカウント内には、Blob Storage（オブジェクトストレージ）、File Storage（共有ファイルシステム）、Queue Storage（メッセージキュー）、Table Storage（NoSQLデータベース）など、さまざまな種類のデータサービスを含む。

### ストレージコンテイナー
Blob Storage内で使用される概念で、Blob（バイナリラージオブジェクト）と呼ばれるファイルやデータの集まりをグループ化するための単位。コンテイナーは、ストレージアカウント内に作成され、複数のBlobを保持する。



 ### 環境変数の追加
 ```sh
environmentVariables: [
]
```

### テンプレートパラメータの追加
```sh
@description('List of files to copy to application storage account.')
param filesToCopy array
```


### リソースグループの作成
```sh
resourceGroupName="learndeploymentscript_exercise_2"
az group create --location eastus --name $resourceGroupName
```

### テンプレートを Azure にデプロイする
```sh
templateFile="main.bicep"
templateParameterFile="azuredeploy.parameters.json"
today=$(date +"%d-%b-%Y")
deploymentName="deploymentscript-"$today

// storage アカウントなども作成 
az deployment group create --resource-group $resourceGroupName --name $deploymentName --template-file $templateFile --parameters $templateParameterFile
```

![image](https://github.com/rensawamo/ARM_extention/assets/106803080/02be3d28-869f-4666-9975-f0e846c6ca62)
 




