# PowerPlatform-PowerApps-PowerAutomate-Dataverse-UnboundAction-ShareAndAssign

Dataverse アクション（バインドされていないアクション）を Power Automate クラウドフローから呼び出して、レコードの共有／レコードの割り当てを行う

---

<br><br><br><br><br><br>

## GrantAccess unbound action

<br><br>

- Target

```plaintext
# 接頭辞_論理名の複数形(共有するレコードのGUID)
pre_tablenames(GUID)

例:
ya_applications(11111111-1111-1111-1111-111111111111)
```

<br><br>

- PrincipalAccess

```json
{
  "AccessMask": "ReadAccess,WriteAccess,AppendAccess,AppendToAccess,CreateAccess,DeleteAccess,ShareAccess,AssignAccess",
  "Principal": {
    "@{string('@odata.type')}": "Microsoft.Dynamics.CRM.systemuser",
    "systemuserid": "<Systemuser GUID>"
  }
}
```

[AccessRights Enum (Microsoft.Crm.Sdk.Messages)](https://learn.microsoft.com/en-us/dotnet/api/microsoft.crm.sdk.messages.accessrights?view=dataverse-sdk-latest)

<br><br><br><br><br><br>

---

Copyright (c) 2023 YA-androidapp(https://github.com/yzkn) All rights reserved.
