FROM microsoft/aspnetcore:2.0 AS base
WORKDIR /app
EXPOSE 80

FROM microsoft/aspnetcore-build:2.0 AS build
WORKDIR /src
COPY CVOmarBahjaoui/CVOmarBahjaoui.csproj CVOmarBahjaoui/
RUN dotnet restore CVOmarBahjaoui/CVOmarBahjaoui.csproj
COPY . .
WORKDIR /src/CVOmarBahjaoui
RUN dotnet build CVOmarBahjaoui.csproj -c Release -o /app

FROM build AS publish
RUN dotnet publish CVOmarBahjaoui.csproj -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "CVOmarBahjaoui.dll"]
