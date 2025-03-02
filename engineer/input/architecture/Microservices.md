![](/images/architecture/Microservice.jpeg)


# マイクロサービスとは
複数の小さなサービスを連携させて大きなサービスを構築するもの


# 構築例

フロントエンド(next.js + typescript)<br>
BFF(nest.js + GraphQL + typescript)<br>
バックエンド(gRPC + go)<br>

## 説明
gRPCを使用することでバックエンド(マイクロサービス)間で通信を行うことができる<br>
複数のバックエンドから必要なデータ'だけ'を取得するためにGraphQLが必要<br>
BFFに採用するフレームワークはGraphQLとgRPCを両方を取り扱える必要があり、それを満たす為、nest.jsが採用されることが多いらしい<br>

