FROM mcr.microsoft.com/dotnet/sdk:9.0 AS build
WORKDIR /src

COPY ["phase1_student_rbd/phase1_student_rbd.csproj", "phase1_student_rbd/"]
RUN dotnet restore "phase1_student_rbd/phase1_student_rbd.csproj"

COPY . .
WORKDIR "/src/phase1_student_rbd"
RUN dotnet publish -c Release -o /app/publish

FROM mcr.microsoft.com/dotnet/aspnet:9.0 AS final
WORKDIR /app
COPY --from=build /app/publish .

EXPOSE 5000
ENV ASPNETCORE_URLS=http://+:5000

ENTRYPOINT ["dotnet", "phase1_student_rbd.dll"]
