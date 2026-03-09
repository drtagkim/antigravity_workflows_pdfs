---
description: Markdown 문서를 PDF 파일로 변환 (Python 기반)
---
# 마크다운을 PDF로 변환 (md2pdf)

이 워크플로우는 사용자가 지정한 마크다운(`.md`) 파일을 읽고, 파이썬(Python) 스크립트를 동적으로 실행하여 깔끔하게 포맷팅된 `.pdf` 파일로 변환 및 저장하는 프로세스입니다. 

기본적으로 `markdown` 라이브러리로 HTML을 생성하고, `weasyprint` 라이브러리로 PDF를 렌더링하는 방식을 사용합니다.

## 1. 대상 파일 및 경로 확인
- 사용자가 변환하고자 하는 타겟 마크다운 파일(예: `주요추진내용.md`)의 절대 경로를 확인합니다.
- 출력될 PDF 파일의 경로와 이름(예: `주요추진내용_보고서.pdf`)을 확정합니다.

## 2. 변환 파이썬 스크립트 작성
- `/tmp/md_to_pdf_converter.py` 경로에 변환 파이썬 스크립트를 `write_to_file` 도구를 사용하여 생성합니다.
- **파이썬 스크립트 필수 포함 내용**:
  - `markdown` 모듈을 통한 텍스트 변환 (UTF-8 인코딩 주의)
  - `weasyprint` 모듈을 사용한 HTML -> PDF 렌더링
  - (선택) 한글 폰트 깨짐 방지를 위해 HTML 헤더에 기본 폰트 명시 (예: `<style>body { font-family: 'AppleGothic', 'Malgun Gothic', sans-serif; }</style>`)

## 3. 스크립트 실행 및 PDF 생성
- `run_command` 도구를 사용하여 필요한 Python 패키지를 설치하고 스크립트를 실행합니다.
  
```bash
# 필요한 패키지 조용히 설치
pip install --quiet markdown weasyprint

# 생성한 임시 파이썬 스크립트 실행
python3 /tmp/md_to_pdf_converter.py
```

## 4. 완료 및 파일 경로 보고
- 변환된 `.pdf` 파일이 지정된 폴더에 정상적으로 생성되었는지 확인합니다.
- 사용자(교수님)에게 변환 완료 소식을 알리고, 최종 PDF 파일의 절대 경로를 가독성 좋게 브리핑합니다.
