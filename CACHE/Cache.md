# Cache
캐시는 재요청시 빠른 응답을 하기위해 저장해둔 데이터를 말한다.

캐시는 특정 분야에서 사용하는 것이 아닌 여러 분야에서 사용되며, 방식의 차이는 있지만 빠른 처리를 위해 데이터를 저장한다는 점은 동일하다.

CPU도 메모리의 접근을 줄이기 위해 캐시를 두고 있으며, DB나 웹 서버, 웹 브라우저 등에서도 사용되고 있다.

## 캐시의 효율
캐시가 존재하면 무조건 효율적일까

캐시는 필요한 데이터를 복사해 뒀다가 필요해지면 별도의 과정없이 복사해둔 데이터를 사용하는 것이다. 그 말은 복사해두지 않은 데이터는 원래대로 처리를 해야한다는 뜻이고, 거기에 캐시 관리와 탐색에 대한 오버헤드가 들게 된다는 뜻이다.

캐시는 어떤 데이터를 저장해 둘 것인가가 중요한 문제이다.

CPU캐시를 기준으로 얘기해보자.

CPU캐시는 CPU의 몇가지 특성을 근거로 캐시를 관리한다.
- Temporal Locality (시간적 지역성) : CPU가 메모리에 접근할 때, 해당 메모리에 다시 접근할 확률이 높다.
- Spatial Locality (공간적 지역성) : CPU가 메모리에 접근하면, 근처 메모리에 접근할 확률이 높다.

CPU가 위과 같은 메모리 접근을 하는 경향은 다음과 같은 이유가 있다.
- 프로그램의 구조 : 프로그램의 절차적인 구조로 데이터의 접근이 근처로 이어진다. 반복문으로 인해 접근했던 데이터에 반복적으로 접근한다.
- 선형적인 데이터 구조 : 배열과 같은 구조는 데이터가 선형적으로 이어져있어 높은 확률로 순차적으로 접근하게 된다.

# Redis
Redis와 in-memory, key-value에 대한 자세한 내용은 [링크](./Redis.md)

# Varnish
Varnish와 CDN에 대한 자세한 내용는 추가 예정

# 참고 자료
캐시
https://ko.wikipedia.org/wiki/%EC%BA%90%EC%8B%9C

캐시의 효율 https://en.wikipedia.org/wiki/Locality_of_reference