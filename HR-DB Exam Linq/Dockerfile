FROM mcr.microsoft.com/dotnet/runtime:7.0 AS base
WORKDIR /app

FROM mcr.microsoft.com/dotnet/sdk:7.0 AS build
WORKDIR /src
COPY ["HR-DB Exam Linq/HR-DB Exam Linq.csproj", "HR-DB Exam Linq/"]
RUN dotnet restore "HR-DB Exam Linq/HR-DB Exam Linq.csproj"
COPY . .
WORKDIR "/src/HR-DB Exam Linq"
RUN dotnet build "HR-DB Exam Linq.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "HR-DB Exam Linq.csproj" -c Release -o /app/publish /p:UseAppHost=false

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "HR-DB Exam Linq.dll"]
