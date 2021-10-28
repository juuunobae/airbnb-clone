# Django
- 거대한 프레임워크이고, 많은 유틸리티들이 구현되어 있다.
- 이미 구현되어있는 기능을 간단하게 사용가능하다.
- 관리자 페이지 사용자 인증 등
- 이미 만들어져 있는 기능을 사용해 개발 시간을 줄일 수 있다.
- 하지만, 이미 있는 기능을 제공하기 때문에 원하는데로 커스텀이 하기가 힘들다.

# Flask
- 짧은 시간에 간결한 코드로 서버를 만들 수 있다.
- 거의 모든 것을 직접 만들어서 사용해야 한다.

# Django Template
- 사용자간 상호작용이 많으면 React나 다른 프레임워크가 용이하겠지만, 콘텐츠 위주인 경우에는 django template도 사용할만 하다.

# pipenv
- python을 설치하며 pip가 딸려오는데, npm 역할을 하고 모든 것을 전역적으로 설치한다.
- 패키지를 해당 프로젝트에만 설치하기 위해 pipenv를 사용한다.
- `brew install pipenv` 설치 명령어
- 설치하면 생성되는 pipfile은 package.json과 같은 역할을 한다.

# 프로젝트 생성
- 프로젝트 폴더를 만들고 그 폴더 안에서 터미널에 `pipenv --three` 명령어 실행
  - pipenv --three: python3을 사용할 것이라고 명시하는 것
- `pipenv shell` 명령어를 이용해 개발환경으로 들어간다.
- `pipenv install django==[version]`으로 장고 설치