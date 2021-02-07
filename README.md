# WSL2-Setting
WSL2 (Window Subsystem Linux) 세팅 및 설정



## 1. Linux용 Windows 하위 시스템 사용 설정

- ### powershell 관리자 권한 실행

```powershell
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
```

위 단계는 WSL 1을 설치하는 과정으로 WSL 2를 설치할 경우 아래 과정을 거쳐야 함

- ### WSL2 요구사항

  - x64기준 **윈도우 버전 1903, 빌드 18362 이상**
  - ARM64 기준 **윈도우 버전 2004, 빌드 19041 이상**
  - 위 버전보다 낮을경우 WSL2를 지원하지 않음

