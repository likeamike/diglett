FROM mcr.microsoft.com/dotnet/core/sdk:3.1 AS build
WORKDIR /src
COPY "Diglett.sln" "Diglett.sln"
COPY "Weather.Api/Weather.Api.csproj" "Weather.Api/Weather.Api.csproj"
RUN dotnet restore "Weather.Api/Weather.Api.csproj"
COPY . .
WORKDIR /src/Weather.Api
RUN dotnet publish --no-restore -c Release -o /diglett


FROM mcr.microsoft.com/dotnet/core/aspnet:3.1 AS final
EXPOSE 80
WORKDIR /diglett
COPY --from=build /diglett .
ENTRYPOINT [ "dotnet", "Weather.Api.dll" ]