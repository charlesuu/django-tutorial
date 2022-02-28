# Django로 웹페이지 만들기
![녹화_2022_02_28_18_13_59_481](https://user-images.githubusercontent.com/76809524/155957196-6062abb4-6a4a-49a6-a3e5-f1c75bde793a.gif)
(내가 만든 CRUD)


 생활 코딩의 [ Django Web Framework](https://opentutorials.org/course/4886) 강의를 듣고 CRUD기능이 있는 간단한 웹페이지를 만들어보았다. 웹개발은 완전히 처음이었지만 재미있었다. 백엔드 웹 개발이라는게 이 기초적인 것의 연장이라면, 어쩌면 내가 즐길 수 있는 일이 아닐까하는 생각이 든다. 이 느낌을 간직하고 새로 알게된 지식들을 정리하기 위해서 결과물을 남긴다.


# 배운 내용
## html, 파이썬 정리
Django 학습을 위해서 html과 파이썬 문법을 빠르게 훑어 보았다. 다행히 html문법은 프로그래밍 언어의 문법보다는 훨씬 쉬웠다. 웹 페이지의 구성을 표현하기 위한 최소한의 문법만으로 구성되어있다는 생각이 들었고, 태그의 이름도 직관적인 것이 많아서 사용하기 편했다.

[생활코딩 웹&html 강의](https://opentutorials.org/course/3084)를 통해서 웹의 역사와 기본적인 html태그들에 대해서 공부하고, 태그를 표로 정리해둔 블로그를 보고 다시 정리하였다. 태그를 하나씩 배우는 것도 좋았지만, 그보다는 정적인 웹 서버와 동적인 웹 어플리케이션 서버 사이의 차이점을 직관적으로 알 수 있게 된 것이 좋았다. 미리 만들어둔 html코드를 서빙하는 것과, 프로그래밍 언어와 프레임워크를 통해 동적으로 html태그들을 생성해서 서빙하는 것의 차이였다. Django프레임워크 실습을 하면서 이 차이를 느꼈을 때 html이 무엇인지 미리 공부하고 오길 잘했다는 생각이 들었다.

파이썬은 저번 학기 학교 수업에서 써보았지만 코딩 양이 많지는 않았다. 그래서 학원에서 다룬 언어들에 비해 익숙하지 않다. 이 쯤에서 다시 리마인드도 하고 Django배우면서도 잘 쓸 수 있도록 예전에 배웠던 내용들을 다시 찾아보았다. 문법적으로는 C#이나 C보다 친절해서 막상 파이썬으로 코딩할 일이 많아지면 금방 익숙해 질 수 있을 것 같다. 이제 눈으로만 보고 까먹는건 그만하고 배울 때 제대로 배워놔야겠다.ㅎㅎ

## 장고 설치 및 가상환경의 개념
 강의에 등장하는 내용은 아니지만 장고 설치 과정에서 이것저것 찾아보다 가상환경의 개념에 대해 알게 되었다. 바로 [다른 프로젝트](https://github.com/charlesuu/first-Django-app)에 적용해보면서 익혀보았다. 결론적으로는 한 컴퓨터에서 여러 프로젝트를 만들 때, 프로젝트 별로 전용 환경을 구성하는 개념이었다. 모든 파이썬 프로젝트가 같은 패키지 및 인터프리터를 사용하면 프로젝트를 여러 개 개발 할 때 버전 차이로 인해 꼬일 여지가 생긴다. 이런 상황이 생기지 않게 프로젝트 별로 완전히 분리된 환경을 만들어주는 기능이었다. 복잡한 프로젝트를 여러 개 개발하게 되거나, 특수한 버전의 패키지를 필요로하는 프로젝트를 하게 될 때 유용하겠다.

## 포트

<p align="center"><img width="70%" src="https://user-images.githubusercontent.com/76809524/155928601-8b407130-91a4-4b37-b374-b8a139002eae.png"/>(출처 : 생활코딩)</p>


 웹 수업에서 내 컴퓨터를 서버로 사용해서 웹 사이트를 동작시키는 실습을 해보았다. 그 과정에서 계속 쓰였던 것이 IP주소와 포트였다. Django 수업에서는 포트에 대해 좀 더 알 수 있었다. 서버 컴퓨터에 접속하고 싶다면 주소를 통해 접근하면된다. 그런데 서버 컴퓨터에는 다양한 서버 소프트웨어가 깔려있으므로 그 중 어떤 소프트웨어에 접근해야하는지는 IP주소만으로 알 수 없다. 이를 해결하기 위해 각 소프트웨어는 하나의 포트에 연결되어있다. 어떤 포트에 접근하는 것으로 원하는 소프트웨어를 사용할 수 있는 것이다.
 예를 들어 django 테스트용 서버는 기본적으로 8000번 포트를 사용한다. 따라서 <code>python manage.py renserver;</code> 명령어를 실행하고 <code>http://127.0.0.1:8000</code>으로 접속하는 것이다. 만약 8000번 포트를 다른 프로그램이 사용중이거나, 그냥 다른 포트를 사용하고 싶다면 <code>python manage.py renserver 8888;</code> 처럼 다른 포트 주소를 입력해주면 된다.


## 프로젝트/앱, 라우팅
<p align="center"><img width="50%" src="https://user-images.githubusercontent.com/76809524/155964511-a0d01d7b-0f75-451a-be97-bc05b624e3b3.png"/><img width="50%" src="https://user-images.githubusercontent.com/76809524/155965357-c0e70b9d-4973-40d3-8b40-24ce86d3d1fc.png"/></p>
<p align="center"><img width="70%" src="https://user-images.githubusercontent.com/76809524/155965357-c0e70b9d-4973-40d3-8b40-24ce86d3d1fc.png"/></p>

 학원에서 C, C#으로 프로그램을 만들 때 함수, 클래스, 파일 등으로 로직을 쪼갰었다. 한 파일의 main문에서 모든 로직을 구현할 수도 있지만, 연관성있는 로직끼리 그룹을 지어서 관리하는게 더 좋았기 때문이다. 실제로 코딩 양이 많은 과제를 할 때 함수로 적절히 쪼개가며 코딩하는게 훨씬 생각하기도 편하고, 읽기도 편해서 다음 날에 이어서 코딩하기도 수월하다는 걸 느낀적이 많았다.
  같은 원리로 웹 어플리케이션을 만들 때도 프로젝트 단에서 모든 로직을 구현하기 보다 기능별로 앱을 만드는 방법이 있었다. 첫 번째 그림에서 처럼


## CRUD
