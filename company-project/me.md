spring cloud zuul
=================
1.API GATEWAY란?  
-----------------
Microservice Architecture(이하 MSA)에서 언급되는 컴포넌트 중 하나이며, 모든 클라이언트 요청에 대한 end point를 통합하는 서버이다. 마치 프록시 서버처럼 동작한다. 그리고, 인증 및 권한, 모니터링, logging 등 추가적인 기능이 있다.  
모든 비지니스 로직이 하나의 서버에 존재하는 Monolithic Architecture와 달리 MSA는 도메인 별 데이터를 저장하고 도메일별로 하나 이상의 서버가 따로 존재한다. 한 서비스에 한개 이상의 서버가 존재하기 때문에 이 서비스를 사용하는 클라이언트 입장에서는 다수의 end-point가 생기게 되며, end-point를 변경이 있어났을떄, 관리하기가 힘들다. 그래서 MSA환경에서 서비스에 대한 도메인인 하나로 통합할 수 있는 API GATEWAY가 필요한 것이다.  

API GATEWAY를 도입하기 위한 오픈소스  
* KONG  
* API Umbrella  
* Netflix Zuul  
> Zuul is the front door for all requests from devices and web sites to the backend of 
the Netflix streaming application. As an edge service application, Zuul is built to enable 
dynamic routing, monitoring, resiliency and security. It also has the ability to route requests 
to multiple Amazon Auto Scaling Groups as appropriate.  

> Netflix에서 사용하는 API GATEWAY이다.  

2.Zuul이란?  
--------------------
2-1.Zuul을 사용하는 이유  
----------------------  
클라이언트 요청은 많은 트래픽과 다양한 형태(예상하지 못한)의 요청으로 경고없이 운영에 이슈를 발생시킨다. 이러한 상황에 신속히 대응할수 있는 시스템 zuul을 Netflix에서 개발하였다. zuul은 이러한 문제를 신속하고, 동적으로 해결하기 위해서 groovy 언어로 다양한 형태의 Filter를 실행한다. Filter에 기능을 정의하고, 이슈 사항 발생시 적절한 Filter를 추가함으로써 이슈사항을 대비할 수 있다.  

2-2.Netflix Filter의 기능 
----------------------- 
* Authentication and Security  
  * 클라이언트 요청시, 각 리소스에 대한 인증 요구 사항을 식별하고 이를 만족하지 않는 요청은 거부  
* Insights and Monitoring  
  * 의미있는 데이터 및 통계 제공  
* Dynamic Routing  
  * 필요에 따라 요청을 다른 클러스터로 동적 라우팅  
* Stress Testing
  * 성능 측정을 위해 점차적으로 클러스터 트래픽을 증가  
* Load Shedding  
  * 각 유형의 요청에 대한 용량을 할당하고, 초과하는 요청은 제한  
* Static Response handling  
  * 클러스터에 오는 응답을 대신하여 API GATEWAY에서 응답 처리  








































참고 링크  
----------
----------
LINK : [spring-cloud-netflix.docs](https://spring.io/projects/spring-cloud-netflix)  
LINK : [배민-API-GATEWAY-적용사례](http://woowabros.github.io/r&d/2017/06/13/apigateway.html)  
LINK : [Zuul2-참고-gitbook](https://coe.gitbook.io/guide/gateway/zuul_2)   



