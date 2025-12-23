FROM mcr.microsoft.com/dotnet/sdk:10.0 AS build
WORKDIR /app

COPY . .
RUN dotnet publish -c Release -o /app/publish

FROM mcr.microsoft.com/dotnet/aspnet:10.0
WORKDIR /app

COPY --from=build /app/publish .

EXPOSE 7070
ENV ASPNETCORE_HTTP_PORTS=7070

ENTRYPOINT ["dotnet", "cartservice.dll"]