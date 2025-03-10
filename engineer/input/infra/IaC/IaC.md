Infrastructure as Codeの略で、CPU、メモリといったサーバのインフラ構築を、コードを用いて管理する概念。

インフラ構築のコード化により、自動で環境構築をしてくれるため、手作業による人為的なミスを削減することが可能です。同じ環境を何台も作成しなければならない場合にも、自動構築してくれるため作業時間を短縮できます。また、通常のソフトウェア開発と同じようにコードをバージョン管理することで、いつ修正したのかが明確となり、不具合の際などに第三者が検証しやすくなります。

属人化されない手順書がいらない
自動化ができる

https://www.ntt-tx.co.jp/column/iac/230815/
<br>


# 参考2
https://zenn.dev/ring_belle/articles/iac-general-features

メリット
IaCツールを導入すると、ソースコードでインフラリソースを管理できるようになります。それによって、さまざまな恩恵を受けることができます。

リリース前にレビューが受けられる
IaCツールがない場合、AWS上になにかリソースを追加する場合、ブラウザでAWSコンソールから作成しなければなりません。
その場合、他人のレビューを受けるためには、スクリーンショットを撮り、作業フロー(手順書)をドキュメント化しなければなりません。これはお世辞にも効率的とはいえません。
しかし、IaC化されていれば、アプリケーションコードの修正と同じフローで、ソースを修正し、github上でレビューを行うことができるようになります。

複数環境を簡単に作成・管理できる
IaCツールを導入すると、Production環境とStaging環境、Test環境などの複数環境が簡単に作成できます。
Network構成からWebサーバー、DBサーバーまでソースで管理されているため、同じソースを他のAWS環境に適用すれば、Production環境と全く同じStaging環境を作成することが可能です。(もちろん、StagingのみCPUやメモリなどのリソースを変更することも簡単です。)

リソース間の関係が可視化できる
IaCツールを導入すると、

セキュリティグループAは、リソースBとリソースCに使われている
リソースBはデータベースDに紐づいている
データベースDはネットワークEに構築されている
などのリソース間の関係が簡単に把握できます。
そのため、リソースの関係を可視化するために構成図を作成・運用する必要性がなくなります。(ドキュメントを作る・運用するというのは大きなコストなため、IaCツールを導入する大きなメリットの一つになります)

誰かがリソースを変更したら、(自動で)引き戻せる
AWS上で誰かが間違えてリソースを変更した場合、IaCツールを導入しているとその変更を検知することができます。(ソースで管理している状態とAWS上の状態が異なるため)
また、CrossplaneのようなControlplane型のIaCツールを使っていると、その変更を自動で検知し、ソースコードと同じ状態に自動で引き戻してくれます。

デメリット
IaCツールを導入することで発生するデメリットは大きくわけて2つです。

学習コストが高い
IaCツールの代表格Terraformを使う場合、Terraform用の言語(HCL)を覚えなければなりません。 また、stateファイルの管理など、Terraform独自の構造も覚えなければならないため、IaCツールを導入する際の学習コストは検討した方がいいでしょう。

IaCツールを動かす環境を用意しないといけない
Terraformを使う場合はCI等でterraform cliを実行する。Crossplaneを使う場合はCrossplaneが動作するKubernetesクラスターを用意するなど、IaCツールの動作環境を用意しなければなりません。
また、IaCツールもver upしていくため、IaCツールのverup等、運用負荷も考慮する必要があります。

まとめ
IaCツールのメリット・デメリットを紹介しましたが、個人的にはIaCツールは現代のweb開発で必須のツールだと思っています。そのため、チーム開発を行う場合は必ずIaCツールの導入を検討することをおすすめします。

