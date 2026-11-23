FROM mcr.microsoft.com/dotnet/sdk:10.0 AS build
WORKDIR /src
COPY Lab14_AlvaradoPiero/Lab14_AlvaradoPiero.csproj Lab14_AlvaradoPiero/
RUN dotnet restore Lab14_AlvaradoPiero/Lab14_AlvaradoPiero.csproj
COPY . .
RUN dotnet publish Lab14_AlvaradoPiero/Lab14_AlvaradoPiero.csproj -c Release -o /app/publish

FROM mcr.microsoft.com/dotnet/aspnet:10.0 AS final
WORKDIR /app
COPY --from=build /app/publish .
ENV ASPNETCORE_HTTP_PORTS=10000
EXPOSE 10000
ENTRYPOINT ["dotnet", "Lab14_AlvaradoPiero.dll"]