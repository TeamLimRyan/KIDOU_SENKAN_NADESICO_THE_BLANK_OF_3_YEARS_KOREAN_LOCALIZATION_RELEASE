# 설치 안내

## 1. 준비물

- 지원되는 일본판 원본 BIN/CUE 2디스크 세트
- Windows PowerShell 5.1 또는 PowerShell 7
- xdelta3 3.2.0 또는 호환 버전
- 약 1.1GB 이상의 빈 출력 공간

xdelta3는 [공식 프로젝트](https://github.com/jmacd/xdelta)에서 받을 수 있습니다. 릴리스 ZIP에는 실행 파일을 포함하지 않습니다.

## 2. 원본 폴더 구성

다음 6개 파일을 같은 폴더에 둡니다. 파일명은 바꾸지 마세요.

```text
Kidou Senkan Nadesico - The Blank of 3 Years (Japan) (Disc 1) (Track 1).bin
Kidou Senkan Nadesico - The Blank of 3 Years (Japan) (Disc 1) (Track 2).bin
Kidou Senkan Nadesico - The Blank of 3 Years (Japan) (Disc 1).cue
Kidou Senkan Nadesico - The Blank of 3 Years (Japan) (Disc 2) (Track 1).bin
Kidou Senkan Nadesico - The Blank of 3 Years (Japan) (Disc 2) (Track 2).bin
Kidou Senkan Nadesico - The Blank of 3 Years (Japan) (Disc 2).cue
```

## 3. 패치 적용

릴리스 ZIP을 푼 폴더에서 PowerShell을 열고 실행합니다.

```powershell
.\apply_patch.ps1 `
  -SourceDir '원본 BIN-CUE 폴더' `
  -OutputDir '새 한글판 출력 폴더' `
  -Xdelta3 'xdelta3.exe 전체 경로'
```

Windows 실행 정책으로 스크립트가 차단되면 다음처럼 실행합니다.

```powershell
powershell -ExecutionPolicy Bypass -File .\apply_patch.ps1 `
  -SourceDir '원본 BIN-CUE 폴더' `
  -OutputDir '새 한글판 출력 폴더' `
  -Xdelta3 'xdelta3.exe 전체 경로'
```

스크립트는 다음 순서로 안전하게 처리합니다.

1. 원본 6개 파일의 SHA-256 검사
2. 디스크 1·2 데이터 트랙에 xdelta3 패치 적용
3. CDDA 트랙과 CUE를 바이트 그대로 출력 폴더에 복사
4. 출력 6개 파일의 SHA-256 검사

원본 폴더는 수정하지 않습니다. 출력 폴더는 원본과 달라야 하며, 없거나 비어 있어야 합니다.

## 4. 실행

출력 폴더의 `...(Disc 1).cue`를 에뮬레이터에서 불러옵니다. Track 1 BIN을 직접 불러오면 CD 오디오가 재생되지 않을 수 있으므로 반드시 CUE를 사용하세요.

게임이 디스크 교체를 요구하면 에뮬레이터의 디스크 교체 기능으로 `...(Disc 2).cue`를 선택합니다. 디스크 교체 중에는 게임을 재설정하지 마세요.

## 5. 다운로드 검증

릴리스에 함께 제공되는 `NADESICO_TBO3Y_KO_v1.0.0.zip.sha256`의 값과 ZIP 파일의 SHA-256을 비교할 수 있습니다.

```powershell
Get-FileHash .\NADESICO_TBO3Y_KO_v1.0.0.zip -Algorithm SHA256
```
