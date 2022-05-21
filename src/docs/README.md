<!-- omit in toc -->
# センターHP運用手順書

## ドキュメント作成者 <!-- {docsify-ignore} -->

- e-mail: zk.takayuki@gmail.com
- Twitter: [@tasks_sch](https://twitter.com/tasks_sch)

## ドキュメントの見方

ドキュメント中には`{ユーザー名}`のように括弧で囲った表記がありますが，それらは適宜状況によって置き換えが発生する箇所を指します
例えば，

```sh
ssh -i ~/.ssh/id_rsa {ユーザー名}@www.monodukuri.kit.ac.jp
```

ユーザー名が`hogehoge`だった場合

```sh
ssh -i ~/.ssh/id_rsa hogehoge@www.monodukuri.kit.ac.jp
```

のように置き換えて読んでください．

## FAQ
### サーバーに接続するには?

- [接続方法](ssh.md)
- [サーバーの情報](info.md)

### SSL証明書の更新方法

- [証明書申請手順](certificate.md)
- [証明書の設定方法](cert_update.md)
