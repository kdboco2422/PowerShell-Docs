---
external help file: PSITPro3_Management.xml
schema: 2.0.0
---

# Stop-Computer
## SYNOPSIS
Stops \(shuts down\) local and remote computers.

## SYNTAX

```
Stop-Computer [[-ComputerName] <String[]>] [[-Credential] <PSCredential>] [-AsJob]
 [-Authentication <AuthenticationLevel>] [-Force] [-Impersonation <ImpersonationLevel>]
 [-ThrottleLimit <Int32>] [-Confirm] [-WhatIf]
```

## DESCRIPTION
The Stop-Computer cmdlet shuts down computers remotely.
It can also shut down the local computer.

You can use the parameters of Stop-Computer to run the shutdown operations as a background job, to specify the authentication levels and alternate credentials, to limit the concurrent connections that are created to run the command, and to force an immediate shut down.

This cmdlet does not require Windows PowerShell remoting unless you use the AsJob parameter.

## EXAMPLES

### -------------------------- EXAMPLE 1 --------------------------
```
PS C:\>stop-computer
```

This command shuts down the local computer.

### -------------------------- EXAMPLE 2 --------------------------
```
PS C:\>stop-computer -computername Server01, Server02, localhost
```

This command stops two remote computers, Server01 and Server02, and the local computer, identified as "localhost".

### -------------------------- EXAMPLE 3 --------------------------
```
PS C:\>$j = stop-computer -computername Server01, Server02 -asjob
PS C:\>$results = $j | receive-job
PS C:\>$results
```

These commands run a Stop-Computer command as a background job on two remote computers, and then get the results.

The first command uses the AsJob parameter to run the command as a background job.
The command saves the resulting job object in the $j variable.

The second command uses a pipeline operator to send the job object in $j to the Receive-Job cmdlet, which gets the job results.
The command saves the results in the $results variable.

The third command displays the result saved in the $results variable.

Because the AsJob parameter creates the job on the local computer and automatically returns the results to the local computer, you can run the Receive-Job command as a local command.

### -------------------------- EXAMPLE 4 --------------------------
```
PS C:\>stop-computer -comp Server01 -impersonation anonymous -authentication PacketIntegrity
```

This command restarts the Server01 remote computer.
The command uses customized impersonation and authentication settings.

### -------------------------- EXAMPLE 5 --------------------------
```
PS C:\>$s = get-content domain01.txt
PS C:\>$c = get-credential domain01\admin01
PS C:\>stop-computer -computername $s -force -throttlelimit 10 -credential $c
```

These commands force an immediate shut down of all of the computers in Domain01.

The first command gets a list of computers in the domain and saves it in the $s variable.

The second command gets the credentials of a domain administrator and saves them in the $c variable.

The third command shuts down the computers.
It uses ComputerName parameter to submit the list of computers in the $s variable, the Force parameter to force an immediate shutdown, and the Credential parameter to submit the credentials saved in the $c variable.
It also uses the ThrottleLimit parameter to limit the command to 10 concurrent connections.

## PARAMETERS

### -AsJob
Runs the command as a background job.

Note: To use this parameter, the local and remote computers must be configured for remoting and, on Windows Vista and later versions of Windows, you must open Windows PowerShell with the "Run as administrator" option.
For more information, see about_Remote_Requirements".

When you use the AsJob parameter, the command immediately returns an object that represents the background job.
You can continue to work in the session while the job completes.
The job is created on the local computer and the results from remote computers are automatically returned to the local computer.
To manage the job, use the Job cmdlets.
To get the job results, use the Receive-Job cmdlet.

For more information about Windows PowerShell background jobs, see about_Jobs and see about_Remote_Jobs.

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

### -Authentication
Specifies the authentication level that is used for the  WMI connection.
\(Stop-Computer uses WMI.\) The default value is Packet.

Valid values are:

Unchanged:       The authentication level is the same as the previous command.

Default:         Windows Authentication.

None:            No COM authentication.

Connect:         Connect-level COM authentication.

