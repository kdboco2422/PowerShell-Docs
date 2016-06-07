---
external help file: PSITPro3_Utility.xml
schema: 2.0.0
---

# Get-Variable
## SYNOPSIS
Gets the variables in the current console.

## SYNTAX

```
Get-Variable [[-Name] <String[]>] [-Exclude <String[]>] [-Include <String[]>] [-Scope <String>] [-ValueOnly]
```

## DESCRIPTION
The Get-Variable cmdlet gets the Windows PowerShell variables in the current console.
You can retrieve just the values of the variables by specifying the ValueOnly parameter, and you can filter the variables returned by name.

## EXAMPLES

### -------------------------- EXAMPLE 1 --------------------------
```
PS C:\>Get-Variable m*
```

This command gets variables with names that begin with the letter "m".
The command also gets the value of the variables.

### -------------------------- EXAMPLE 2 --------------------------
```
PS C:\>Get-Variable m* -Valueonly
```

This command gets only the values of the variables that have names that begin with "m".

### -------------------------- EXAMPLE 3 --------------------------
```
PS C:\>Get-Variable -Include M*,P*
```

This command gets information about the variables that begin with either the letter "M" or the letter "P".

### -------------------------- EXAMPLE 4 --------------------------
```
PS C:\>Get-Variable -Scope 0
PS C:\>Compare-Object (Get-Variable -Scope 0) (Get-Variable -Scope 1)
```

The first command gets only the variables that are defined in the local scope.
It is equivalent to "Get-Variable -Scope Local" and can be abbreviated as "gv -s 0".

The second command uses the Compare-Object cmdlet to find the variables that are defined in the parent scope \(Scope 1\) but are visible only in the local scope \(Scope 0\).

## PARAMETERS

### -Exclude
Omits the specified items.
Wildcards are permitted.

```yaml
Type: String[]
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: 
Accept pipeline input: false
Accept wildcard characters: True
```

### -Include
Specifies only the items upon which the cmdlet will act, excluding all others.
Wildcards are permitted.

```yaml
Type: String[]
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: 
Accept pipeline input: false
Accept wildcard characters: True
```

### -Name
Specifies the name of the variable.
Wildcards are permitted.
You can also pipe a variable name to Get-Variable.

```yaml
Type: String[]
Parameter Sets: (All)
Aliases: 

Required: False
Position: 1
Default value: 
Accept pipeline input: true (ByValue, ByPropertyName)
Accept wildcard characters: True
```

### -Scope
Gets only the variables in the specified scope.
Valid values are "Global", "Local", or "Script", or a number relative to the current scope \(0 through the number of scopes, where 0 is the current scope and 1 is its parent\).
"Local" is the default.
For more information, see about_Scopes.

```yaml
Type: String
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: Local
Accept pipeline input: false
Accept wildcard characters: False
```

### -ValueOnly
Gets only the value of the variable.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: False
Accept pipeline input: false
Accept wildcard characters: False
```

## INPUTS

### System.String
You can pipe a string that contains the variable name to Get-Variable.

## OUTPUTS

### System.Management.Automation.PSVariable
Get-Variable returns a System.Management.Automation variable object for each variable that it gets.
The object type depends on the variable.

## NOTES
This cmdlet does not manage environment variables.
To manage environment variables, you can use the environment variable provider.

## RELATED LINKS

[Online Version:](http://go.microsoft.com/fwlink/?LinkID=113336)

[Clear-Variable](e8e9af2f-e5c9-4ab8-8518-b305b1c4494a)

[New-Variable](5c7c621f-c086-4286-8f9b-86cadecb8c0b)

[Remove-Variable](a58fb01b-6bb4-48e9-a07c-5ad907dc4791)

[Set-Variable](a961f6e3-12d2-4210-a039-62f502623a8c)

