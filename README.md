# PowerPlatform-PowerApps-PowerAutomate-Dataverse-UnboundAction-ShareAndAssign

Dataverse アクション（バインドされていないアクション）を Power Automate クラウドフローから呼び出して、レコードの共有／レコードの割り当てを行う

---

<br><br><br><br>

## GrantAccess unbound action

<br><br><br>

### Target

```plaintext
# 接頭辞_論理名の複数形(共有するレコードのGUID)
pre_tablenames(GUID)

例:
ya_applications(11111111-1111-1111-1111-111111111111)
```

<br><br><br>

### PrincipalAccess

```json
{
  "AccessMask": "ReadAccess,WriteAccess,AppendAccess,AppendToAccess,CreateAccess,DeleteAccess,ShareAccess,AssignAccess",
  "Principal": {
    "@{string('@odata.type')}": "Microsoft.Dynamics.CRM.systemuser",
    "systemuserid": "<Systemuser GUID>"
  }
}
```

<br><br>

#### [AccessRights Enum (Microsoft.Crm.Sdk.Messages)](https://learn.microsoft.com/en-us/dotnet/api/microsoft.crm.sdk.messages.accessrights?view=dataverse-sdk-latest)

| Name           | Value  | Description                                                                        |
|----------------|--------|------------------------------------------------------------------------------------|
| None           | 0      | No access. Value = 0x00.                                                           |
| ReadAccess     | 1      | The right to read the specified type of record. Value = 0x01.                      |
| WriteAccess    | 2      | The right to update the specified record. Value = 0x02.                            |
| AppendAccess   | 4      | The right to append the specified record to another object. Value = 0x04.          |
| AppendToAccess | 16     | The right to append another record to the specified object. Value = 0x10.          |
| CreateAccess   | 32     | The right to create a record. Value = 0x20.                                        |
| DeleteAccess   | 65536  | The right to delete the specified record. Value = 0x10000.                         |
| ShareAccess    | 262144 | The right to share the specified record. Value = 0x40000.                          |
| AssignAccess   | 524288 | The right to assign the specified record to another user or team. Value = 0x80000. |

<br><br>

#### [アクセス権間の依存関係](https://learn.microsoft.com/ja-jp/power-apps/developer/data-platform/security-access-rights#dependencies-between-access-rights)

| 操作                                           | 必要なアクセス権                                                                                                                                                                    |
| ---------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| レコードを作成して、そのレコードの所有者になる | CREATE、READ                                                                                                                                                                        |
| レコードの共有                                 | SHARE。 共有操作を実行するユーザーにはこのアクセス権が必要です。 <br> READ。 共有操作を実行するユーザーにはこのアクセス権が必要です。レコードが共有されているユーザーにも必要です。 |
| レコードの割り当て                             | ASSIGN、WRITE、READ                                                                                                                                                                 |
| レコードを追加する                             | WRITE、READ、APPENDTO                                                                                                                                                               |
| レコードを追加する                             | WRITE、READ、APPEND                                                                                                                                                                 |

<br><br><br>

---

Copyright (c) 2025 YA-androidapp(https://github.com/yzkn) All rights reserved.
