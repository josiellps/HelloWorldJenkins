 
FROM mcr.microsoft.com/dotnet/core/aspnet:3.1 AS build-env
WORKDIR /app
EXPOSE 5000
COPY . ./
RUN dotnet restore helloWorld/helloWorld.csproj
WORKDIR /app/helloWorld/ 
RUN dotnet publish -c Release -o out

FROM mcr.microsoft.com/dotnet/core/runtime:3.1
WORKDIR /app
COPY --from=build-env /app/helloWorld/out . 
ENTRYPOINT ["dotnet", "helloWorld.dll"]