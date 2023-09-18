FROM mcr.microsoft.com/dotnet/aspnet:7.0 AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

FROM mcr.microsoft.com/dotnet/sdk:7.0 AS build
WORKDIR /src
COPY ["src/profile/EzMap.ProfileService.Api/EzMap.ProfileService.Api.csproj", "src/profile/EzMap.ProfileService.Api/"]
RUN dotnet restore "src/profile/EzMap.ProfileService.Api/EzMap.ProfileService.Api.csproj"
COPY . .
WORKDIR "/src/src/profile/EzMap.ProfileService.Api"
RUN dotnet build "EzMap.ProfileService.Api.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "EzMap.ProfileService.Api.csproj" -c Release -o /app/publish /p:UseAppHost=false

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "EzMap.ProfileService.Api.dll"]
