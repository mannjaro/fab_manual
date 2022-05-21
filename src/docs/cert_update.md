# 証明書の更新手順

!> 年に一度証明書の有効期限が切れるので，それに合わせて更新する必要があります

## 手順

1. [証明書の発行申請](certificate.md)を参考に，発行の申請をする
2. 秘密鍵と証明書`www.monodukuri.kit.ac.jp.key, www.monodukuri.kit.ac.jp.cer`をもらう
3. 秘密鍵にはパスフレーズがかかっており，解除しないと面倒なので，以下のコマンドで解除を行う．解除時にパスフレーズを入力するので，事前に聞いておくこと

```sh
openssh rsa -in {秘密鍵のパス}　-out {出力先のパス}
```

4. VPSサーバー上のフォルダにこれらを配置する
   - 秘密鍵`www.monodukuri.kit.ac.jp.key`は`/usr/local/workspace/cis_cert/private`
   -  証明書`www.monodukuri.kit.ac.jp.cer`は`/usr/local/workspace/cis_cert/certs`

!> それぞれのファイル名は上記の名前に従うこと

5. VPSサーバーの`/usr/local/workspace/`に移動し，以下のコマンドを実行する

```sh
docker-compose build && docker-compose up -d
```

6. [ものづくりセンターHP](https://www.monodukuri.kit.ac.jp) にアクセスし，証明書が有効になっていることを確認する

### 中間証明書の取得

中間証明書は[ここ](https://repo1.secomtrust.net/sppca/nii/odca4/index.html)からダウンロードできます．

?> 現在使用している中間証明書有効期限は2029年までです

中間証明書は`/usr/local/workspace/cis_cert/chain/`に配置し，ファイル名は`chain_rsa.cer`にしてください．
