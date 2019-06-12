<!--
Version 0.1
-->


#  Table of Contents
1. [Understanding PowerShell JEA](#understanding-powershell-jea)
    1. [Sign in to SRV01](#sign-in-to-srv01)
    1. [Open the Windows PowerShell ISE](#open-the-windows-powershell-ise)
    1. [Open the PowerShell script](#open-the-powershell-script-1)
    1. [Read the script description](#read-the-script-description-1)
    1. [Store non-admin credentials](#store-non-admin-credentials-1)
    1. [Connect to a JEA endpoint](#connect-to-a-jea-endpoint)
    1. [List the endpoint commands](#list-the-endpoint-commands-1)
    1. [Show the ConnectedUser and RunAsUser context](#show-the-connecteduser-and-runasuser-context)
    1. [Execute the admin command as non-admin](#execute-the-admin-command-as-non-admin)
    1. [Execute a command not included in the endpoing](#execute-a-command-not-included-in-the-endpoint)
    1. [Disconnect from the endpoint](#disconnect-from-the-endpoint-1)
    1. [Repeat the last command as admin](#repeat-the-last-command-as-admin)
    1. [Close the Windows PowerShell ISE](#close-the-windows-powershell-ise)
1. [Creating and managing a JEA endpoint](#creating-and-managing-a-jea-endpoint)
    1. [Open an elevated Windows PowerShell ISE window](#open-an-elevated-windows-powershell-ise-window-1)
    1. [Open the PowerShell script](#open-the-powershell-script-2)
    1. [Read the script description](#read-the-script-description-2)
    1. [Show all PowerShell remoting endpoints](#show-all-powershell-remoting-endpoints)
    1. [Unregister the JEA_Demo endpoint](#unregister-the-jeademo-endpoint)
    1. [Show all PowerShell remoting endpoints again](#show-all-powershell-remoting-endpoints-again)
    1. [Re-register the JEA_Demo endpoint](#re-register-the-jeademo-endpoint)
    1. [Create an endpoint configuration file](#create-an-endpoint-configuration-file)
    1. [Open the file](#open-the-file)
    1. [Review the file contents](#review-the-file-contents-1)
    1. [Modify the SessionType value](#modify-the-sessiontype-value)
    1. [Modify the TranscriptDirectory value](#modify-the-transcriptdirectory-value)
    1. [Modify the RunAsVirtualAccount value](#modify-the-runasvirtualaccount-value)
    1. [Modify the RoleDefinitions value](#modify-the-roledefinitions-value)
    1. [Save the file](#save-the-file-1)
    1. [Close the JeaDEMO2.pssc file](#close-the-jeademo2pssc-file)
    1. [Register a new JEA endpoint](#register-a-new-jea-endpoint)
    1. [Store non-admin-credentials](#store-non-admin-credentials-2)
    1. [List the endpoint commands](#list-the-endpoint-commands-2)
    1. [Show the Demo_Module file structure](#show-the-demomodule-file-structure)
    1. [Open the Maintenance.psrc file](#open-the-maintenancepsrc-file)
    1. [Review the file contents](#review-the-file-contents-2)
    1. [Modify the VisibleExternalCommands value](#modify-the-visibleexternalcommands-value)
    1. [Modify the VisibleCmdlets value](#modify-the-visiblecmdlets-value)
    1. [Save the file](#save-the-file-2)
    1. [Close the Maintenance.psrc file](#close-the-maintenancepsrc-file)
    1. [Connect to JEA_Demo2](#connect-to-jeademo2)
    1. [List the endpoint commands](#list-the-endpoint-commands)
    1. [Restart the Spooler service](#restart-the-spooler-service)
    1. [Restart the WSearch service](#restart-the-wsearch-service)
    1. [Invoke ipconfig](#invoke-ipconfig)
    1. [Confirm that you can restart the computer](#confirm-that-you-can-restart-the-computer)
    1. [Disconnect from the endpoint](#disconnect-from-the-endpoint-2)
    1. [Close the Windows PowerShell ISE window](#close-the-windows-powershell-ise-window-1)
1. [Working with the user drive in a JEA endpoint](#working-with-the-user-drive-in-a-jea-endpoint)
    1. [Open an elevated Windows PowerShell ISE window](#open-an-elevated-windows-powershell-ise-window-2)
    1. [Open the PowerShell script](#open-the-powershell-script-3)
    1. [Review the script contents](#review-the-script-contents)
    1. [Run the script](#run-the-script)
    1. [Close the file](#close-the-file)
    1. [Open the PowerShell script](#open-the-powershell-script-4)
    1. [Read the script description](#read-the-script-description-3)
    1. [Store non-admin credentials](#store-non-admin-credentials-3)
    1. [Create a remoting session](#create-a-remoting-session)
    1. [Get the user drive location](#get-the-user-drive-location)
    1. [Generate a new process report](#generate-a-new-process-report)
    1. [Copy the report locally](#copy-the-report-locally)
    1. [Open the report](#open-the-report)
    1. [Close the report](#close-the-report)
    1. [Show the user drive root folder contents](#show-the-user-drive-root-folder-contents)
    1. [Close the remoting session](#close-the-remoting-session)
    1. [Verify the user drive root folder still exists](#verify-the-user-drive-root-folder-still-exists)
    1. [Close the Windows PowerShell ISE window](#close-the-windows-powershell-ise-window-2)
1. [Reporting on JEA](#reporting-on-jea)
    1. [Open an elevated Windows PowerShell ISE window](#open-an-elevated-windows-powershell-ise-window-3)
    1. [Open the PowerShell script](#open-the-powershell-script-5)
    1. [Read the script description](#read-the-script-description-4)
    1. [List all JEA endpoints](#list-all-jea-endpoints)
    1. [List the endpoint commands for a specific user](#list-the-endpoint-commands-for-a-specific-user)
    1. [View the JEA session transcripts](#view-the-jea-session-transcripts)
    1. [Review the PowerShell event log entries](#review-the-powershell-event-log-entries)
    1. [Close the Windows PowerShell ISE window](#close-the-windows-powershell-ise-window-3)
1. [Deployment and maintenance with DSC](#deployment-and-maintenance-with-dsc)
    1. [Open an elevated Windows PowerShell ISE window](#open-an-elevated-windows-powershell-ise-window-4)
    1. [Open the PowerShell script](#open-the-powershell-script-6)
    1. [Read the script description](#read-the-script-description-5)
    1. [Define a sample JEA configuration](#define-a-sample-jea-configuration)
    1. [Bypass some security checks](#bypass-some-security-checks)
    1. [Store admin credentials](#store-admin-credentials)
    1. [Generate a MOF file for deployment to srv02](#generate-a-mof-file-for-deployment-to-srv02)
    1. [Push the MOF file to a remote server](#push-the-mof-file-to-a-remote-server)
    1. [Store non-admin credentials](#store-non-admin-credentials-4)
    1. [Enter a session inside the remote JEA endpoint](#enter-a-session-inside-the-remote-jea-endpoint)
    1. [List connection information from the endpoint](#list-connection-information-from-the-endpoint)
    1. [Exit the remoting session](#exit-the-remoting-session)
    1. [End the lab](#end-the-lab)

* * *

# Understanding PowerShell JEA TEST
>LODSProperties
>* IntroductionUri = https://lodmanuals.blob.core.windows.net/manuals/Ignite 2016/Videos/IDL4002_new content/Experiencing PowerShell JEA.mp4

## INTRODUCTION MESSAGE 

In this exercise, you will connect to an existing JEA endpoint that will allow
you to invoke the Restart-Service cmdlet as well as a custom Get-UserInfo
function.

## COMPLETION MESSAGE

Congratulations! You have now finished the first exercise! You should have
a good idea of what JEA is by now. Click **Continue** to advance to the
next exercise.

---

### Sign in to SERVER!

If necessary, click the **Switch to Machine** icon to the right of this
instruction, and then sign in to **SRV01** as **CONTOSO\LabAdmin** using
**Passw0rd!** as the password.

#### :computer: ACTIONS 

>LODSProperties
>* VM = SRV01

---

### Open the Windows PowerShell ISE

On the taskbar, click **Windows PowerShell ISE**.

#### :camera: SCREENSHOT

>LODSProperties
>* Uri = screens/open-windows-powershell-ise.png 
>* ShowAutomatically = No

#### :calling: COMMAND

```PowerShell
powershell_ise.exe
```

---

### Open the PowerShell script

On the File menu, click **Open**. Browse to
**C:\JEA\Exercises\1-JEAIntro.ps1**, and then click **Open**.

#### :bulb: KNOWLEDGE

In the PowerShell ISE, you can also open files in the editor by invoking the
psedit filePath command. This can be very convenient when you're working in the
embedded PowerShell console and you want to have a look at a file in the
current working folder.

For example, you could have invoked psedit C:\JEA\Exercises\1-JEAIntro.ps1 in
the embedded PowerShell console to open the file you were asked to open in this
exercise.

#### :camera: SCREENSHOT

>LODSProperties
>* Uri = screens/open-the-powershell-script-1.png
>* ShowAutomatically = No

![](screens/open-the-powershell-script-1.png)

---

### Read the script description

Read the comments at the top of the **1-JEAIntro.ps1** file.

#### :bulb: KNOWLEDGE

The 1-JEAIntro.ps1 script file contains the Enter-PSSession and the
Exit-PSSession commands. These two commands are for interactive use in
PowerShell only and they should not be invoked as part of a larger script. That
is why the commands in this file must be run one at a time.

#### :camera: SCREENSHOT

>LODSProperties
>* Uri = screens/read-the-script-description-1.png 
>* ShowAutomatically = No

---

### Store non-admin credentials

Run the command on **line 20**. When prompted, enter the password **Passw0rd!**.

#### :warning: ALERT

Unlike normal scripts that you would usually run to completion, for this
exercise, you must run the commands in the 1-JEAIntro.ps1 script file one at a
time. Please view the **Screenshot** and click the **Knowledge** [Bulb in head]
icon for instructions on how to run commands one at a time.

#### :bulb: KNOWLEDGE

You can invoke individual commands in an open script file in any of the
following ways:

1. Place your cursor anywhere on the line with the command you want to invoke,
and then press **F8** (recommended).
1. Place your cursor anywhere on the line with the command you want to invoke,
and then on the toolbar, click **Run Selection**.
1. Copy the command, and then paste it into the integrated PowerShell console.

It's a good idea to get used to using shortcuts like F8 to run the current or
selected command so that you can work more efficiently.

#### :camera: SCREENSHOT

>LODSProperties
>* Uri = screens/store-non-admin-credentials.png 
>* ShowAutomatically = No


---

### Connect to a JEA endpoint

Run the command on **line 23**.

#### :bulb: KNOWLEDGE

This command will open an interactive remote PowerShell connection to the
JEA_Demo endpoint on the local machine and will place you inside of that session
as though you were CONTOSO\BenSmith. The change in the PowerShell prompt to
[localhost]: PS> provides you with a visual cue indicating that you are working
inside of a remote session on localhost.

#### :camera: SCREENSHOT

>LODSProperties
>* Uri = screens/connect-to-a-jea-endpoint.png 
>* ShowAutomatically = No

---

### List the endpoint commands

Run the command on **line 26**.

#### :bulb: KNOWLEDGE

When you are inside a remote JEA Endpoint, invoking the Get-Command command will
show you a list of the commands that are available to you in the JEA endpoint to
which you connected. The commands you see will always be a very limited subset
of the commands that are normally available in PowerShell.

By default, all JEA endpoints include seven default JEA cmdlets. The JEA_Demo
endpoint includes two additional commands-Get-UserInfo and Restart-Service-that
were explicitly added to it when it was created. You will learn how to create a
JEA endpoint and add commands to it in a later exercise.

#### :camera: SCREENSHOT

>LODSProperties
>* Uri = screens/list-the-endpoint-commands-1.png 
>* ShowAutomatically = No

---

### Show the ConnectedUser and RunAsUser context

Run the command on **line 29**.

#### :bulb: KNOWLEDGE

The Get-UserInfo function that is included in the JEA_Demo JEA endpoint lets
you look at the user context under which this session is operating. The
properties that are output include the ConnectedUser as well as the RunAsUser.
ConnectedUser is the account that was used to connect to the remote session-for
example, your user account, which is CONTOSO\BenSmith in this session. RunAsUser
is a privileged virtual account that is created when the session is created and
destroyed when the session is closed. It performs actions on behalf of the
connected user.

The connected user does not need to have administrator privileges. All actions
taken by the connected user while connected to a JEA endpoint are performed in
the context of the privileged RunAs account. By connecting as one user and
running as a privileged user, you allow non-privileged users to perform specific
administrative tasks without giving them administrative rights.

With JEA, administrative commands can only be invoked by the non-admin connected
user through the JEA endpoint in which the commands are exposed. The non-admin
connected user cannot invoke the same administrative commands outside of a JEA
session.

#### :camera: SCREENSHOT

>LODSProperties
>* Uri = screens/show-the-connecteduser-and-runasuser-context.png 
>* ShowAutomatically = No

---

### Execute the admin command as non-admin

Run the command on **line 32**.

#### :bulb: KNOWLEDGE

This command demonstrates JEA in action. Normally, Restart-Service requires
administrative privileges to run; however, with JEA, a virtual RunAs account
executes commands that you invoke inside of the JEA endpoint on your behalf,
and that account has the administrative privileges that are needed. This is why
you are able to restart a service even though you connected to the JEA endpoint
by using non-privileged credentials (CONTOSO\BenSmith).

#### :camera: SCREENSHOT

>LODSProperties
>* Uri = screens/execute-the-command-as-non-admin.png
>* ShowAutomatically = No

---

### Execute a command not included in the endpoint

Run the command on **line 35**.

#### :bulb: KNOWLEDGE

Notice that JEA will prevent you from running this command successfully. Since
this command was not explicitly added to the JEA endpoint for the user
CONTOSO\BenSmith, the virtual RunAs account cannot run it, even though it has
the privileges required to do so.

JEA allows you to limit the commands exposed to specific users inside of a JEA
endpoint. It also allows you to limit what specific users can do with commands
that are exposed to them. You will learn more about this in the next exercise.

#### :camera: SCREENSHOT

>LODSProperties
>* Uri = screens/execute-a-command-not-included-in-the-endpoint.png 
>* ShowAutomatically = No|Once|EveryTime

---

### Disconnect from the endpoint

Run the command on **line 38**.

#### :bulb: KNOWLEDGE

Disconnecting from a JEA endpoint closes the JEA session and causes PowerShell
to delete the virtual RunAs account that was created when the session was
created (when you connected to the JEA endpoint). If you connected to a JEA
endpoint by using specific user credentials, when you disconnect from that
endpoint, you will return to the local session in your own security context.

---

### Repeat the last command as admin

Run the command on **line 42**.

#### :bulb: KNOWLEDGE

This command is the same command that you couldn't run a moment ago while using
CONTOSO\BenSmith, but that you have access to as CONTOSO\LabAdmin. This
demonstrates how you were able to change your user context inside of a JEA
endpoint, with all commands invoked by using a virtual RunAs account on behalf
of CONTOSO\BenSmith.

#### :camera: SCREENSHOT

>LODSProperties
>* Uri = screens/repeat-the-last-command-as-admin.jpg 
>* ShowAutomatically = No

---

### Close the Windows PowerShell ISE

On the File menu, click **Exit**.

* * *

# Creating and managing a JEA endpoint

>LODSProperties
>* IntroductionUri = https://lodmanuals.blob.core.windows.net/manuals/Ignite 2016/Videos/IDL4002_new content/Creating and Managing a JEA Endpoint.mp4

## INTRODUCTION MESSAGE

In this exercise, you will create an exact replica of the demo JEA endpoint you
used in the last exercise. You will then modify that endpoint by adding some
commands to it and restricting others, and then you will verify that those
modifications were automatically applied to the endpoint.

## COMPLETION MESSAGE

Congratulations! You now understand what JEA endpoints allow you to do, and you
know how to create and manage JEA endpoints. Click Continue to advance to the
next exercise.

---

### Open an elevated Windows PowerShell ISE window

On the taskbar, right-click **Windows PowerShell**, and then click **Run ISE as
Administrator**. Click Yes when prompted by UAC.

#### :bulb: KNOWLEDGE

Creation and management of JEA endpoints requires elevation.

---

### Open the PowerShell script

On the File menu, click **Open**. Browse to
**C:\JEA\Exercises\2-JEACreateAndManage.ps1**, and then click **Open**.

#### :camera: SCREENSHOT

>LODSProperties
>* Uri = screens/open-the-powershell-script-2.png 
>* ShowAutomatically = No

---

### Read the script description

Read the comments at the top of the **2-JEACreateAndManage.ps1** file.

#### :camera: SCREENSHOT

>LODSProperties
>* Uri = screens/read-the-script-description-2.png
>* ShowAutomatically = No

---

### Show all PowerShell remoting endpoints

Run the command on **line 18**.

#### :bulb: KNOWLEDGE

JEA uses restricted PowerShell remoting endpoints to provide delegated
administration using role-based access control. The Get-PSSessionConfiguration
command shows you all PowerShell remoting endpoints on the system-session
configuration is just a fancy name for endpoint. Most of the endpoints shown in
the output of this command are created by default in Windows. The JEA_Demo
endpoint is one that was specifically added and configured for JEA to allow you
to understand how JEA works by completing the tasks in the previous exercise.

#### :camera: SCREENSHOT

>LODSProperties
>* Uri = screens/show-all-powershell-remoting-endpoints.png
>* ShowAutomatically = No

---

### Unregister the JEA_Demo endpoint

Run the command on **line 21**.

#### :bulb: KNOWLEDGE

JEA endpoints must be registered on a system in order for them to be available
for connections, and they must be unregistered to remove them from the list of
available endpoints. When you unregister a JEA endpoint, you can no longer
connect to the endpoint, but the files that were used to create the endpoint
remain on the disk in case you need them later.

#### :camera: SCREENSHOT

>LODSProperties
>* Uri = screens/unregister-the-jeademo-endpoint.png
>* ShowAutomatically = No

---

### Show all PowerShell remoting endpoints again

Run the command on **line 24**.

#### :bulb: KNOWLEDGE

Since you unregistered the JEA_Demo endpoint, it no longer appears in the list
of endpoints available for connection on this system. If someone were to try to
use Enter-PSSession to connect to that JEA endpoint, the command would fail
because the JEA endpoint is no longer registered.

#### :camera: SCREENSHOT

>LODSProperties
>* Uri = screens/show-all-powershell-remoting-endpoints-again.png
>* ShowAutomatically = No

---

### Re-register the JEA_Demo endpoint

Run the command on **line 27**.

#### :bulb: KNOWLEDGE

Registration of a JEA endpoint does not establish a link between the endpoint
and the configuration file. The configuration file can be moved or discarded
once registration is complete; however, you should keep your configuration files
if you want to be able to easily change the configuration of a JEA endpoint
later.

In this command, you are re-registering the JEA_Demo endpoint using the same
configuration file that was used when it was originally registered. In this
case, you did not modify the file, but you could have. When you need to make
configuration changes to a JEA endpoint itself, such as enabling or disabling
the User drive, or adding or removing role assignments for users or groups, it
is much easier to make those modifications when you have access to the
configuration file that was used to register the endpoint. These last three
tasks demonstrate the steps you would take to change the configuration of a JEA
endpoint that is registered in your environment.

#### :camera: SCREENSHOT

>LODSProperties
>* Uri = screens/re-register-the-jeademo-endpoint.png
>* ShowAutomatically = No

---

### Create an endpoint configuration file

Run the command on **line 30**.

#### :bulb: KNOWLEDGE

To create a new JEA endpoint, you must first produce at least two files:

1. A PowerShell session configuration file.
1. One or more PowerShell Role Capability files.

A PowerShell session configuration (.pssc) file defines the configuration of an
endpoint. JEA requires several specific configuration settings in order to work
properly, and those settings are added to this type of file.

PowerShell Role Capability (.psrc) files define the capabilities of a role that
is exposed through a JEA endpoint. This includes the commands that can be
executed in an endpoint as well as any restrictions that are placed on those
commands.

In this task, you create a new session configuration file by using the
New-PSSessionConfiguration cmdlet. When you first start creating session
configuration files by using New-PSSessionConfiguration, you should always
invoke that cmdlet with the -Full switch parameter. This parameter tells
PowerShell to add placeholders for every option that is available to the session
configuration file that is generated. This is a great way to learn what is
possible with these files. You will see the options that are available when you
open the file in the next task.

#### :camera: SCREENSHOT

>LODSProperties
>* Uri = screens/create-an-endpoint-configuration-file.png
>* ShowAutomatically = No

---

### Open the file

Run the command on **line 33**. A new tab opens in the script pane.

#### :bulb: KNOWLEDGE

The psedit command is an easy way to open files you want to edit in the
PowerShell ISE.

#### :camera: SCREENSHOT

>LODSProperties
>* Uri = screens/open-the-file.png
>* ShowAutomatically = No

---

### Review the file contents

Review the contents of the **JEADDemo2.pssc** file.

#### :bulb: KNOWLEDGE

A PowerShell Session Configuration file-also known as a PowerShell endpoint
configuration file-is a lot like a PowerShell module manifest (.psd1). It
contains key-value pairs that define the configuration of the PowerShell
endpoint.

After you create one of these files by using the New-PSSessionConfigurationFile
cmdlet, you must make several modifications to the file contents before it can
be used to register a new JEA endpoint. You will modify this file in the next
few tasks so that you can later register a new JEA endpoint, referencing this
file as the configuration file.

#### :camera: SCREENSHOT

>LODSProperties
>* Uri = screens/review-the-file-contents-1.png
>* ShowAutomatically = No

---

### Modify the SessionType value

In the SessionType field value on line 22, type **'RestrictedRemoteServer'**.

#### :bulb: KNOWLEDGE

The SessionType field defines the preset default settings that will be used when
an endpoint is registered with the session configuration file. When this field
is set to RestrictedRemoteServer, any endpoint that is registered with it will:

1. Automatically include the Get-Command, Get-FormatData, Select-Object, 
Get-Help, Measure-Object, Exit-PSSession, Clear-Host, and Out-Default cmdlets.
1. Set the ExecutionPolicy to RemoteSigned.
1. Set the LanguageMode to NoLanguage.

The net effect of these settings is a secure and minimal starting point for
configuring your JEA endpoint.

#### :camera: SCREENSHOT

>LODSProperties
>* Uri = screens/modify-the-sessiontype-value.png
>* ShowAutomatically = No

#### :calling: COMMAND TypeText

```Text
'RestrictedRemoteServer'
```

---

### Modify the TranscriptDirectory value

Uncomment the line with the **TranscriptDirectory** field, and then replace the
field value with **"C:\ProgramData\JEAConfiguration\Transcripts"**.

#### :bulb: KNOWLEDGE

The TranscriptDirectory field defines where the transcripts of each PowerShell
endpoint session are saved. Whenever someone connects to an endpoint with this
field set, PowerShell starts recording a new transcript, and when someone
disconnects from an endpoint, PowerShell stops recording the transcript. These
transcripts allow you to audit sessions by inspecting the actions taken in each
session in an easily readable way.

Note that Windows Eventing can also be used to capture information about what
each user ran with PowerShell; however, PowerShell transcripts are a little more
readable, with the command output inline just as it appears during a session.

#### :camera: SCREENSHOT

>LODSProperties
>* Uri = screens/modify-the-transcriptdirectory-value.png
>* ShowAutomatically = No

#### :calling: COMMAND TypeText

```Text
'C:\ProgramData\JEAConfiguration\Transcripts'
```

---

### Modify the RunAsVirtualAccount value

Uncomment the line with the **RunAsVirtualAccount** field.

#### :bulb: KNOWLEDGE

The RunAsVirtualAccount field indicates that PowerShell should run as a virtual
account whenever anyone connects to this endpoint. By default, virtual accounts
used in this fashion are a member of the built-in local Administrators group. If
the endpoint is on a domain controller, the virtual account is also a member of
the Domain Administrators group.

The virtual account is automatically created when someone connects to the
endpoint, and it is automatically destroyed when the same person disconnects
from that endpoint. This provides safer delegation by eliminating the need to
manually manage membership of the local Administrators group and Domain
Administrators group.

#### :camera: SCREENSHOT

>LODSProperties
>* Uri = screens/modify-the-runasvirtualaccount-value.png
>* ShowAutomatically = No

---

### Modify the RoleDefinitions value

Select the entire **line 46** with the **RoleDefinitions** field, and then click
the **Type Text** button to the right of this message. The **Screenshot** shows
the expected result.

#### :bulb: KNOWLEDGE

The RoleDefinitions field assigns role capabilities by name to specific users or
groups. Role capabilities define exactly what can be done as a privileged
account. With this field, you can specify the functionality available to any
connecting user directly or based on group membership. This is the core of JEA's
RBAC functionality.

With this modification, you are exposing the pre-made maintenance role
capability-defined in a role capability file that is placed in a module for
discoverability-to the CONTOSO\BenSmith user account.

#### :camera: SCREENSHOT

>LODSProperties
>* Uri = screens/modify-the-roledefinitions-value.png
>* ShowAutomatically = No

#### :calling: COMMAND TypeText

```Text
RoleDefinitions = @{'CONTOSO\BenSmith' = @{RoleCapabilities = 'Maintenance'}}
```

---

### Save the file

Press **Ctrl+S** to save the **JEADemo2.pssc** configuration file.

---

### Close the JEADemo2.pssc file

Close the **JEADemo2.pssc** file to return to the **2-JEACreateAndManage.ps1**
file.

---

### Register a new JEA endpoint

Run the command on **line 36**.

#### :bulb: KNOWLEDGE

Once you have created a new endpoint configuration file that is suitable for a
JEA endpoint, you need to register it in order for the JEA endpoint to be
available for connections. The Register-PSSessionConfiguration cmdlet allows you
to register new JEA endpoints with an endpoint configuration (.pssc) file.

When you register a JEA endpoint, no direct association with the endpoint
configuration file used during the registration is retained. You can move or
delete the endpoint configuration file after the endpoint is registered without
affecting the registered endpoint; however, it is not recommended to delete
these files because you may want to use them later to re-register an endpoint
with a slightly different configuration.

#### :camera: SCREENSHOT

>LODSProperties
>* Uri = screens/register-a-new-jea-endpoint.png
>* ShowAutomatically = No

---

### Store non-admin credentials

Run the command on **line 40**. When prompted, enter **Passw0rd!** as the
password.

---

### List the endpoint commands

Run the command on **line 43**.

#### :bulb: KNOWLEDGE

You can work with JEA endpoints interactively by using Enter-/Exit-PSSession or
remotely by using Invoke-Command.

As you can see from the output, the new JEA endpoint you just created exposes
the same set of commands as the one you used in the previous exercise.

#### :camera: SCREENSHOT

>LODSProperties
>* Uri = screens/list-the-endpoint-commands-2.png
>* ShowAutomatically = No

---

### Show the Demo_Module file structure

Run the command on **line 46**.

#### :bulb: KNOWLEDGE

This command shows you that there is a Maintenance.psrc file in a
RoleCapabilities subfolder of the Demo_Module module. This is discoverable by
using the PSModulePath environment variable. Role capability (.psrc) files
define what a user can do in a JEA endpoint. They identify a whitelist of things
like visible commands, visible applications, and more.

When you registered the JEA_Demo2 endpoint, you did so by referencing a
configuration file that assigned the Maintenance role to the CONTOSO\BenSmith
user. When a user connects to a JEA endpoint, PowerShell looks at the session
configuration (.pssc) file to determine which roles are associated with the
connecting user. PowerShell then looks up their role capabilities by name, where
the name of each role assigned to them is compared to the names of .psrc files
inside RoleCapabilities subfolders in modules that are discoverable. If a
matching role capability file is found, PowerShell adds the additional commands
and other settings it defines to the JEA session before the user starts using
it. This just-in-time approach to JEA session creation, combined with the
separation of role capabilities from session configuration information, allows
you to modify role capabilities without having to re-create the JEA endpoints
that use them.

#### :camera: SCREENSHOT

>LODSProperties
>* Uri = screens/show-the-demomodule-file-structure.png
>* ShowAutomatically = No

---

### Open the Maintenance.psrc file

Run the command on **line 49**. A new tab opens in the script pane.

#### :camera: SCREENSHOT

>LODSProperties
>* Uri = screens/open-the-maintenancepsrc-file.png
>* ShowAutomatically = No

---

### Review the file contents

Review the contents of the **Maintenance.psrc** file.

#### :bulb: KNOWLEDGE

JEA endpoints are PowerShell Remoting endpoints that are configured to restrict
the commands that are available to a user or group when they connect to that
endpoint. The command restrictions are defined inside a role capability (.psrc)
file, and are included in PowerShell modules for easy distribution and
discovery. Role capability files are then associated with users and groups in
PowerShell session configuration-a fancy term for PowerShell endpoint-files that
define what a PowerShell endpoint supports. This combination of PowerShell
session configuration files and role capability files provide the backbone that
makes JEA work.

Much like session configuration files, role capability files are a lot like
module manifests. They contain a set of key-value pairs that define the modules,
assemblies, scripts, etc. that should be loaded when this role is used as well
as the commands that are whitelisted for a user who is assigned to this role.

#### :camera: SCREENSHOT

>LODSProperties
>* Uri = screens/review-the-file-contents-2.png
>* ShowAutomatically = No

---

### Modify the VisibleExternalCommands value

Uncomment the **VisibleExternalCommands** field on **line 31**, and then replace
the field value with **'C:\Windows\System32\ipconfig.exe'**.

#### :bulb: KNOWLEDGE

The VisibleExternalCommands field can be used to expose executable programs as
well as PowerShell scripts. It is very important to always provide the full path
to external commands to ensure a similarly named (and potentially malicious)
program placed in the user's path does not get executed instead.

Note that executable programs often include both read and write capabilities by
using their many command-line arguments. Due to the broad scope of executables
with many command-line arguments, making individual cmdlets visible where
read-only capabilities are separate from capabilities that affect change is
preferred over making executable programs visible.

#### :camera: SCREENSHOT

>LODSProperties
>* Uri = screens/modify-the-visibleexternalcommands-value.png
>* ShowAutomatically = No

#### :calling: COMMAND TypeText

```Text
'C:\Windows\System32\ipconfig.exe'
```

---

### Modify the VisibleCmdlets value

Select the entire **line 25** with the VisibleCmdlets field, and then click the
**Type Text** button to the right of this message.

#### :bulb: KNOWLEDGE

This modification demonstrates a few interesting examples that show how you can
expose and limit the capabilities of commands. In the original version of this
file, the only non-default visible cmdlet was Restart-Service. With these
modifications, Restart-Computer and all of the Get cmdlets in the NetTCPIP
module will be added to the list of commands made visible by this role. These
modifications also restrict what can be done with Restart-Service, limiting its
capabilities to the Spooler service.
 
When making commands visible to a JEA role by using a wildcard string, you are
strongly encouraged to examine closely every command that will match that
wildcard character to ensure you don't unintentionally make commands visible.

#### :camera: SCREENSHOT

>LODSProperties
>* Uri = screens/modify-the-visiblecmdlets-value.png
>* ShowAutomatically = No

#### :calling: COMMAND TypeText

```Text
VisibleCmdlets = 'Restart-Computer',
                 @{
                     Name = 'Restart-Service'
                     Parameters = @{ Name = 'Name'; ValidateSet = 'Spooler' }
                 },
                 'NetTCPIP\Get-*'
```

---

### Save the file

Press **Ctrl+S** to save the **Maintenance.psrc** file.

#### :camera: SCREENSHOT

>LODSProperties
>* Uri = screens/save-the-file.png
>* ShowAutomatically = No

---

### Close the Maintenance.psrc file

Close the **Maintenance.psrc** file.

---

### Connect to JEA_Demo2

In the **2-JEACreateAndManage.ps1** script, run the command on **line 52**.

#### :bulb: KNOWLEDGE

You may see a failed to refresh warning message. You can safely ignore this
message.

#### :camera: SCREENSHOT

>LODSProperties
>* Uri = screens/connect-to-jeademo2.png
>* ShowAutomatically = No

---

### List the endpoint commands

Run the command on **line 55**.

#### :bulb: KNOWLEDGE

Since you modified the Maintenance.psrc file, you should see many additional
commands in this command list. These come from the addition of the ipconfig
executable program, the Restart-Computer cmdlet, and all of the Get commands in
the NetTCPIP module.

#### :camera: SCREENSHOT

>LODSProperties
>* Uri = screens/list-the-endpoint-commands-3.png
>* ShowAutomatically = No

---

### Restart the Spooler service

Run the command on **line 58**.

#### :bulb: KNOWLEDGE

This works as expected because the Spooler service name is in the whitelist of
names allowed by the Restart-Service cmdlet in this role.

#### :camera: SCREENSHOT

>LODSProperties
>* Uri = screens/restart-the-spooler-service.png
>* ShowAutomatically = No

---

### Restart the WSearch service

Run the command on **line 61**.

#### :bulb: KNOWLEDGE

In the original version of Maintenance.psrc, the Restart-Service cmdlet was
added without any restrictions. In this exercise, you added a restriction to the
Restart-Service cmdlet so that it will only work for the spooler service. As a
result, this command fails as expected.

#### :camera: SCREENSHOT

>LODSProperties
>* Uri = screens/restart-the-wsearch-service.png
>* ShowAutomatically = No

---

### Invoke ipconfig

Run the command on **line 64**.

#### :camera: SCREENSHOT

>LODSProperties
>* Uri = screens/invoke-ipconfig.png
>* ShowAutomatically = No

---

### Confirm that you can restart the computer

Run the command on **line 67**.

#### :camera: SCREENSHOT

>LODSProperties
>* Uri = screens/confirm-that-you-can-restart-the-computer.png
>* ShowAutomatically = No

---

### Disconnect from the endpoint

Run the command on **line 70**.

---

### Close the Windows PowerShell ISE window

On the File menu, click **Exit**.

* * *

# Working with the user drive in a JEA endpoint

>LODSProperties
>* IntroductionUri = https://lodmanuals.blob.core.windows.net/manuals/Ignite 2016/Videos/IDL4002_new content/Working with the User Drive.mp4

## INTRODUCTION MESSAGE

In this exercise, you will create a new JEA endpoint that mounts a user drive.
You will then connect to that endpoint and invoke commands that let you interact
with the user drive.

## COMPLETION MESSAGE

Congratulations! You now know how to leverage the user drive in your own JEA
endpoints. Click Continue to move to the next exercise.

---

### Open an elevated Windows PowerShell ISE window

On the taskbar, right-click **Windows PowerShell**, and then click **Run ISE as
Administrator**. Click **Yes** when prompted by UAC.

---

### Open the PowerShell script

On the FIle menu, click **Open**. Browse to
**C:\JEA\Exercises\3a-JEASetupEndpointWithUserDrive.ps1**, and then click
**Open**.

#### :camera: SCREENSHOT

>LODSProperties
>* Uri = screens/open-the-powershell-script-3.png
>* ShowAutomatically = No

---

### Review the script contents

Review the contents of the **3a-JEASetupEndpointWithUserDrive.ps1** file.

#### :bulb: KNOWLEDGE

This script file will create a new JEA endpoint called JEA_UserDrive_Demo. The
creation of this endpoint is broken down into four main parts:

1. Lines 6-22 create an empty Support_Demo module that is discoverable by all
users.
1. Lines 28-48 create a role capability file inside of the Support_Demo module.
The role capability file defines a Get-UserDriveLocation function (lines 39-40)
and a New-ProcessReport function (lines 43-44). These two functions work
directly with the user drive.
1. Lines 54-85 create a new JEA endpoint configuration file that will mount the
user drive for any user who connects to an endpoint registered with this
configuration file.
1. Line 92 registers the JEA_UserDrive_Demo endpoint on the system.

When the MountUserDrive field is set to true in a session configuration file
used to register a JEA endpoint, as it will be in this case (see line 77),
PowerShell will create a constrained, user-specific space in the file system
whenever a user connects to that endpoint. That space is known as the user
drive.

The user drive allows files to be created in a JEA endpoint in a location that
is accessible to the connected user. It also allows files to be copied into or
out of a JEA endpoint without having to expose other parts of the file system to
end users who use that endpoint. By default, it is limited to 50MB per user, but
that setting may be changed in the session configuration file.

#### :camera: SCREENSHOT

>LODSProperties
>* Uri = screens/review-the-script-contents.png
>* ShowAutomatically = No

---

### Run the script

On the toolbar, click **Run Script** (green arrow). When prompted, click **Run
once**.

#### :camera: SCREENSHOT

>LODSProperties
>* Uri = screens/run-the-script.png
>* ShowAutomatically = No

---

### Close the file

Close the **3a-JEASetupEndpointWithUserDrive.ps1** script file.

---

### Open the PowerShell script

On the File menu, click **Open**. Browse to
**C:\JEA\Exercises\3b-JEAWorkingWithUserDrive.ps1**, and then click **Open**.

#### :camera: SCREENSHOT

>LODSProperties
>* Uri = screens/open-the-powershell-script-4.png
>* ShowAutomatically = No

---

### Read the script description

Read the comments at the top of the **3b-JEAWorkingWithUserDrive.ps1** file.

#### :camera: SCREENSHOT

>LODSProperties
>* Uri = screens/read-the-script-description-3.png
>* ShowAutomatically = No

---

### Store non-admin credentials

Run the command on **line 20**. When prompted, enter **Passw0rd!** as the
password.

---

### Create a remoting session

Run the command on **line 23**.

#### :bulb: KNOWLEDGE

Unlike the earlier exercises in which you used Enter-PSSession to invoke
interactive commands from inside of a JEA session, in this exercise, you will
create a new PowerShell remoting session and connect it to the
JEA_UserDrive_Demo endpoint as CONTOSO\BenSmith. Once you have a remoting
session stored in a variable, you can then use that session in multiple remoting
commands.

Having a remoting session in a variable is useful in a number of scenarios.

- Capturing data received from a JEA endpoint directly from a command
invocation-for example, storing the results of an Invoke-Command invocation in a
variable.
- Copying items to or from the user drive-for example, Copy-Item.
- Using the pipeline to send data into or process data coming out of a JEA
endpoint-for example, Invoke-Command.

The rest of this exercise will focus on the second scenario in the list.

It is important to note that the folder to which the user drive is mapped
persists beyond JEA sessions. This means that if you disconnect from a JEA
endpoint and then reconnect to the same endpoint again later, the files in your
user drive will still be there.

---

### Get the user drive location

Run the command on **line 26**.

#### :bulb: KNOWLEDGE

The Invoke-Command cmdlet is very useful for JEA. It allows you to store output
from a JEA command in a variable. In this case, you store the location of the
user drive that is retrieved by using the Get-UserDriveLocation command that is
defined in the JEA endpoint in a variable so that you can use it later.

Normally, you would not expose the path to which the user drive is mapped to
non-admin JEA users. You're simply doing it here to learn how it works.

---

### Generate a new process report

Run the command on **line 29**.

#### :bulb: KNOWLEDGE

There are many scenarios where it may be useful for you to use the user drive.
One scenario is when you want to generate a file the same way every time a
specific JEA command is run, regardless of the user who runs it. Another
scenario is when you have a command that requires a path to a data file to run
(.csv, .txt, etc.). To satisfy scenarios like these, you can set up your JEA
endpoint such that the commands it exposes to users internally leverage the user
drive as needed.

In this task, you run a command that is an example of the first scenario
presented. The New-ProcessReport command generates a report in the user drive on
the remote system.

---

### Copy the report locally

Run the command on **line 32**.

#### :bulb: KNOWLEDGE

The Copy-Item command has two new parameters that facilitate copying items out
of or into a JEA session: -FromSession and -ToSession. These two parameters are
mutually exclusive and cannot be used in the same invocation of Copy-Item. With
the addition of these new parameters, copying files into or out of a JEA
endpoint is as easy as copying files on your local computer.

#### :camera: SCREENSHOT

>LODSProperties
>* Uri = screens/copy-the-report-locally.png
>* ShowAutomatically = No

---

### Open the report

Run the command on **line 35**.

#### :camera: SCREENSHOT

>LODSProperties
>* Uri = screens/open-the-report.png
>* ShowAutomatically = No

---

### Close the report

Close the **ProcessReport.html** file.

---

### Show the user drive root folder contents

Run the command on **line 38**.

#### :bulb: KNOWLEDGE

When JEA users are working with the user drive, they will always reference a
path starting with User. Behind the scenes, the user drive is mapped to a
specific location in the file system on the computer where the JEA endpoint is
registered. You retrieved that location by running the command on line 26
earlier in this exercise and stored it in the $userDriveLocation variable. This
command shows you the contents of that folder.

#### :camera: SCREENSHOT

>LODSProperties
>* Uri = screens/show-the-user-drive-root-folder-contents.png
>* ShowAutomatically = No

---

### Close the remoting session

Run the command on **line 41**.

#### :bulb: KNOWLEDGE

When you are finished with a session you opened by using New-PSSession, you
should always close it by using Remove-PSSession.

---

### Verify the user drive root folder still exists

Run the command on **line 44**.

#### :bulb: KNOWLEDGE

Unlike a virtual account which only exists as long as a user is connected to a
JEA endpoint, the folder to which the user drive is mapped for a user persists
across JEA sessions.

#### :camera: SCREENSHOT

>LODSProperties
>* Uri = screens/verify-the-user-drive-root-folder-still-exists.png
>* ShowAutomatically = No

---

### Close the Windows PowerShell ISE window

On the File menu, click **Exit**.

* * *

# Reporting on JEA

>LODSProperties
>* IntroductionUri = https://lodmanuals.blob.core.windows.net/manuals/Ignite 2016/Videos/IDL4002_new content/Reporting on JEA.mp4

## INTRODUCTION MESSAGE

Because JEA allows non-privileged users to run in a privileged context, logging
and auditing are extremely important. In this section, you will learn about the
tools that you can use to help you with logging and auditing.

## COMPLETION MESSAGE

Congratulations! You have now learned how to perform logging and auditing with
JEA. Click Continue to advance to the next exercise.

---

### Open an elevated Windows PowerShell ISE window

On the taskbar, right-click **Windows PowerShell**, and then click **Run ISE as
Administrator**. Click **Yes** when prompted by UAC.

#### :bulb: KNOWLEDGE

Reporting on JEA endpoint configuration, role capabilities, and event log data
requires elevation. Viewing JEA transcript files may require elevation if you
configure your file system security accordingly.

---

### Open the PowerShell script

On the File menu, click **Open**. Browse to
**C:\JEA\Exercises\4-JEAReporting.ps1**, and then click **Open**.

#### :camera: SCREENSHOT

>LODSProperties
>* Uri = screens/open-the-powershell-script-5.png
>* ShowAutomatically = No

---

### Read the script description

Read the comments at the top of the **4-JEAReporting.ps1** file.

#### :camera: SCREENSHOT

>LODSProperties
>* Uri = screens/read-the-script-description-4.png
>* ShowAutomatically = No

---

### List all JEA endpoints

Run the command on **line 14**.

#### :bulb: KNOWLEDGE

You previously used the Get-PSSessionConfiguration cmdlet to list all PowerShell
Remoting endpoints. This includes JEA endpoints. By applying a client-side
filter with the Where-Object cmdlet, you can automatically filter that list to
show only the JEA endpoints that are on the local machine.

#### :camera: SCREENSHOT

>LODSProperties
>* Uri = screens/list-all-jea-endpoints.png
>* ShowAutomatically = No

---

### List the endpoint commands for a specific user

Run the command on **line 17**.

#### :bulb: KNOWLEDGE

As you create JEA endpoints and assign roles to users or groups, it is important
to verify that individual users have access to the exact set of commands that
you expect them to have inside of the JEA endpoint, and nothing more. This is
also something that you may need to audit on an ongoing basis. You typically
won't have a user's password, so you need another way to verify the commands to
which users have access inside of a JEA endpoint.

The Get-PSSessionCapability cmdlet allows you to retrieve a list of commands to
which specific users will have access when they connect to the JEA endpoint that
you identify so that you can properly audit and report on this information.

#### :camera: SCREENSHOT

>LODSProperties
>* Uri = screens/list-the-endpoint-commands-for-a-specific-user.png
>* ShowAutomatically = No

---

### View the JEA session transcripts

Run the command on **line 20**. In the File Explorer window that opens, open the
most recent transcript file, review the contents, and then close the file as
well as File Explorer.

#### :bulb: KNOWLEDGE

When you register a JEA endpoint with the New-PSSessionConfigurationFile cmdlet,
you can optionally specify a transcript directory. The directory you view here
was used in the initial setup of the JEA_Demo JEA endpoint, as well as during
the creation of the JEA_Demo2 JEA Endpoint in exercise 2.

Transcripts allow you to "look over the shoulder" of a person using a JEA
endpoint. One transcript is created for each JEA session, and all actions taken
in that session will be recorded. JEA records information about the connected
user, the RunAs user, the commands run during the session, the output from those
commands, and more.

#### :camera: SCREENSHOT

>LODSProperties
>* Uri = screens/view-the-jea-session-transcripts.png
>* ShowAutomatically = No

---

### Review the PowerShell event log entries

Run the command on **line 23**. Review the contents of the GridView, and then
close it.

#### :bulb: KNOWLEDGE

In addition to transcription, you can also turn on module logging for Windows
PowerShell. Module logging was turned on for JEA-SRV01 during the setup of this
lab. When you have module logging turned on, all PowerShell actions are recorded
in regular Windows event logs. The log entries that are recorded are a little
more challenging to deal with when compared to transcripts, but the level of
detail they give you can be useful.

In the PowerShell operational log, an entry with the event ID 4104 will be added
to the log for each command invoked when module logging is enabled. The command
you invoke in this task retrieves all of entries with event ID 4104 from the
PowerShell operational log and displays them in a grid for review.

#### :camera: SCREENSHOT

>LODSProperties
>* Uri = screens/review-the-powershell-event-log-entries.png
>* ShowAutomatically = No

---

### Close the Windows PowerShell ISE window

On the File menu, click **Exit**.

* * *

# Deployment and maintenance with DSC

## INTRODUCTION MESSAGE

In this exercise, you will deploy and test a new JEA endpoint to a remote system
using PowerShell Desired State Configuration (DSC).

## COMPLETION MESSAGE

Congratulations! You have now completed the fifth and final exercise in this
lab. You can continue learning more about JEA by visiting the newly-updated JEA
section on MSDN at https://msdn.microsoft.com/powershell/jea/readme, or by
monitoring the conversation on the JEA project page on GitHub at
https://github.com/PowerShell/JEA.

---

### Open an elevated Windows PowerShell ISE window

On the taskbar, right-click **Windows PowerShell**, and then click **Run ISE as
Administrator**. Click **Yes** when prompted by UAC.

#### :bulb: KNOWLEDGE

Deploying JEA endpoints to remote systems with PowerShell Desired State
Configuration (DSC) requires elevation.

---

### Open the PowerShell script

On the File menu, click **Open**. Browse to
**C:\JEA\Exercises\5-JEADeployWithDSC.ps1**, and then click **Open**.

---

### Read the script description

Read the comments at the top of the **5-JEADeployWithDSC.ps1** file.

#### :bulb: KNOWLEDGE

Support for deploying JEA endpoints by using DSC has recently become available.
The DSC Resource module that is used to deploy JEA endpoints is a new feature
and still undergoing bug fixes. It is important to keep that in mind as you
start working with JEA and DSC.

#### :camera: Screenshot

>LODSProperties
>* Uri = screens/read-the-script-description-5.png
>* ShowAutomatically = No

---

### Define a sample JEA configuration

Select **lines 20-51**, and then on the toolbar, click **Run Selection** (green
arrow on page).

#### :bulb: KNOWLEDGE

Lines 20-51 in the 5-JEADeployWithDSC.ps1 file define the configuration that
will be used to deploy JEA to remote systems in the current PowerShell session.

The deployment configuration is defined in two steps.

1. Copy a role capability file from a UNC share to the target server where the
JEA endpoint is being deployed (see lines 34-41).
1. Create the JEA endpoint on that remote system, assigning the role
capabilities to a user and using a user drive (see lines 43-49). This step will
not start until the first step has completed successfully.

#### :camera: SCREENSHOT

>LODSProperties
>* Uri = screens/define-a-sample-jea-configuration.png
>* ShowAutomatically = No

---

### Bypass some security checks

Select **lines 54-62**, and then on the toolbar, click **Run Selection** (green
arrow on page).

#### :bulb: KNOWLEDGE

To simplify this lab, you will not use all of the security features that are
available in PowerShell DSC. Lines 54-62 instruct PowerShell DSC to allow a
plain text password and to allow a domain user to be used for the deployment.
In production environments, you should not allow plain text passwords nor should
you allow domain users to be used for deployments unless necessary.

#### :camera: SCREENSHOT

>LODSProperties
>* Uri = screens/bypass-some-security-checks.png
>* ShowAutomatically = No

---

### Store admin credentials

Run the command on **line 67**. When prompted, enter **Passw0rd!** as the
password.

---

### Generate a MOF file for deployment to srv02

Run the command on **line 70**.

#### :bulb: KNOWLEDGE

When you invoke a DSC configuration, a MOF file is generated that can be used to
push the deployment to a remote system or to pull the deployment onto a remote
system. For more information about DSC and push vs. pull servers, please consult
the DSC documentation.

The MOF file that is generated will be given a name that matches the name of the
node (computer) to which it will be applied, and it will be stored in a
subfolder of the current folder that has the same name as the configuration that
you are invoking. For example, in this exercise, the MOF file that is generated
by this command will be created as .\SampleJeaConfig\srv02.mof. To keep your MOF
files organized, as a best practice, you should create a folder on your system
where you will store them and run your DSC configurations from that folder so
that they are all kept in the same place.

#### :camera: SCREENSHOT

>LODSProperties
>* Uri = screens/generate-a-mof-file-for-deployment-to-srv02.png
>* ShowAutomatically = No

---

### Push the MOF file to a remote server

Run the command on **line 73**.

#### :warning: ALERT

This command will generate an error when the remote WinRM Service is restarted
after the JEA Endpoint is registered. This error can be safely ignored.

#### :bulb: KNOWLEDGE

The Start-DscConfiguration cmdlet pushes a MOF file to a remote server for
processing by its local configuration manager (LCM). When you use this cmdlet,
it is highly recommended that you run it with Verbose so that you can see
everything that is going on and be in a better position to troubleshoot issues
if you run into any.

In this task, you are simply pushing the MOF file you created in the previous
task to the remote server so that the LCM on that server can comply with the MOF
configuration instructions. Since the MOF file contains instructions to create a
JEA endpoint, once this command is finished you will have a new JEA endpoint to
which you can connect.

#### :camera: SCREENSHOT

>LODSProperties
>* Uri = screens/push-the-mof-file-to-a-remote-server.png
>* ShowAutomatically = No

---

### Store non-admin credentials

Run the command on **line 77**. When prompted, enter **Passw0rd!** as the
password.

---

### Enter a session inside the remote JEA endpoint

Run the command on **line 80**.

#### :bulb: KNOWLEDGE

In earlier exercises, you were working with local endpoints, running as if they
were remote. In this command, you're actually connecting to a JEA endpoint that
is running in a remote endpoint. The experience and capabilities are the same as
you saw during previous exercises, but this time you're truly working with a
remote system.

---

### List connection information from the endpoint

Run the command on **line 83**.

#### :bulb: KNOWLEDGE

Much like in the first exercise, this command will output some connection
information from the breakpoint. When remotely managing multiple systems, you
can also use this information to identify which system you are connected to.

#### :camera: SCREENSHOT

>LODSProperties
>* Uri = screens/list-connection-information-from-the-endpoint.png
>* ShowAutomatically = No

---

### Exit the remoting session

Run the command on **line 86**.

---

### End the lab

Click **Done** to finalize and close the lab.
