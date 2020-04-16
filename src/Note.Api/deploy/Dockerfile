FROM mcr.microsoft.com/dotnet/core/sdk:3.1 AS build
WORKDIR /src
COPY "Diglett.sln" "Diglett.sln"
COPY "Note.Api/Note.Api.csproj" "Note.Api/Note.Api.csproj"
RUN dotnet restore "Note.Api/Note.Api.csproj"
COPY . .
WORKDIR /src/Note.Api
RUN dotnet publish --no-restore -c Release -o /diglett


FROM mcr.microsoft.com/dotnet/core/aspnet:3.1 AS final
EXPOSE 80
WORKDIR /diglett
COPY --from=build /diglett .
ENTRYPOINT [ "dotnet", "Note.Api.dll" ]