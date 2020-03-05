# Robin Changelog

All notable changes to the [Robin project](https://robin-language.org/) will be documented in this file.

The format is based on [Keep a Changelog](http://keepachangelog.com/) and this project adheres to [Semantic Versioning](http://semver.org/).

---

## [0.9.3.5631] - 2020-03-09

### Added Modules
- **Ancora**, connect to Ancora, upload documents and retrieve results.

### Added Actions
- Ancora.Connect
- Ancora.GetBatchTypes
- Ancora.UploadDocument
- Ancora.IsBatchStateSuccessful
- Ancora.GetCapturedData
- Ancora.GetCapturedDataAndExportDocument

### New Features
- New Robin extension add-on for web automation (Google Chrome)
- New Robin extension add-on for web automation (Mozilla Firefox)
- Added ability to extend Robin through its SDK.
- Added Visual Studio templates for VS2017/2019 for Robin extension (project and action templates).
- Code snippets for if statements, switch, foreach, loop etc.
- Autocomplete functionality for enums.

### Modified
- Updated installer to include Visual Studio templates
- **Custom Modules** folder is now created in the Robin root folder during installation.
- Multiline comments are now enabled by **/#** and end by **#/**.
- When hitting Ctrl+Space for options preview, Modules are now presented before keywords in the editor.
- Removed Cognitive.Microsoft.TextAnalytics.DetectLanguage action as it is deprecated and not supported by the API any longer.
- In the editor Categories/Subcategories are now distinct from the Actions (followed by a dot).
- Text.Parse action now returns a list of numeric values instead of a list of text values.
- Filenames of Appmasks now allow for spaces.
- Controls from imported appmasks cannot be saved to variables. The full path of the control must be utilized [appmask name].[app name].[screen name].[control name]

### Fixed Bugs
- Improved functionality of UIAutomation modules regarding Java apps.
- Fixed error in retrieved JSON when utilizing Cognitive.Microsoft.Face.DetectFromSmile.
- Fixed error in retrieved JSON when utilizing Cognitive.Microsoft.Face.DetectFromURL.
- Fixed error handling when redundant 'end' keywords are included in Robin scripts. 
- Fixed exception handling (InvokeCognitiveServiceError) for Cognitive.Google actions.
- Fixed decryption of encrypted variables. Removed redundant square icons produced.
- Fixed error handling for redundant **end** keywords.
- Fixed Excel.ReadCell action's return type.
- Text.Parse action now returns occurrence positions (list of numbers).
- Text.RegexParse action now returns occurrence positions (list of numbers).
- Fixed Module Loader initialization for proper folder identification.
- Fixed MouseAndKeyboard.MoveMouse accuracy issues that occured randomly. 
- Fixed escape character sequence for unified experience.
- Fixed editor UI pop-ups that remained open on focus-lost.
- Multiple calling of same functions is now enabled.
- Fixed UIAutomation.GetWindow action random error occurance.
- Fixed UIAutomation.GetWindowUseTimeout action random error occurance.
- IfFileExists.Overwrite action now overwrites the file (used to append).
- IfFileExists.Append action now appends to the file (used to overwrite).
- Fixed File.WriteCSV and File.WriteCSVWithCustomSeparator actions (they appended text instead of overwriting).
- Fixed File.WriteCSVWithCustomSeparator error throwing when the VariableToWrite argument was a list.
- Fixed UIAutomation.Windows.Focus random error "Window not found".
- Fixed UIAutomation.Click error throwing even when action was executed successfully.

### Known Bugs
- Scripts that utilize appsmask files have to either use the full path of the appmask otherwise the script file has to be closed and re-opened.
- Robin scripts won't execute on Windows Server 2016.
- Robin CLI stops working in Windows 32bit.
- Exchange.RetrieveEmails is not working for Drafts Folder.
- File.WriteCSV and File.WriteCSVWithCustomSeparator miss exception handling.
- .handle property returns HNWD but can't be utilized to manipulate a window.
- Running CommandLine.Read action doesn't return CmdOutput output.
- Running CommandLine.ReadAndSplit action doesn't return CmdOutput output.
- CaptureFast.Connect action is not throwing an error.

---

## [0.9.2.5567] - 2019-12-16

### Added Modules
- **AWS**, connect to Amazon Web Services and automate a variety of tasks.
- **ActiveDirectory**, connect to an Active Directory server and perform operations. 
- **Azure**, connect to Azure Cloud and automate the management of resources like virtual machines, disks, snapshots and resource groups.

### Added Actions

- ActiveDirectory.ConnectToServer
- ActiveDirectory.ConnectToServerWithAuthentication
- ActiveDirectory.CloseConnection
- ActiveDirectory.Group
- ActiveDirectory.Group.GetGroupInfo
- ActiveDirectory.Group.GetGroupMembers
- ActiveDirectory.Group.RenameGroup
- ActiveDirectory.Group.DeleteGroup
- ActiveDirectory.Group.AddUserToGroup
- ActiveDirectory.Group.RemoveUserFromGroup
- ActiveDirectory.Object.CreateObject
- ActiveDirectory.Object.DeleteObject
- ActiveDirectory.Object.MoveObject
- ActiveDirectory.Object.RenameObject
- ActiveDirectory.User.CreateUser
- ActiveDirectory.User.GetUserInfo
- ActiveDirectory.User.EnableUser
- ActiveDirectory.User.DisableUser
- ActiveDirectory.User.RenameUser
- ActiveDirectory.User.DeleteUser
- ActiveDirectory.User.ResetUserPassword
- ActiveDirectory.User.UnlockUser
- ActiveDirectory.User.UpdateUserInfo
- AWS.EC2.CreateEc2SessionWithAccessKeys
- AWS.EC2.CreateEc2SessionWithProfile
- AWS.EC2.EndEC2Session
- AWS.EC2.Volumes.CreateVolume
- AWS.EC2.Volumes.CreateVolumeFromSnapshot
- AWS.EC2.Volumes.AttachVolume
- AWS.EC2.Volumes.DetachVolume
- AWS.EC2.Volumes.DescribeVolumes
- AWS.EC2.Volumes.DeleteVolume
- AWS.EC2.Instances.StartEC2Instance
- AWS.EC2.Instances.StopEC2Instance
- AWS.EC2.Instances.RebootEC2Instance
- AWS.EC2.Instances.GetAvailableEC2Instances
- AWS.EC2.Instances.DescribeEC2Instance
- AWS.EC2.Snapshots.CreateSnapshot
- AWS.EC2.Snapshots.DescribeSnapshots
- AWS.EC2.Snapshots.DeleteSnapshot
- Azure.CreateSessionViaServicePrincipal
- Azure.CreateSessionViaFile
- Azure.CreateSessionViaUser
- Azure.GetSubscriptions
- Azure.EndSession
- Azure.VirtualMachines.GetVirtualMachines
- Azure.VirtualMachines.DescribeVirtualMachine
- Azure.VirtualMachines.StartVirtualMachine
- Azure.VirtualMachines.StopVirtualMachine
- Azure.VirtualMachines.ShutDownVirtualMachine
- Azure.VirtualMachines.RestartVirtualMachine
- Azure.VirtualMachines.Disks.GetDisks
- Azure.VirtualMachines.Disks.AttachManagedDisk
- Azure.VirtualMachines.Disks.AttachUnManagedDisk
- Azure.VirtualMachines.Disks.DetachDisk
- Azure.VirtualMachines.Disks.CreateManagedDisk
- Azure.VirtualMachines.Disks.CreateManagedDiskFromSnapshot
- Azure.VirtualMachines.Disks.CreateManagedDiskFromStorageBlob
- Azure.VirtualMachines.Disks.DeleteDisk
- Azure.VirtualMachines.Snapshots.GetSnapshots
- Azure.VirtualMachines.Snapshots.CreateSnapshot
- Azure.VirtualMachines.Snapshots.DeleteSnapshot
- Azure.ResourceGroups.GetResourceGroups
- Azure.ResourceGroups.CreateResourceGroup
- Azure.ResourceGroups.DeleteResourceGroup

### Modified
- Introduced categories and subcategories for Action grouping in Modules. 
   for example, in **UIAutomation** module, DataExtraction, FormFilling and Windows categories were added.
- Renaming of arguments/enums/values to align with the segregation to the new categories/subcategories.
- Added extra exceptions to some actions for improved exception handling.
- Display.ShowMessageWithTimeout default Timeout value is set to 3 seconds instead of 30.
- Implemented window style for MessageDialog so that it can be customized externally.

### Fixed Bugs
- Fixed assignment by index in nested lists.
- CurrentDateTime.DayOfWeek can now be used in loops.
- Resolved random robot crashes that occurred when commenting out a Console.Write command.
- Resolved random failures of some actions included in the CyberArk module.
- Fixed UISpy attribute updating. Previously some attributes were updated but were not visible in the UISpy editor.
- Variables.ListOfRandomNumbers now generates appropriate values (numeric type).
- Fixed Cognitive.Google.Vision.FaceDetectionFromFile execution. Previously the action didn't execute at random intervals but the script didn't exit with an error code.
- Fixed looping issues that resulted in script termination.

### Known Bugs
- Robin scripts won't execute on Windows Server 2016.
- Robin CLI stops working in Windows 32bit.
- Exchange.RetrieveEmails is not working for Drafts Folder.
- File.WriteCSV and File.WriteCSVWithCustomSeparator append text at the end of the file instead of overwriting.
- The IfFileExists.Overwrite option appends text at the end of the file and the IfFileExists.Append option overwrites the previous text.
- .handle property returns HNWD but can't be utilized to manipulate a window.
- File.WriteCSVWithCustomSeparator throws an error when the VariableToWrite argument is a list.
- UIAutomation.Windows.Focus might throw error "Window not found".
- Running CommandLine.Read action doesn't return CmdOutput output.
- Running CommandLine.ReadAndSplit action doesn't return CmdOutput output.
- CaptureFast.Connect action is not throwing an error.
- UIAutomation.Click error is generated although the action is executed successfully.

---
---