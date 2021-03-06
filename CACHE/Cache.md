# Cache
캐시는 재요청시 빠른 응답을 하기위해 저장해둔 데이터를 말한다.

캐시는 특정 분야에서 사용하는 것이 아닌 여러 분야에서 사용되며, 방식의 차이는 있지만 빠른 처리를 위해 데이터를 저장한다는 점은 동일하다.

CPU도 메모리의 접근을 줄이기 위해 캐시를 두고 있으며, DB나 웹 서버, 웹 브라우저 등에서도 사용되고 있다.

## 캐시의 효율
캐시가 존재하면 무조건 효율적일까

캐시는 필요한 데이터를 별도의 메모리에 복사해 뒀다가 필요해지면 캐시 메모리에 있는지 확인하고, 있으면 바로 데이터를 가져오고, 없으면 원본에서 데이터를 찾아 가져오게 된다. 캐시 메모리에 데이터가 없으면 데이터를 찾는 오버헤드만 늘어난 것이 된다.

캐시는 캐시메모리에 데이터가 있을 수록(Cache Hit) 성능에 도움이 된다.

CPU캐시를 기준으로 얘기해보자.

CPU캐시는 CPU의 몇가지 특성을 근거로 캐시를 관리한다.
- Temporal Locality (시간적 지역성) : CPU가 메모리에 접근할 때, 해당 메모리에 다시 접근할 확률이 높다.
- Spatial Locality (공간적 지역성) : CPU가 메모리에 접근하면, 근처 메모리에 접근할 확률이 높다.
```
CPU가 위과 같은 메모리 접근을 하는 경향은 다음과 같은 이유가 있다.
- 프로그램의 구조 : 프로그램의 절차적인 구조로 데이터의 접근이 근처로 이어진다. 반복문으로 인해 접근했던 데이터에 반복적으로 접근한다.
- 선형적인 데이터 구조 : 배열과 같은 구조는 데이터가 선형적으로 이어져있어 높은 확률로 순차적으로 접근하게 된다.
```
위와 같은 특성이 없다면 캐시는 성능에 도움을 주지 못할 것이다. 오히려 캐시 체크하는 오버헤드로 인해 성능이 저하될지도 모르겠다.

# CDN
Contents Delivery Network

물리적으로 떨어져있는 클라이언트에 빠르게 데이터를 전송하기 위한 기술이다.

원리는 다음과 같다.

![CDN](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=http%3A%2F%2Fcfile9.uf.tistory.com%2Fimage%2F99EA983C5C5304ED21598E)

원본 서버의 데이터를 캐싱하는 서버를 두고 클라이언트의 요청이 오면 캐시 서버가 클라이언트의 요청을 처리한다. 원본서버는 캐시서버의 요청만 처리한다.

위와 같은 구성이 어떤 이점이 있는지 알아보자.
- 캐시서버가 많을 수록 클라이언트의 요청이 분산된다.
- 캐시서버가 물리적으로 떨어져 있으면, 해당 서버 근처의 클라이언트들이 빠르게 데이터를 받을 수 있게 된다.
- 원본 서버가 잠시 다운되더라도 캐시서버의 데이터로 운영이 가능하다.(다운로드만)

다운로드가 대다수인 서비스에서 좋은 성능을 보일 수 있다. (ex. 스트리밍, 퍼블리싱)

## GSBL
CDN을 얘기할 때, GSBL이라는 개념이 같이 나온다.

Global Server Load Balancing

DNS 서비스의 발전된 형태라고 한다.

DNS에 비해 여러 기능이 추가돼 클라이언트가 최대한 빠르게 응답을 받을 수 있는 서버를 알려준다. (서버 부하, 위치, 레이턴시를 기준으로 정한다.)

자세한건 직접 찾아보자.

# Redis
Redis와 in-memory, key-value에 대한 자세한 내용은 [링크](./Redis.md)

# Varnish
Varnish는 웹 캐시 서버이다. 웹 가속기라는 표현을 사용하는데 필자가 보기엔 표현의 차이다.

프록시 서버이자 웹 캐시 서버인 Squid에 비해 더 좋은 성능을 보인다고 한다.

VCL이라는 설정언어를 사용해 간단하게 설정을 할 수 있다.

# 참고 자료
캐시
https://ko.wikipedia.org/wiki/%EC%BA%90%EC%8B%9C

캐시의 효율
https://en.wikipedia.org/wiki/Locality_of_reference

CDN
https://goddaehee.tistory.com/173

Varnish
https://d2.naver.com/helloworld/352076

