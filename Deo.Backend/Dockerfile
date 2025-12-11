# stage1: build the app
FROM mcr.microsoft.com/dotnet/sdk:9.0-alpine3.23 AS build-stage
# beim builden des images wechseln wir das working directory
WORKDIR /build
# kopiere alle dateien in das working directory
# rechter punkt: target (working directory im container)
#COPY . /build
COPY . .
RUN dotnet publish

FROM mcr.microsoft.com/dotnet/aspnet:9.0-alpine3.23
WORKDIR /app
COPY --from=build-stage /build/bin/Release/net9.0/publish .
ENTRYPOINT ["/app/Deo.Backend"]