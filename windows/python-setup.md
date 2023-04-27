# Setting up ANY python version on Windows

## Install Desired Python Version
Go to https://www.python.org/ and install your desired version of Python for Windows using the recommended Windows `.exe` installer.

Install for just the current user and DO NOT check the `Add Python to the environment variables` advanced option.

## Setup Environment Variable Manually

Set the `USER` environment variable `CURRENT_PYTHON` to the path pointing to the local user `Python 3.9` root directory:
```powershell
[System.Environment]::SetEnvironmentVariable('CURRENT_PYTHON', `
    'C:\Users\jlvmo\AppData\Local\Programs\Python\Python39', `
    [System.EnvironmentVariableTarget]::User)
```

Append the newly added `CURRENT_PYTHON` environment variable and the `Scripts` directory to the `Path` variable for users:
```powershell
[System.Environment]::SetEnvironmentVariable('Path', `
    [System.Environment]::GetEnvironmentVariable('Path', `
        [System.EnvironmentVariableTarget]::User) + ';%CURRENT_PYTHON%\;%CURRENT_PYTHON%\Scripts', `
    [System.EnvironmentVariableTarget]::User)
```

## Disable Windows Apps Execution Aliases for Python App Installers

Disable the following execution aliases from the Windows `Settings -> Apps -> Advanced app settings -> App execution aliases`

<img width="584" alt="screenshot" src="https://user-images.githubusercontent.com/23618863/234939150-29b397c8-9039-4bbe-b179-f4c903b7706c.png">

## Confirm `python` Command is Working and Using the Correct Path

Check the `python` command:
```powershell
(Get-Command python).Path
```

Check the `pip` command:
```powershell
(Get-Command pip).Path
```
