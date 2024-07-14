# dotnet-al2023-docker-sample
Amazon Linux 2023 の Dockerイメージをビルドするサンプル

## Feature
- .NET8
- ASP.NET Core
- Amazon Linux 2023
- Nginx

## Note
- Docker/build-docker.bat (build-docker.sh) を実行することで、Dockerイメージのビルドを行います。
    - マルチステージビルドを利用し、バックエンドをビルドした上で、アプリケーションサーバのイメージを生成します。
    - Dockerイメージをビルドする際には Docker Desktop が必要です。
- supervisor を用いて、Nginx と ASP.NET Core の両プロセスを管理しています。