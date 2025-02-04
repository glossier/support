---
external help file: JumpCloud-help.xml
Module Name: JumpCloud
online version: https://github.com/TheJumpCloud/support/wiki/Remove-JCUserGroupMember
schema: 2.0.0
---

# Remove-JCUserGroupMember

## SYNOPSIS
Removes a JumpCloud User from a JumpCloud User Group

## SYNTAX

### ByName (Default)
```
Remove-JCUserGroupMember [-GroupName] <String> [-Username] <String> [<CommonParameters>]
```

### ByID
```
Remove-JCUserGroupMember [[-GroupName] <String>] [-ByID] [-GroupID <String>] -UserID <String>
 [<CommonParameters>]
```

## DESCRIPTION
The Remove-JCUserGroupMember function is used to remove a JumpCloud User from a JumpCloud User Group. The user can be removed by Username or by UserID.

## EXAMPLES

### Example 1
```powershell
PS C:\> Remove-JCUserGroupMember -Username cclemons -GroupName 'The Band'
```

Removes the JumpCloud user with Username 'cclemons' from the User Group 'The Band'

### Example 2
```powershell
PS C:\> Get-JCUser | Where-Object sudo -EQ $false | Remove-JCUserGroupMember -GroupName 'Administrators'
```

Removes all JumpCloud users where the 'sudo' attribute is equal to $false from the User Group 'Administrators'

### Example 3
```powershell
PS C:\> Get-JCUser | Where-Object created -lt (Get-Date).AddDays(-7) | Remove-JCUserGroupMember -GroupName 'New Hires'
```

Removes all JumpCloud users not created within the last 7 days from the User Group 'New Hires'

### Example 4
```powershell
Get-JCUser | Select-Object username, @{name='Attribute Value'; expression={$_.attributes.value}} | Where-Object 'Attribute Value' -Like *Marketing* | Remove-JCUserGroupMember -GroupName Sales
```

Removes all JumpCloud users with a custom attribute value which contains 'Marketing' from the JumpCloud User Group 'Sales'. Note that to access the value of a nested property you must use Select-Object to access the nested property. In this example a calculated property is also used.
## PARAMETERS

### -ByID
Use the -ByID parameter when either the UserID or GroupID is passed over the pipeline to the Add-JCUserGroupMember function. The -ByID SwitchParameter will set the ParameterSet to 'ByID' which will increase the function speed and performance.

```yaml
Type: SwitchParameter
Parameter Sets: ByID
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -GroupID
The GroupID is used in the ParameterSet 'ByID'. The GroupID for a User Group can be found by running the command:
PS C:\> Get-JCGroup -type 'User'

```yaml
Type: String
Parameter Sets: ByID
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -GroupName
The name of the JumpCloud User Group that you want to remove the User from.

```yaml
Type: String
Parameter Sets: ByName
Aliases: name

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

```yaml
Type: String
Parameter Sets: ByID
Aliases: name

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -UserID
The _id of the User which you want to remove from the User Group.
To find a JumpCloud UserID run the command:
PS C:\> Get-JCUser | Select username, _id
The UserID will be the 24 character string populated for the _id field.
UserID has an Alias of _id. This means you can leverage the PowerShell pipeline to populate this field automatically using the Get-JCUser function before calling Remove-JCUserGroupMember. This is shown in EXAMPLES 2, 3, and 4.

```yaml
Type: String
Parameter Sets: ByID
Aliases: _id, id

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Username
The Username of the JumpCloud user you wish to remove from the User Group.

```yaml
Type: String
Parameter Sets: ByName
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters
This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable. For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).

## INPUTS

### System.String
## OUTPUTS

### System.Object
## NOTES

## RELATED LINKS
