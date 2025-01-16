
# Serverless APIs using Azure Functions (TurbineRepair)

.NET Core 8 Azure Function API to determine whether an emergency repair on a wind turbine is cost-effective or Not.

hours:	The estimated time to make a turbine repair, up to the nearest whole hour.
capacity:	The capacity of the turbine, in kilowatts.

The function then calculates how much a repair costs, and how much revenue the turbine could make in a 24-hour period. Parameters are supplied either in the query string or in the payload of a POST request.
This function code returns a message of Yes or No to indicate whether an emergency repair is cost-effective. It also returns the revenue opportunity that the turbine represents and the cost to fix the turbine.

## Project References
```
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>net8.0</TargetFramework>
    <AzureFunctionsVersion>v4</AzureFunctionsVersion>
    <OutputType>Exe</OutputType>
    <ImplicitUsings>enable</ImplicitUsings>
    <Nullable>enable</Nullable>
  </PropertyGroup>
  <ItemGroup>
    <FrameworkReference Include="Microsoft.AspNetCore.App" />
    <PackageReference Include="Microsoft.Azure.Functions.Worker" Version="1.20.1" />
    <PackageReference Include="Microsoft.Azure.Functions.Worker.Extensions.Http" Version="3.1.0" />
    <PackageReference Include="Microsoft.Azure.Functions.Worker.Extensions.Http.AspNetCore" Version="1.2.0" />
    <PackageReference Include="Microsoft.Azure.Functions.Worker.Extensions.OpenApi" Version="1.5.1" />
    <PackageReference Include="Microsoft.Azure.Functions.Worker.Sdk" Version="1.16.4" />
    <PackageReference Include="Microsoft.ApplicationInsights.WorkerService" Version="2.21.0" />
    <PackageReference Include="Microsoft.Azure.Functions.Worker.ApplicationInsights" Version="1.1.0" />
  </ItemGroup>
  <ItemGroup>
    <None Update="host.json">
      <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>
    </None>
    <None Update="local.settings.json">
      <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>
      <CopyToPublishDirectory>Never</CopyToPublishDirectory>
    </None>
  </ItemGroup>
  <ItemGroup>
    <Using Include="System.Threading.ExecutionContext" Alias="ExecutionContext" />
  </ItemGroup>
</Project>

```

## APIs

Below is a list of API endpoints with their respective input and output. Please note that the application needs to be running.

### Users - Calculate Repair Cost & Indicate repair is cost-effective or Not.

Endpoint

```
http://localhost:7041/api/swagger/ui

{
  "hours": 432,
  "capacity": 4221
}
```

Response body

```json
{
  "message": "No",
  "revenueOpportunity": "$12156.48",
  "costToFix": "$108100"
}
```

![123](https://github.com/user-attachments/assets/0d2fcf89-f582-4664-8cb9-a34baf08f3e2)
![1234](https://github.com/user-attachments/assets/048ef655-11b6-430d-afcb-ff1a13af81f0)

