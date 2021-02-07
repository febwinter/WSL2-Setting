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