Call:            Call-level COM authentication.

Packet:          Packet-level COM authentication.

PacketIntegrity: Packet Integrity-level COM authentication.

PacketPrivacy:   Packet Privacy-level COM authentication.

```yaml
Type: AuthenticationLevel
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: Packet (4)
Accept pipeline input: false
Accept wildcard characters: False
```

### -ComputerName
Stops the specified computers.
The default is the local computer.

Type the NETBIOS name, IP address, or fully qualified domain name of one or more computers in a comma-separated list.
To specify the local computer, type the computername or "localhost".

This parameter does not rely on Windows PowerShell remoting.
You can use the ComputerName parameter even if your computer is not configured to run remote commands.

```yaml
Type: String[]
Parameter Sets: (All)
Aliases: CN, __SERVER, Server, IPAddress

Required: False
Position: 1
Default value: Local computer
Accept pipeline input: true (ByPropertyName)
Accept wildcard characters: False
```

### -Credential
Specifies a user account that has permission to perform this action.
The default is the current user.

Type a user name, such as "User01" or "Domain01\User01", or enter a PSCredential object, such as one from the Get-Credential cmdlet.

```yaml
Type: PSCredential
Parameter Sets: (All)
Aliases: 

Required: False
Position: 2
Default value: Current user
Accept pipeline input: false
Accept wildcard characters: False
```

### -Force
Forces an immediate shut down of the computers.

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

### -Impersonation
Specifies the impersonation level to use when calling WMI.
\(Stop-Computer uses WMI.\) The default value is "Impersonate".

Valid values are:

Default:      Default impersonation.

Anonymous:    Hides the identity of the caller.

Identify:     Allows objects to query the credentials of the caller.

Impersonate:  Allows objects to use the credentials of the caller.

```yaml
Type: ImpersonationLevel
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: Impersonate
Accept pipeline input: false
Accept wildcard characters: False
```

### -ThrottleLimit
Specifies the maximum number of concurrent connections that can be established to run this command.
If you omit this parameter or enter a value of 0, the default value, 32, is used.

The throttle limit applies only to the current command, not to the session or to the computer.

```yaml
Type: Int32
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: 32
Accept pipeline input: false
Accept wildcard characters: False
```

### -Confirm
Prompts you for confirmation before running the cmdlet.Prompts you for confirmation before running the cmdlet.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: false
Accept pipeline input: false
Accept wildcard characters: False
```

### -WhatIf
Shows what would happen if the cmdlet runs.
The cmdlet is not run.Shows what would happen if the cmdlet runs.
The cmdlet is not run.

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases: 

Required: False
Position: Named
Default value: false
Accept pipeline input: false
Accept wildcard characters: False
```

## INPUTS

### None
You cannot pipe input to this cmdlet.

## OUTPUTS

### None or System.Management.Automation.RemotingJob
When you use the AsJob parameter, the cmdlet returns a job object \(System.Management.Automation.RemotingJob\).
Otherwise, it does not generate any output.

## NOTES
This cmdlet uses the Win32Shutdown method of the Win32_OperatingSystem WMI class.

In Windows PowerShell 2.0, the AsJob parameter does not work reliably when you are restarting/stopping remote computers.
In Windows PowerShell 3.0, the implementation is changed to resolve this problem.

## RELATED LINKS

[Online Version:](http://go.microsoft.com/fwlink/?LinkID=135263)

[Add-Computer](712f3460-c5d0-4af8-8de6-6d06e4a1a838)

[Checkpoint-Computer](9ef7dd97-dbd9-43de-8988-9ab85e7827ad)

[Remove-Computer](89871167-713a-4f43-af35-e2891b8849e6)

[Rename-Computer](60054009-a41f-468d-91d9-815b63dbdf48)

[Restart-Computer](ba50f64c-866e-4315-91c7-0ce16b44c47e)

[Restore-Computer](c570f18d-f1dd-462a-b00b-3eb1d2a81dfc)

[Test-Connection](7c54e3a1-8d8c-44ad-9056-ef0514c158d6)

