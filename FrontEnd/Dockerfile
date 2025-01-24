FROM mcr.microsoft.com/dotnet/sdk:7.0 AS build
WORKDIR /src
COPY FrontEnd.csproj .
RUN dotnet restore "FrontEnd.csproj"
COPY . .
RUN dotnet publish "FrontEnd.csproj" -c Release -o /app/publish /p:UseAppHost=false

FROM nginx:alpine
COPY --from=build /app/publish/wwwroot /usr/share/nginx/html
