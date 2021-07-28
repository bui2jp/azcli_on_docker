# azcli_on_docker

Docker コンテナーでの Azure CLI の実行

```
https://docs.microsoft.com/ja-jp/cli/azure/run-azure-cli-docker
```
## install(run) login
```
$ docker run -it --rm mcr.microsoft.com/azure-cli
```

## version
```
bash-5.1# az --version
azure-cli                         2.26.1

core                              2.26.1
telemetry                          1.0.6
```

## az login
```
## az login
To sign in, use a web browser to open the page https://microsoft.com/devicelogin and enter the code ######## to authenticate.
```
ブラウザを使って認証


## コマンドを見つける
```
bash-5.1# az find login
```

## VM 作成してみる

```
bash-5.1# az login
```

リソースグループ作成
```
az group create --name TutorialResources --location eastus
```

vm作成
```
az vm create --resource-group TutorialResources \
  --name TutorialVM1 \
  --image UbuntuLTS \
  --generate-ssh-keys \
  --output json \
  --verbose
```

リソースグループごと削除
```
bash-5.1# az group delete --name TutorialResources --no-wait
```

subscriptionの変更
account list で SubscriptionId を確認して、account set で変更
```
bash-5.1# az account list --output table
Name                        CloudName    SubscriptionId                        State    IsDefault
--------------------------  -----------  ------------------------------------  -------  -----------
Azure サブスクリプション 1  AzureCloud   4a2b8f56-0eae-457a-be65-66ac50222f37  Enabled  False
従量課金                    AzureCloud   8f20b603-894f-4cdc-a8a9-bcfc249b4535  Enabled  True

bash-5.1# az account set --subscription 8f20b603-894f-4cdc-a8a9-bcfc249b4535
```
