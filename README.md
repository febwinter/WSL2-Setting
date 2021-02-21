# WSL2-Setting
WSL2 (Window Subsystem Linux) 세팅 및 설정



## 1. Linux용 Windows 하위 시스템 사용 설정

- #### powershell 관리자 권한 실행(WSL 1)

```powershell
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
```

위 단계는 WSL 1을 설치하는 과정으로 WSL 2를 설치할 경우 아래 요구사항을 확인해야 함

- #### WSL 2 요구사항
  - x64기준 **윈도우 버전 1903, 빌드 18362 이상**
  - ARM64 기준 **윈도우 버전 2004, 빌드 19041 이상**
  - 위 버전보다 낮을경우 WSL2를 지원하지 않음



## 2. Virtual Machine 플랫폼 옵션 기능 활성화

- #### PowerShell 관리자 권한 실행

```powershell
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
```

Virtual Machine 플랫폼 옵션 기능을 사용하도록 설정한것

- #### 시스템 재시작



## 3. 커널 업데이트 패키지 설치(WSL 2 only)

- #### 업데이트 패키지 다운로드 [링크](https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_x64.msi)

- #### 관리자 권한으로 실행 및 설치

WSL 1 버전은 Linux의 System Call을 Window API로 변환하는 구조를 취하고 있었으나 WSL 2로 업데이트되며 윈도우즈에 리눅스 커널을 올리는 형태로 변화되었다. 따라서 WSL2는 Full Linux 커널이며 Linux API를 지원한다. 직접 리눅스 커널을 탑재하여 기존의 변환 과정을 거치지 않아 속도적 이점을 얻게 되었다.

본 단계는 WSL 2를 위해 필요한 부분이며 WSL 1만을 사용하는 경우 필요 없는 단계이다.



## 4. WSL1을 WSL 2 버전으로 변경

- #### PowerShell 관리자 권한 실행

```powershell
wsl --set-default-version 2
```



## 5. MS Store를 통한 Linux 배포판 설치

[MS Store](https://aka.ms/wslstore)을 통해 각종 배포판을 설치할 수 있다.



## 6. WSL 버전 확인 및 버전 설정

```powershell
wsl --list --verbose
  NAME                   STATE           VERSION
* Ubuntu                 Running         1
```

PowerShell 혹은 CMD 상에서 위 명령어를 입력시 설치된 리눅스 배포판과 버전이 나타난다.

```
wsl --set-version <distribution name> <versionNumber>
wsl --set-default-version 2
```

위의 명령어와 같이 배포판관 버전을 설정해주어 변경한다.

```powershell
  NAME                   STATE           VERSION
* Ubuntu                 Running         2
```

변경되면 다시 명령어를 입력했을 때 다음과 같이 나타난다.



## 7. WSL 종료 방법

WSL을 실행시키게 되면 창을 끄더라도 따로 종료시키지 않는 한 계속해서 실행되어 있는다.

종료시 다음과 같은 명령어를 사용해 종료가 가능하다.

```powershell
wsl -t Ubuntu
```

위 명령어에서 'Ubuntu' 대신 배포판 이름에 해당하는 문자열을 넣어 실행시키면 종료되며 확인시 다음과 같이 나타난다.

```powershell
  NAME                   STATE           VERSION
* Ubuntu                 Stopped         2
```