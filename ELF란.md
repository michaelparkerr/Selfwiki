# ELF란?

ELF : **Excutable** and **Linkable** Format

Location : /usr/bin

Instruction : readelf -h gcc

- **ELF**

  실행파일

- **실행**

  디스크에 저장된 프로그램이 메모리 영역으로 올라가서 컴퓨팅 자원을 사용하여 서비스를 제공해주는 것.

- **프로세스**

  실행 중인 프로그램

- **주소공간 = 세그먼트**

  프로세스에게 주어진 메모리 영역(가상[MMU를 이용한 페이징 이용하여 가상 주소]+물리)

- **ELF의 역할**

  프로그램이 실행될 때 메모리 올라가야하는 영역을 미리 정리하여 관리. 

- **메모리에 올라가야하는 부분**

  코드, 전역 데이터, 읽기 전용 데이터 등 + ELF가 덧붙일 데이터

- **코드의 실행 => 프로세스 진행**

  올라온 주소 공간의 text 영역(=코드 영역)의 instruction을 한 라인씩 실행



main.c

```c
#include "my_header.h"

int main(void){
    	my_func();
    	return 0;
}
```

my_header.h

```c
void my_func();
```

my_header.c

```c
#include "my_header.h"

void my_func() {}
```

Compile instruction

```bash
gcc main.c my_header.c -o main
```

 이 과정에서 my_func 를 알려줘야 완벽한 프로그램이 된다.

- **알려주는 시점**

  컴파일할 때, 실행할 때(메모리에 로드할 때), 런타임할 때

- **ELF의 .rel 섹션**

  my_func를 rel 섹션에 적어둔다 = relocatable symbol을 resolving reference해달라는 요청

  **이것이 Linkable**하다는 것이다.

- 