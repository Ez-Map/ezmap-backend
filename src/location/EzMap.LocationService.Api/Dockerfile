FROM mcr.microsoft.com/dotnet/aspnet:7.0 AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

FROM mcr.microsoft.com/dotnet/sdk:7.0 AS build
WORKDIR /src
COPY ["src/location/EzMap.LocationService.Api/EzMap.LocationService.Api.csproj", "src/location/EzMap.LocationService.Api/"]
RUN dotnet restore "src/location/EzMap.LocationService.Api/EzMap.LocationService.Api.csproj"
COPY . .
WORKDIR "/src/src/location/EzMap.LocationService.Api"
RUN dotnet build "EzMap.LocationService.Api.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "EzMap.LocationService.Api.csproj" -c Release -o /app/publish /p:UseAppHost=false

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "EzMap.LocationService.Api.dll"]
