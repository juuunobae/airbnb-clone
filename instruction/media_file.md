# Meida file
- 사용자가 웸에서 업로드한 정적 파일이다.
- 미디어 파일을 업로드하면 프로젝트 폴더의 루트에 저장이 되고 URL이 없다.
- 파일의 경로를 설정해주고 사진을 사용할 수 있도록 URL을 설정해주어야 한다.

> 서버 배포 환경에서는 서버폴더에 저장하지 않는다.</br>
> 개발 환경에서만 연습용이나 테스트용으로 사용

# MEDIA_ROOT
- 미디어 파일의 경로를 설정해주는 것
- `MEDIA_ROOT = os.path.join(BASE_DIR, "uploads")`

## BASE_DIR
- 프로젝트 폴더의 위치를 절대경로로 표시해놓은 것

## os.path.join
- 2개 이상의 path를 합쳐준다.

# MEDIA_URL
- 파일의 URL을 설정해주는 것
- `MEDIA_URL = "/media/"`
  - 절대 경로로 사용하기 위해서는 경로 앞에 /를 넣어준다.
- 사용자가 어떠한 URL로 가면 서버가 어떠한 폴더에 접근을 하게 한다.

# Static file
- 정적인 파일, js, css, image, font 등과 같이 개발자가 사전에 미리 서버에 저장 해둔 파일들을 말한다.

## Static Method
- static 파일의 경로를 등록해준다.
  - `static(settings.MEDIA_URL, documnet_root=settings.MEIDA_ROOT)`
  - `static(파일 URL, 파일 path)`