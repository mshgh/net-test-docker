FROM mcr.microsoft.com/dotnet/core/sdk:2.2-alpine AS build
WORKDIR /app

# copy csproj and restore as distinct layers
COPY ./src/HwDemo/*.csproj ./HwDemo/
WORKDIR /app/HwDemo
RUN dotnet restore

# copy and publish app and libraries
WORKDIR /app/
COPY ./src/HwDemo/. ./HwDemo/
WORKDIR /app/HwDemo
RUN dotnet publish -c Release -o out


# test application -- see: dotnet-docker-unit-testing.md
#FROM build AS testrunner
#WORKDIR /app/tests
#COPY tests/. .
#ENTRYPOINT ["dotnet", "test", "--logger:trx"]


FROM mcr.microsoft.com/dotnet/core/runtime:2.2-alpine AS runtime
WORKDIR /app
COPY --from=build /app/HwDemo/out ./
ENTRYPOINT ["dotnet", "HwDemo.dll"]
