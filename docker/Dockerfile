# アプリケーションサーバを準備するステージ
FROM amazonlinux:2023 AS base
RUN dnf update \
    && dnf install -y nginx
RUN dnf install -y python3-pip \
    && pip3 install supervisor
RUN dnf install -y aspnetcore-runtime-8.0
COPY ./docker/supervisord.conf /etc/supervisor/conf.d/
COPY ./docker/app.conf /etc/nginx/default.d/
EXPOSE 80

# バックエンドをビルドするステージ
FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build-api
ARG BUILD_CONFIGURATION=Release
WORKDIR /src
COPY ["src/SampleWebApplication/", "."]
RUN dotnet restore "./SampleWebApplication.csproj"
RUN dotnet build "./SampleWebApplication.csproj" -c $BUILD_CONFIGURATION -o /app/build
RUN dotnet publish "./SampleWebApplication.csproj" -c $BUILD_CONFIGURATION -o /app/publish /p:UseAppHost=false

# アプリケーションサーバにビルド結果をデプロイするステージ
FROM base AS final
WORKDIR /app
COPY --from=build-api /app/publish .
CMD ["supervisord", "-c", "/etc/supervisor/conf.d/supervisord.conf"]
