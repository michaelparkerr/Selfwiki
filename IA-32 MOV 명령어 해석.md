- 32bit CPU여도 16bit register인 AX사용 가능. 사용하기 위해서는  Prefix를 붙여줘야함.

**Intel 64 and IA-32 Architectures Instructuion Format**

(인텔 64 and IA[Intel Architecture]-32 명령어 집합 구조 포맷)

**IA-32**는 이전 사용되던 **IA-16 Architecture**의 확장임.

IA-32 = x86-32

**x86(80x86) = 인텔이 개발한 마이크로프로세서 계열 + 이들과 호환되는 프로세서들에서 사용한 명령어 집합 구조 통칭하는 말**

이렇게 이름이 붙은 이유는 초기 프로세서들 이름이 모두 **80으로 시작해서 86**으로 끝났기 때문.

여기서 InstructionPrefix가 32비트 CPU가 16비트로 사용할 수 있게 해주는 것.

![사용자 삽입 이미지](http://cfs8.tistory.com/upload_control/download.blog?fhandle=YmxvZzIyNTgzM0BmczgudGlzdG9yeS5jb206L2F0dGFjaC8wLzI1MDAwMDAwMDAwMC5wbmc%3D)

- Instruction Prefixes : 첫 1Byte 위치에 존재할 수도 존재하지 않을 수도 있음. 존재할 경우 Group 1~4까지 4가지 Group으로 나뉜다. 명령어의 쓰임에 따라 존재 여부가 결정, 주로 string명령어들과 함께 사용되고 해당 명령어에 대해서 특정한 상황에 반복적인 일을 처리할 때 사용하거나 16비트-> 32비트의 어드레스 사이즈로 해석하거나 32비트->16비트 어드레스 사이즈로 해석할 때 사용함	.

- Opcode : 명령코드=작동코드, 마이크로 프로세서가 수행해야할 일들의 종류를 나타내주는 필드. 데이터 처리, 저장, 이동, 비교, 분기 명령어가 있음. 명령어 종류에 따른 여러가지 opcode가 존재. 1,2,3 Byte값이 들어갈 수 있음.

mov 명령어 하나만으로도 다양한 mov op 코드 리스트가 있음.

![1562502348935](C:\Users\kim\AppData\Roaming\Typora\typora-user-images\1562502348935.png)

- ModR/M : 오퍼랜드(피연산자)가 레지스터에 있는지, 메모리에 있는지를 나타내는 것. Mod,Reg/Opcode,r/m의 3개의 필드로 구성. 메모리상의 오퍼랜드를 참조하는 많은 명령들은 주소 지정 방식을 지시하는 바이트인 ModR/M 바이트를 Opcode 바로 다음에 가진다. ModR/M 바이트는 해당 OP 코드가 가진 오퍼랜드의 종류와 방식을 지정한다는 점에서 큰 의미가 있다. ModR/M 바이트를 통해서 지정할 수 있는 오퍼랜드의 종류는 레지스터와 메모리번지가 있으며 메모리 번지인 경우에는 번지 지정 형식까지 알려주기 때문에 상당히 중요한 바이트이다. 1바이트 값이 들어간다.

![1562505486781](C:\Users\kim\AppData\Roaming\Typora\typora-user-images\1562505486781.png)

![1562505506918](C:\Users\kim\AppData\Roaming\Typora\typora-user-images\1562505506918.png)

- EC의 11100000 값을 환산한 것.

![1562505598512](C:\Users\kim\AppData\Roaming\Typora\typora-user-images\1562505598512.png)

레지스터 코드 50+r 에서 0이므로 eax, 52는 2이므로 edx 이런식으로 57이 push edi가 되는 것.

- SIB Byte : 간접 어드레스 형태로 주소 지정되었을 때 인덱싱 할 때 인덱스 값과 스케일 값 수치를 나타내기 위해서 사용한다. 1바이트 값이 들어간다.
- Displacement : 번지 지정 시에 변위값(Offset) 지정할 때 사용한다. 1,2 또는 4바이트 값이 들어가거나 안 들어간다.
- Immediate : 번지 지정 시에 상수로 정의한 값을 오퍼랜드로 사용할 때 사용한다. 1,2,4 바이트 값이 들어가거나 안 들어간다.