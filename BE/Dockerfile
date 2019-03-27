# build
FROM mcr.microsoft.com/dotnet/core/sdk:2.2.105-alpine3.9 AS build
WORKDIR /app

COPY . .
RUN ls
RUN dotnet restore
RUN dotnet publish --output /out/ --configuration Release

# run
FROM mcr.microsoft.com/dotnet/core/aspnet:2.2.3-alpine3.9 as run
WORKDIR /app
ENV ASPNETCORE_URLS="http://*:5000"

COPY --from=build /out .

ENTRYPOINT ["dotnet", "PPD.ESchool.Host.dll"]