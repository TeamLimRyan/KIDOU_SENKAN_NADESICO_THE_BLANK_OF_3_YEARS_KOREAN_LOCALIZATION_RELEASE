# 기동전함 나데시코 The blank of 3years 한국어 패치

세가 새턴용 `기동전함 나데시코 The blank of 3years` 일본판 2디스크를 한국어로 즐길 수 있게 하는 비공식 팬 패치입니다.

이 저장소와 릴리스에는 원본 게임의 BIN/CUE, 패치가 적용된 전체 디스크 이미지, BIOS, 세이브 파일이 포함되지 않습니다. 정품에서 직접 준비한 원본 BIN/CUE와 xdelta3가 필요합니다.

## 주요 내용

- 시나리오·선택지·시스템 메시지 한국어화
- 이미지와 오프닝 영상 내 텍스트 현지화
- 흰색 본문, 회색 가장자리, 검은색 외곽선의 한국어 글꼴
- 조합식 한국어 이름 입력
- 타이틀 화면의 불러오기, 저장 슬롯 미리보기, 확인 창, 불러온 뒤 게임 실행 확인
- 디스크 1·2 일괄 패치와 SHA-256 자동 검증

## 설치

1. [Releases](https://github.com/TeamLimRyan/NADESICO_TBO3Y_KO/releases)에서 `NADESICO_TBO3Y_KO_v1.0.0.zip`을 내려받아 압축을 풉니다.
2. 일본판 원본 2디스크를 한 폴더에 BIN/CUE 형식으로 준비합니다.
3. xdelta3 3.2.0 또는 호환 버전을 준비합니다.
4. PowerShell에서 다음 명령을 실행합니다.

```powershell
powershell -ExecutionPolicy Bypass -File .\apply_patch.ps1 `
  -SourceDir 'C:\Games\Nadesico-JP' `
  -OutputDir 'C:\Games\Nadesico-KO' `
  -Xdelta3 'C:\Tools\xdelta3.exe'
```

`PASS: 모든 CUE/BIN 파일의 SHA-256이 검증되었습니다.`가 나오면 출력 폴더의 디스크 1 CUE를 에뮬레이터에서 실행합니다. 게임이 디스크 교체를 요구하면 같은 출력 폴더의 디스크 2 CUE로 교체하세요.

자세한 설명은 [INSTALL.md](INSTALL.md), 오류별 해결 방법은 [TROUBLESHOOTING.md](TROUBLESHOOTING.md)를 참조하세요.

## 지원 원본

파일명과 SHA-256이 모두 일치해야 합니다. 오디오 트랙과 CUE도 적용 스크립트가 자동으로 확인합니다.

| 파일 | SHA-256 |
|---|---|
| Disc 1 Track 1 BIN | `5272944339FD00C976971A9ABFBC342F877E0291EA18D96442A1CC3E5081B6D7` |
| Disc 1 Track 2 BIN | `B18E4C1C55A6E17F678928DD373E347D2337ADF55F6B0C693C7D260B81217982` |
| Disc 1 CUE | `0BE0A912B78FBD0A6F562DE5D8F504A75239F435B2B40C7E8483F3F649688D8A` |
| Disc 2 Track 1 BIN | `32B29EFBCEFD8F2A8D5E5466DE9593184ED42CF926CA521DC80FDE71C0780754` |
| Disc 2 Track 2 BIN | `C6D69BBC9D0F083023F0D8BC7CDD86DDA9C3B6D1A996B92A9687268C6B73E375` |
| Disc 2 CUE | `F9870F5012868B49FF7CF50814EF532E65E882BB313C60A8991A34F2D43B641D` |

## 검증 범위

- 최종 디스크 2회 독립 재빌드 및 바이트 단위 결정성 확인
- CUE 구조, ISO LBA, CDDA, 변경 섹터 EDC/ECC 검사 통과
- 이미지 검수 대상 831개 전부 소유자 판정 완료
- 실제 저장 생성, 콜드 부팅, 불러오기, 시나리오 복귀 확인
- 릴리스 패치 2회 독립 생성 및 fresh-source 복원 확인
- 최종 `apply_patch.ps1` 실행 결과 6개 파일 모두 목표 SHA-256과 일치

모든 분기 파일에는 번역이 반영되어 있지만 12개 자연 루트·엔딩을 각각 처음부터 끝까지 실행하는 전수 검증은 완료하지 않았습니다. 이름 입력의 지원 범위와 원본 유지 이미지 표기는 [RELEASE_NOTES.md](RELEASE_NOTES.md)의 알려진 제한 사항을 확인하세요.

## 크레딧과 권리

[CREDITS.md](CREDITS.md)와 [LEGAL.md](LEGAL.md)를 참조하세요. 이 프로젝트는 원작 권리자와 무관한 비공식 팬 프로젝트이며 상업적 이용을 허용하지 않습니다.
