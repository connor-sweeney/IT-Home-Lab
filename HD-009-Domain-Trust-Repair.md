
# HD-009: Active Directory Domain Trust Repair

## Lab Environment
- Hypervisor: VirtualBox
- Server: Windows Server 2022
- Client: Windows 11 Pro
- Domain: connorlab.local

## Problem
User Marcus Johnson could not sign in to the domain.

## Troubleshooting

### 1. Verify Active Directory Account
- Confirmed account was enabled.
- Confirmed account was not locked.
- Confirmed password had not expired.

### 2. Check Domain Trust
Ran the following PowerShell command:

```powershell
Test-ComputerSecureChannel -Verbose
```

**Result:** False

The workstation's secure channel was broken.

### 3. Repair Secure Channel
```powershell
Test-ComputerSecureChannel -Repair -Credential (Get-Credential)
```

**Result:** True

### 4. Verify Resolution
```powershell
Test-ComputerSecureChannel -Verbose
```

**Result:** True

Successfully signed in as the affected domain user
on the lab workstation.

## Lessons Learned
- How domain trust relationships work.
- How to diagnose a broken secure channel.
- How to repair domain trust using PowerShell.
- Why verifying the fix is important.
