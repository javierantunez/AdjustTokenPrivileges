# AdjustTokenPrivileges
Adjusts the privileges of the token for a given proccess

QUICK and dirty POC based on Fashion Proof's (Mark Mo) https://github.com/fashionproof/EnableAllTokenPrivs/blob/master/EnableAllTokenPrivs.ps1
In some cases you land in a high integrity proccess, but the token have only some privileges enabled for that proccess. 
This program permits enable all privileges in the token, for a given PID.
We used it in the context of Covenant C2 operations, so we tweaked the code to adjust the privileges inside the covenant process.

You must note that depending on how the covenant grunt was deployed, you will need to provide different PID (to be confirmed):
* For Powershell launched grunts: Actual powershell process PID
* For binary grunts: The Parent Process PID.
* For injected grunts: The injected Process PID (remember that must be high integrity process)

You can check the actual pid using powershell:
$pid

Or view all proccesses PIDs with 
Get-Process

To invoke the prorgram you need to pass the PID of the process to be adjusted as parameter.

Example:
$pid
1234

AdjustTokenprivileges.exe 1234


IMPORTANT NOTE: Adjusting the token enabling all privileges is NOT OPSEC safe. Adjust the code to the purposes of your specific use case.