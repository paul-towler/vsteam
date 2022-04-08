<!-- #include "./common/header.md" -->

# Add-VSTeamServiceEndpoint

## SYNOPSIS

<!-- #include "./synopsis/Add-VSTeamServiceEndpoint.md" -->

## SYNTAX

## DESCRIPTION

The cmdlet adds a new generic connection between TFS/AzD and a third party service (see AzD for available connections).

## EXAMPLES

### Example 1 - Azure Stack Service Connection
```powershell
$methodParameters = @{
    ProjectName  = "some_project_name"
    endpointName = "new_endpoint_name"
    endpointType = "azurerm"
    object        = @{
        url="https://adminmanagement.local.azurestack.external"; 
        authorization = @{
            parameters = @{
                serviceprincipalid = "some_service_principal_id"
                serviceprincipalkey = "some_service_principal_key"
                authenticationType = "spnKey"
                tenantid = "some_tenant_id"
            }
            scheme = "ServicePrincipal"
        }
        isShared=$true
        isReady=$true
        data = @{
            environment = "AzureStack"
            scopeLevel = "Subscription"
            subscriptionId = "some_subscription_id"
            subscriptionName = "some_subscription_name"
            creationMode = "Manual"
        }
    }
 }

 Add-VSTeamServiceEndpoint @methodParameters
```

## PARAMETERS

### Object

Hashtable of Payload for REST call

```yaml
Type: Hashtable
Required: True
Accept pipeline input: true (ByPropertyName)
```

### EndpointName

The name displayed on the services page. In AzD this is the Connection Name.

```yaml
Type: String
Position: 2
```

### EndpointType

Type of endpoint (eg. `kubernetes`, `sonarqube`). See AzD service page for supported endpoints.

```yaml
Type: String
Position: 3
```

<!-- #include "./params/projectName.md" -->

## INPUTS

## OUTPUTS

### vsteam_lib.ServiceEndpoint

## NOTES

<!-- #include "./common/prerequisites.md" -->

## RELATED LINKS



[Get-VSTeamServiceEndpoint](Get-VSTeamServiceEndpoint.md)

[Get-VSTeamServiceEndpointType](Get-VSTeamServiceEndpointType.md)

[Remove-VSTeamServiceEndpoint](Remove-VSTeamServiceEndpoint.md)
