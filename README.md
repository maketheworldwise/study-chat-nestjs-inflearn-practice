# 탄탄한 백엔드 NestJS, 기초부터 심화까지

> 이 프로젝트는 [탄탄한 백엔드 NestJS, 기초부터 심화까지](https://www.inflearn.com/course/%ED%83%84%ED%83%84%ED%95%9C-%EB%B0%B1%EC%97%94%EB%93%9C-%EB%84%A4%EC%8A%A4%ED%8A%B8)강의에서 진행하는 랜덤 채팅 웹 앱 프로젝트입니다.

## 🌴 진행 과정

**프로젝트 설치 :**

```shell
nest new .
npm install --save hbs # Template Engine
npm install --save @nestjs/mongoose mongoose
npm install --save @nestjs/config
```

**MVC 패턴 적용 :**

- public(css, js), views(index.hbs) 디렉토리 생성
- service 제거

**Socket 통신**

HTTP 연결 방식은 단방향이다. 예를 들어 A 클라이언트가 서버에 요청을 보내면, 서버가 응답을 보낼 때 A 클라이언트에게만 전달된다.

만약, A 클라이언트의 요청에 대한 응답을 B 클라이언트도 공유 받아야할 경우에는 어떻게 해야할까?

가장 간단하게 생각할 수 있는 방법은 B 클라이언트가 지속적으로 짧은 시간 동안 다른 클라이언트에 대한 처리 상황을 공유해달라고 요청을 보내는 것이다. 하지만 서버는 지속적인 요청에 대해서 응답을 처리해줘야하는 문제가 있다. 즉, 부하가 커진다는 것이다.

이러한 문제를 해결하기 위해서 Socket 통신이 등장했다. 쉽게 비유해서 생각해보자면, 서버쪽에 멀티탭이 있는 개념이다. 멀티탭의 각 콘센트에 연결된 모든 장비는 전기를 요청할 것이고, 전기 요청을 동시에 전달하는 것이다.

클라이언트가 이벤트를 등록을 하고 서버에 보내고(emit), 서버에서 받아서(on) 클라이언트에 응답을 보내고(emit) 그 응답을 클라이언트가 받는(on) 구조다.

```shell
npm install --save @nestjs/websockets @nestjs/platform-socket.io
nest generate gateway chats
nest generate module chats
```

## 📚 참고

- https://docs.nestjs.com/techniques/mvc
- https://docs.nestjs.com/websockets/gateways
