# Ansible2.1+ARMのテスト

## 環境変数の設定

サービスプリンシパル認証のための情報を以下の2あたりを参考に取得して、環境変数に設定する

[Qiita: バーチャルマシンを ARM対応の Terraform を使ってプロビジョンしてみる](http://qiita.com/TsuyoshiUshio@github/items/4a4393b92ba65c8012ae)

```
export AZURE_SUBSCRIPTION_ID=< サブスクリプションID >
export AZURE_CLIENT_ID=< クライアントID >
export AZURE_SECRET=< シークレット >
export AZURE_TENANT=< テナントID >
export SSH_KEY_DATA=< 管理者用の公開鍵文字列 ...>
```

## playbookの実行

```
$ ansible-playbook -i hosts/hosts default.yml
```

## VM作成時にエラーになる場合...

作成->削除->削除のような作業をしていると、VM作成時に以下のようなエラーでVMが作成できないことがあった。

```
Long running operation failed with status 'Failed'
```

vmの名前を変えたら無事作成できたけど、これで必ず解決するかはわからない...。
