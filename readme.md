# Fortigate HA

## Introduction

This template deploys a 2 x 2 NIC Fortigate Firewall resource in an HA configuration.

## Security Controls

The following security controls can be met through configuration of this template:

* AC-2, AC-3, AC-4, AC-5, AC-6, AC-8, AU-11, AU-12, AU-2, AU-3, AU-4, AU-8, AU-9, CM-3, CM-6, IA-2, IA-3, IA-5, SA-22, SC-10, SC-12, SC-13, SC-7, SC-8, SI-2, SI-4

## Dependancies

* [Resource Groups](https://github.com/canada-ca/accelerators_accelerateurs-azure/blob/master/Templates/arm/resourcegroups/latest/readme.md)
* [Keyvault](https://github.com/canada-ca/accelerators_accelerateurs-azure/blob/master/Templates/arm/keyvaults/latest/readme.md)
* [VNET-Subnet](https://github.com/canada-ca/accelerators_accelerateurs-azure/blob/master/Templates/arm/vnet-subnet/latest/readme.md)

## Parameter format

```json
{
    "$schema": "https://schema.management.azure.com/schemas/2015-01-01/deploymentParameters.json#",
    "contentVersion": "1.0.0.0",
    "parameters": {
        "fwObject": {
            "value": {
                "vmKeyVault": {
                    "keyVaultResourceGroupName": "PwS2-validate-fortigateha-RG",
                    "keyVaultName": "PwS2-validate-[unique]"
                },
                "FortiGateName": "validate01",
                "adminUsername": "fwadmin",
                "adminSecret": "fwpassword",
                "FortiGateImageSKU": "fortinet_fg-vm",
                "FortiGateImageVersion": "latest",
                "instanceType": "Standard_F4s",
                "publicIPAddressName": "validate01-publicip1",
                "publicIP2AddressName": "validate01-publicip2",
                "publicIPNewOrExistingOrNone": "new",
                "publicIP2NewOrExistingOrNone": "new",
                "publicIPResourceGroup": "PwS2-validate-fortigateha-RG",
                "publicIP2ResourceGroup": "PwS2-validate-fortigateha-RG",
                "location": "canadacentral",
                "vnetNewOrExisting": "existing",
                "vnetName": "PwS2-validate-fortigateHA-VNET",
                "vnetResourceGroup": "PwS2-validate-fortigateha-RG",
                "Subnet1Name": "outside",
                "Subnet2Name": "inside",
                "firewall1Config": "Y29uZmlnIHN5c3RlbSBnbG9iYWwNCiAgICBzZXQgYWRtaW4tc3BvcnQgODQ0Mw0KICAgIHNldCBhbGlhcyAiUHdQMEZXQ29yZTAxIg0KICAgIHNldCBob3N0bmFtZSAiUHdQMEZXQ29yZTAxIg0KICAgIHNldCB0aW1lem9uZSAwNA0KZW5kDQpjb25maWcgc3lzdGVtIGludGVyZmFjZQ0KICAgIGVkaXQgInBvcnQxIg0KICAgICAgICBzZXQgdmRvbSAicm9vdCINCiAgICAgICAgc2V0IG1vZGUgZGhjcA0KICAgICAgICBzZXQgYWxsb3dhY2Nlc3MgcGluZyBodHRwcyBzc2ggaHR0cCBmZ2ZtIHByb2JlLXJlc3BvbnNlDQogICAgICAgIHNldCB0eXBlIHBoeXNpY2FsDQogICAgICAgIHNldCBkZXNjcmlwdGlvbiAiT3V0c2lkZSINCiAgICAgICAgc2V0IGFsaWFzICJPdXRzaWRlIg0KICAgICAgICBzZXQgc25tcC1pbmRleCAxDQogICAgbmV4dA0KICAgIGVkaXQgInBvcnQyIg0KICAgICAgICBzZXQgdmRvbSAicm9vdCINCiAgICAgICAgc2V0IG1vZGUgZGhjcA0KICAgICAgICBzZXQgYWxsb3dhY2Nlc3MgcGluZyBodHRwcyBzc2ggaHR0cCBmZ2ZtIHByb2JlLXJlc3BvbnNlDQogICAgICAgIHNldCB0eXBlIHBoeXNpY2FsDQogICAgICAgIHNldCBkZXNjcmlwdGlvbiAiQ29yZVRvU3Bva2VzIg0KICAgICAgICBzZXQgYWxpYXMgIkNvcmVUb1Nwb2tlcyINCiAgICAgICAgc2V0IHNubXAtaW5kZXggMg0KICAgICAgICBzZXQgZGVmYXVsdGd3IGRpc2FibGUNCiAgICBuZXh0DQplbmQNCmNvbmZpZyBzeXMgYXV0by1zY2FsZQ0KICAgIHNldCBzdGF0IGVuYWJsZQ0KICAgIHNldCByb2xlIG1hc3Rlcg0KICAgIHNldCBzeW5jLWludCBwb3J0Mg0KICAgIHNldCBwc2tzZWNyZXQgQ2FuYWRhMTIzNDU2IQ0KZW5k",
                "firewall2Config": "Y29uZmlnIHN5c3RlbSBnbG9iYWwNCiAgICBzZXQgYWRtaW4tc3BvcnQgODQ0Mw0KICAgIHNldCBhbGlhcyAiUHdQMEZXQ29yZTAyIg0KICAgIHNldCBob3N0bmFtZSAiUHdQMEZXQ29yZTAyIg0KICAgIHNldCB0aW1lem9uZSAwNA0KZW5kDQpjb25maWcgc3lzdGVtIGludGVyZmFjZQ0KICAgIGVkaXQgInBvcnQxIg0KICAgICAgICBzZXQgdmRvbSAicm9vdCINCiAgICAgICAgc2V0IG1vZGUgZGhjcA0KICAgICAgICBzZXQgYWxsb3dhY2Nlc3MgcGluZyBodHRwcyBzc2ggaHR0cCBmZ2ZtIHByb2JlLXJlc3BvbnNlDQogICAgICAgIHNldCB0eXBlIHBoeXNpY2FsDQogICAgICAgIHNldCBkZXNjcmlwdGlvbiAiT3V0c2lkZSINCiAgICAgICAgc2V0IGFsaWFzICJPdXRzaWRlIg0KICAgICAgICBzZXQgc25tcC1pbmRleCAxDQogICAgbmV4dA0KICAgIGVkaXQgInBvcnQyIg0KICAgICAgICBzZXQgdmRvbSAicm9vdCINCiAgICAgICAgc2V0IG1vZGUgZGhjcA0KICAgICAgICBzZXQgYWxsb3dhY2Nlc3MgcGluZyBodHRwcyBzc2ggaHR0cCBmZ2ZtIHByb2JlLXJlc3BvbnNlDQogICAgICAgIHNldCB0eXBlIHBoeXNpY2FsDQogICAgICAgIHNldCBkZXNjcmlwdGlvbiAiQ29yZVRvU3Bva2VzIg0KICAgICAgICBzZXQgYWxpYXMgIkNvcmVUb1Nwb2tlcyINCiAgICAgICAgc2V0IHNubXAtaW5kZXggMg0KICAgICAgICBzZXQgZGVmYXVsdGd3IGRpc2FibGUNCiAgICBuZXh0DQplbmQNCmNvbmZpZyBzeXMgYXV0by1zY2FsZQ0KICAgIHNldCBzdGF0IGVuYWJsZQ0KICAgIHNldCBtYXN0ZXItaXAgMTAuMjUwLjIuNQ0KICAgIHNldCBzeW5jLWludCBwb3J0Mg0KICAgIHNldCBwc2tzZWNyZXQgQ2FuYWRhMTIzNDU2IQ0KZW5k",
                "tagValues": {
                    "Owner": "build.pipeline@tpsgc-pwgsc.gc.ca",
                    "CostCenter": "PSPC-EA",
                    "Enviroment": "Validate",
                    "Classification": "Unclassified",
                    "Organizations": "PSPC-CCC-E&O",
                    "DeploymentVersion": "2018-12-14-01"
                }
            }
        }
    }
}
```

## Parameter Values

### Main Template

| Name               | Type   | Required | Value                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| ------------------ | ------ | -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| containerSasToken  | string | No       | SAS Token received as a parameter                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| _artifactsLocation | string | No       | Dynamically derived from the deployment template link uri                                                                                                                                                                                                                                                                                                                                                                                                                      |
| _debugLevel        | string | No       | Specifies the type of information to log for debugging. The permitted values are none, requestContent, responseContent, or both requestContent and responseContent separated by a comma. The default is none. When setting this value, carefully consider the type of information you are passing in during deployment. By logging information about the request or response, you could potentially expose sensitive data that is retrieved through the deployment operations. |
| fwObject           | object | Yes      | Array of [Fortigate2NIC objects](#fortigate2nic-object)                                                                                                                                                                                                                                                                                                                                                                                                                        |

### Fortigate2NIC Object

| Name                         | Type   | Required | Value                                                                                                                                                           |
| ---------------------------- | ------ | -------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| vmKeyVault                   | object | Yes      | Keyvault resource information - [Keyvault Object](#keyvault-object)                                                                                             |
| FortiGateName                | string | Yes      | Name of the firewall Virtual Machine.                                                                                                                           |
| adminUsername                | string | Yes      | Name of the Fortigate admin user                                                                                                                                |
| adminSecret                  | string | Yes      | Name of the keyvault secret containing the Fortigate admin user password                                                                                        |
| FortiGateImageSKU            | string | Yes      | SKU for the fortigate image - fortinet_fg-vm or fortinet_fg-vm_payg                                                                                             |
| FortiGateImageVersion        | string | Yes      | Version of the firewall marketplace image - 5.6.6, 6.0.3, 6.0.4 or latest. Recommended values: latest                                                           |
| instanceType                 | string | Yes      | Virtual Machine size selection. Recommended value: Standard_F4s                                                                                                 |
| publicIPAddressName          | string | Yes      | Name of the Public IP Address                                                                                                                                   |
| publicIP2AddressName         | string | Yes      | Name of the Public IP 2 Address                                                                                                                                 |
| publicIPAddressType          | string | Yes      | Type of public IP address - dynamic or static. Recommended value: static                                                                                        |
| publicIPNewOrExistingOrNone  | string | Yes      | Indicates whether a Public IP is required - none, new or existing. Recommended value: none unless one is required. In this case: new                            |
| publicIP2NewOrExistingOrNone | string | Yes      | Indicates whether a Public IP 2 is required - none, new or existing. Recommended value: none unless one is required. In this case: new                          |
| publicIPResourceGroup        | string | Yes      | Resource Group of the public IP                                                                                                                                 |
| publicIP2ResourceGroup       | string | Yes      | Resource Group of the public IP 2                                                                                                                               |
| location                     | string | Yes      | Location of the resource. Either canadacentral or canadaeast                                                                                                    |
| vnetNewOrExisting            | string | Yes      | Identify whether to use a new or existing vnet - new or existing. Recommended value: existing                                                                   |
| vnetName                     | string | Yes      | Virtual Network name                                                                                                                                            |
| vnetResourceGroup            | string | Yes      | Name of the Resource Group containing the VNET defined above                                                                                                    |
| authenticationType           | string | Yes      | Type of authentication. Allowed values are password or sshPublicKey                                                                                             |
| vmSize                       | string | Yes      | Size of the Virtual Machine. Recommended value is one of Standard_D3 or Standard_D3_v2                                                                          |
| storageAccountName           | string | Yes      | Storage Account prefix where the Virtual Machine's disks and/or diagnostic files will be placed. Name will be made unique.                                      |
| storageAccountRG             | string | Yes      | Name of the Resource Group for the storage account defined above                                                                                                |
| storageAccountType           | string | Yes      | The type of storage account created. Recommended value is Standard_LRS                                                                                          |
| storageAccountNewOrExisting  | string | Yes      | Should the storage account be created as part of the deployment. Possible value is new or existing. Recommended value is new                                    |
| publicIPDnsLabel             | string | Yes      | DNS Prefix for the Public IP used to access the Virtual Machine. Will be made unique.                                                                           |
| publicIPNewOrExisting        | string | Yes      | Indicates whether the Public IP is new or existing                                                                                                              |
| publicIPRG                   | string | Yes      | Resource Group of the public IP                                                                                                                                 |
| publicIPAllocationMethod     | string | Yes      | Enter Dynamic or Static as the type of public IP                                                                                                                |
| publicIPsku                  | string | Yes      | Indicates whether the public IP SKU will be of Basic or Standard                                                                                                |
| virtualNetworkName           | string | Yes      | Virtual Network name                                                                                                                                            |
| virtualNetworkRG             | string | Yes      | Name of the Resource Group containing the VNET defined above                                                                                                    |
| Subnet1Name                  | string | Yes      | Name of the external subnet                                                                                                                                     |
| Subnet2Name                  | string | Yes      | Name of the internal subnet                                                                                                                                     |
| firewall1Config              | string | Yes      | Base64 encoded multipart/mixed string of [Firewall Config and License](#firewall-config-and-license). Leave empty ("") if no firewall configuration is required |
| firewall2Config              | string | Yes      | Base64 encoded multipart/mixed string of [Firewall Config and License](#firewall-config-and-license). Leave empty ("") if no firewall configuration is required |
| tagValues                    | object | Yes      | Object of tag values                                                                                                                                            |

### Keyvault Object

| Name                      | Type                           | Required | Value                                                                   |
| ------------------------- | ------------------------------ | -------- | ----------------------------------------------------------------------- |
| keyVaultResourceGroupName | PwS2-validate-Fortigate2NIC-RG | Yes      | Name of the Resource Group containing the keyvault                      |
| keyVaultName              | PwS2-validate-[unique]         | Yes      | Name of keyvault resource - [Name format options](#name-format-options) |

#### Name Format Options

When specifying the name of a keyvault simply include the token [unique] (including the []) as part of the name. The template will replace the [unique] word with a unique string of characters. For example:

| Name                   | Result                     |
| ---------------------- | -------------------------- |
| key-[unique]-deploy    | key-sd8kjdf678k9-deploy    |
| keyvault-test-[unique] | keyvault-test-sd8kjdf678k9 |

This is helpfull to ensure there will be no keyvault duplicates in Azure as it need to be unique.

### Firewall Config and License

Two part mime message comprised of the desired firewall configuration and the fortigate license. Here is an example of the mime message:

```mime
Content-Type: multipart/mixed; boundary="===============0740947994048919689=="
MIME-Version: 1.0

--===============0740947994048919689==
Content-Type: text/plain; charset="us-ascii"
MIME-Version: 1.0
Content-Transfer-Encoding: 7bit
Content-Disposition: attachment; filename="config"

config system global
    set admin-sport 8443
    set alias "PwP0FWCore01"
    set hostname "PwP0FWCore01"
    set timezone 04
end
config system interface
    edit "port1"
        set vdom "root"
        set mode dhcp
        set allowaccess ping https ssh http fgfm probe-response
        set type physical
        set description "Outside"
        set alias "Outside"
        set snmp-index 1
    next
    edit "port2"
        set vdom "root"
        set mode dhcp
        set allowaccess ping https ssh http fgfm probe-response
        set type physical
        set description "CoreToSpokes"
        set alias "CoreToSpokes"
        set snmp-index 2
        set defaultgw disable
    next
end
config sys auto-scale
    set stat enable
    set role master
    set sync-int port2
    set psksecret Canada123456!
end

--===============0740947994048919689==
Content-Type: text/plain; charset="us-ascii"
MIME-Version: 1.0
Content-Transfer-Encoding: 7bit
Content-Disposition: attachment; filename="license"

-----BEGIN FGT VM LICENSE-----
QAAAAAxO36IkxkoqbVbYEKvz9qpFD+WwKJ5ilbkuiUvK8iZaCBTZ2gicYuVV1oez
O/QM4hnMFQePlvlga/gyI9iIRdnQGQAAXhNlYZQnMJLXyfS7Up6FAhQeb8bOLWu2
TjQ4y76kfL/D30OvlpCZjbQgIWwDJu4NPsZYAob2PDVg+JEhk9dAO9mqTu+gF954
OAlFW7ljUzpjyRU/sfaPwISps+O/lMi+7+vVkbSBputtdSgtIkSKqEeCkdEuoKCd
6OQbWoI9m36FOztiZhlQ3gwrJ3dV94rxvnqkxzaWIQFvByKTaVp9YpTTIGR9aa02
k5N9i6QY+OOLipKFHKlhPBicygePkm5HKGiDoi/cvYrq9kgfcgvV5YglV3d/wl50
iYx/jIOypr8kMrAVcRCrz46Nz/K5U7pC5qL8X2caT+AXVm6dOCNYwsQ/hjZl06Qg
J/StdPQzyY6KuaGryuK8ThmftycVY1adMMJeuGoj3YWoNKWI1aKkjbdFJ6qFk+0J
GMGv4KeM7/UooMiKvyST5Kupfjel/CgpjbRb6tryAvXZBszizvQmmW0CLcLxmmnf
92sSJeQZ1+qh9+EOHRK6XusKRkPfjgFsjQ41KyvdFe9rR0WIaiovSzAk2WWZDWIR
W7Rhzm9Z7PhKMi9MTl+q2gOA02I1f9hc3NVF5jdEzdnrk4AoY8FnbLvkxYSYfFGl
PfDcpqJaM8LrpJAODmqCyQSlYeBXZWnRuxkU/mN6DtkhbsTrY+KO9PVueEUTHtEf
Cu7iNZkv6E/aislDjeYgvbKCScoQZcxqX5c0a9GnoPjbMOQDlnGUu6BqK0YCvxgD
51y7om0ioi1w0U2M37xCDaeYSQDEfdMIhtIsenY1SofIpfoUdqv6ngG2jGti58pA
uH+sdb3Nuc0=
-----END FGT VM LICENSE-----

--===============0740947994048919689==--
```

## History

| Date     | Release                                                                            | Change                  |
| -------- | ---------------------------------------------------------------------------------- | ----------------------- |
| 20190613 | [20190613](https://github.com/canada-ca-azure-templates/fortigateha/tree/20190613) | 1st release of template |
