FROM mcr.microsoft.com/dotnet/sdk:6.0 As build
WORKDIR /app

# Copy everything
COPY . ./
# Restore as distinct layers
RUN dotnet restore
# Build and publish a release
RUN dotnet publish -c Release -o usr/app/out

FROM mcr.microsoft.com/dotnet/sdk:6.0 
EXPOSE 80
WORKDIR /app
COPY --from= build /app/out .
ENTRYPOINT ["dotnet", "aspnet-get-started.dll"]
