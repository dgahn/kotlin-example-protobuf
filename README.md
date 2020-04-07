# Protobuf

## Protocol Buffer란 무엇인가?

Protocol buffer(이하 Protobuf)는 데이터를 직렬화하는 메커니즘이다. 
Protobuf는 데이터를 한번 정의하는데 한번 정의된 데이터를 다양한 언어에서 다양한 구조로 쉽게
사용할 수 있다. 

## 어떻게 동작하는가?

**.proto** 파일에 Protobuf 메시지 유형을 정의하여 직렬화할 정보의 구조화 방법을 지정한다.
각 Protobuf 메시지는 이름과 값을 포함하는 논리적인 정보다. 예제를 보자.

```proto
message Person {
  required string name = 1;
  required int32 id = 2;
  optional string email = 3;

  enum PhoneType {
    MOBILE = 0;
    HOME = 1;
    WORK = 2;
  }

  message PhoneNumber {
    required string number = 1;
    optional PhoneType type = 2 [default = HOME];
  }

  repeated PhoneNumber phone = 4;
}
```

메시지 포맷은 간단하다. 각 메시지 타입은 하나 이상의 고유 한 번호가 지정된 필드가 있다.
(Persion의 name은 1번) 각 필드에는 이름 및 유형이 있고 여기서 값 유형은 숫자, 부울, 문자열, 원시 바이트 또는 짝수일 수 있다.
위와 같이 다른 프로토콜 버퍼 메시지 유형으로 데이터를 계층적으로 구성할 수도 있다. 필드는 optional, required, repeated로 선언할 수 있다.
ProtoBuf에 대한 문법은 [링크](https://develop.google.com/protocol-buffers/docs/proto)를 참고해라

