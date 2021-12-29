### C# Type
#### 정수
##### byte
1-byte unsigned int를 다루는 type. Level 같이 0~255 범위 안에서 변하는 값을 공간 효율적으로 저장할 때 이용.<br>
같은 크기로 signed int를 다루는 sbyte도 지원됨.
##### short
2-bytes signed int를 다루는 type. -3만 ~ 3만까지의 값을 다룸. <br>
역시 unsigned int를 다루는 ushort가 지원됨.
##### int
4-bytes signed int를 다루는 type. -21억 ~ 21억까지의 값을 다룸. 어지간하면 int로 관리 가능.<br>
역시 unsigned int를 다루는 uint가 지원됨.
##### long
8-bytes signed int를 다루는 type. 어지간하면 쓸 일 없을 정도로 큰 범위. <br>
역시 unsigned int를 다루는 ulong이 지원됨.
#### char
C++과 달리 2-bytes의 크기를 가짐 - 기존보다 더 많은 수의 문자를 다룰 수 있음.
#### var
JavaScript에서의 var와 같이 정해진 type은 없고 동적으로 type이 지정됨.<br>
확실히 편하지만 변수가 어떤 type인지 확인하기 번거로워 협업에 좋지 않고, 프로그램 동작에 있어 불안정 요소가 생길 수 있기 때문에 가능하면 남용하지 않는 것이 좋다.
#### Convert.Toint32(value)
형변환에 이용되는 기본 제공 함수이다. 다만 형변환이 불가능한 구조(ex - Convert.Toint32("hello"))일 경우 에러 메시지를 보내므로 주의를 요해야 한다. 

### Operators
#### 비트 연산
##### x << k, x >> k
x의 bits를 k칸씩 미는 연산.<br>
signed value에 >> 연산을 수행할 때에는 주의해야 한다(부호는 유지하기 때문). 따라서 shift 연산은 unsigned value에 사용하는 것이 좋다.
##### x & y, x | y, x ^ y
x와 y의 각 bits에 대해 and, or, xor 연산을 수행하는 연산자. 
##### ~x
x의 각 bits를 flip하는 연산자.

### Formatted String
Formatted String의 경우 상당히 편리해졌다. <br>
`$"Hello World! My name is {name}"` 과 같이 쌍따옴표 앞에 $를 붙이고, 넣고 싶은 변수 양옆에 {}를 붙이면 `"Hello World! My name is %s"`, name"과 같은 작업을 할 수 있다. 

### Function 
#### Ref
Ref는 C++에서 &, dataType* 를 대체하는 개념이다. 예를 들어 함수에 직접 변수를 전달해야 할 때 C++에서는 void func(int* num_ref)라 정의하고 func(&num)과 같이 호출했다. C#에서는 이를 void func(ref int num), func(ref num)으로 대체한다.  
#### Out
Out은 좀 더 한정적인 ref의 개념으로, 함수 정의할 때 void func(out int result1, out int result2)와 같이 정의할 경우, 함수를 호출할 때 넣어준 인자 result1,2 값에 func 내에서 지정한 값을 저장할 수 있게 된다. 일반적으로 여러 개의 return value를 주고 싶을 때 이렇게 구현한다. 
> 이는 ref로도 충분히 구현 가능하다. 하지만 out 키워드의 경우 반드시 result1,2에 값이 담겨서 나와야 할 때 좀 더 안전한 구현이 가능해진다. ref와 달리 out은 해당 인자에 값이 저장되지 않으면 에러 메시지를 출력하기 때문. 즉 out 인자들의 값이 할당될 것을 보장해준다.
