---
layout: post
title: Spring MVC 설명 및 WAS,Web Server 차이
date: August 4, 2022
tags: [java]
---

## Spring MVC 구조

---

![Untitled](https://user-images.githubusercontent.com/52904676/182862105-9fb426f3-48fe-4f15-9a0d-dc3379dcb897.png)

- client : 브라우저
- client → dispathcer-servlet → Controller : client에서 Controller로 url을 요청하면 dispatcher-servlet에 정의된 내용에서 해당 url이 존재하면 Controller에 넘겨준다.
- **dispathcer-servlet : HTTP 프로토콜로 들어오는 모든 요청을 가장 먼저 받아 적합한 컨트롤러에 위임해주는 프론트 컨트롤러**
- View : Jsp, tiles, json
    - tiles : header, footer 정의 (layout 정의)
- scope : 변수를 어떤 범위 내에서 사용할지를 정하는 기준
    - request : 1요청 1응답 후 데이터 사라짐 (범위 : 요청이 응답이 올때까지)
    - session : 1 client (범위 : client 하나당)
    - application : application이 시작되고 종료될 때까지 (application은 잘 사용 안함)
- Controller → View : forward/redirect
    
    **Forward vs Redirect**
    
    - jsp 환경에서 현재 작업중인 페이지에서 다른 페이지로 이동하는 두가지 방식의 페이지 전환 기능

    1. **forward : url이 안바뀜**
        - 예시1. 고객센터에서 A에 전화 후 A에서 B로 연결해주면 고객 정보를 그대롤 넘겨주어 따로 고객정보를 말 안해도 되는 상황이 포워드
        
        ![Untitled 1](https://user-images.githubusercontent.com/52904676/182862266-ec9972fc-3acf-48e2-b5b4-6b3f80a80a25.png)
        
        - 현재 실행중인 페이지와 forward에 의해 호출될 페이지는 request, response 객체를 공유함
        - **forward(건네주기) 방식은 요청정보를 그대로 전달함**
        - **그렇기 때문에 사용자가 최초로 요청한 요청정보는 다음 URL에서도 유효함**
    
    2. **redirect : url이 바뀜**
        - 예시1. 고객센터에서 A에 전화 후 고객정보를 다 이야기했는데 그건 B에서 얘기해야한다고 다시 전화하라고 하는 경우가 redirect
        
        ![Untitled 2](https://user-images.githubusercontent.com/52904676/182862688-58f25d4d-0c4c-4c48-be5c-5f08953f2df8.png)
        
        - 새로운 페이지에서는 request, response 객체가 새롭게 생성됨
        - **redirect의 경우 최초 요청을 받은 url1에서 클라이언트에 redirect할 url2를 리턴하고, 클라이언트에게 전혀 새로운 요청을 생성하여 url2에 다시 요청을 보낸다. 다라서 최초의 요청정보는 더이상 유효하지 않게된다.**
        
        💡 **정리**
        1. url의 변화여부 (forward → 변화 x, redirect → 변화 o)
        2. 객체의 재사용 여부 (forward → 재사용 o, redirect → 재사용 x)

<details markdown=block>
<summary markdown=span>DTO/DAO</summary>
- DAO : Data Access Object는 DB를 사용해 데이터를 조회하거나 조작하는 기능을 전담하도록 만든 오브젝트

- DTO : Data Transfer Object는 VO(Value Object)로 바꿔 말할 수 있는데 계층간 데이터 교환을 위한 자바빈즈를 말한다. 컨트롤러, 뷰, 비즈니스 계층, 퍼시스턴스 계층을 말하며 각 계층간 데이터 교환을 위한 객체를 **DTO** 또는 **VO**라고 부른다.
</details>


### WAS, WebServer

---

**[Web Server]**

- 정적 컨텐츠(html, css 등) 제공
    - WAS를 거치지 않고 바로 제공
- 동적 컨텐츠 제공을 위한 요청 전달
    - request를 WAS에 전달
    - response를 client에 전달

**[WAS]**

- webServer + webController
- tomcat
- DB 조회와 같은 동적 처리

**[Web Server와 WAS를 분리하는 이유]**

- 서버 부하를 방지해 속도를 더 빠르게 하기 위함
- Webserver 하나의 여러개의 WAS를 붙여서 사용할 수 있음

## Reference

---

- [**Redirect VS, Forward (Redirect와 forward의 차이)**](https://doublesprogramming.tistory.com/63)