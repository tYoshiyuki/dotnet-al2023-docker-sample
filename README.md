# dotnet-al2023-docker-sample
Amazon Linux 2023 で ASP.NET Core・Nginx の両プロセスを起動するDockerイメージをビルドするサンプル

## Feature
- .NET8
- ASP.NET Core
- Amazon Linux 2023
- Nginx

## Note
- docker/build-docker.bat を実行することで、Dockerイメージのビルドを行います。
    - マルチステージビルドを利用し、バックエンドをビルドした上で、アプリケーションサーバのイメージを生成します。
    - Dockerイメージをビルドする際には Docker Desktop が必要です。
- supervisor を用いて、Nginx と ASP.NET Core の両プロセスを管理しています。
