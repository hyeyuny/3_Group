# 12week

### **<질의 응답>**

<aside>
💡 **typedef를 사용하여 재정의한 구조체의 이름을 변경하면 기존의 구조체 이름은 어떻게 되는거야?**

</aside>

 typedef를 사용하여 재정의한 구조체의 이름을 변경해도 기존의 구조체 이름은 그대로 유지돼.

 예를 들어, 아래의 코드에서 struct ThreeDime라는 이름의 구조체를 typedef를 사용하여 ThreeDime라는 새로운 이름으로 재정의해볼게.

```c
struct ThreeDime
{
double x;
double y;
double z;
};
typedef struct ThreeDime ThreeDime;
```

 이 경우, struct ThreeDime와 ThreeDime는 동일한 구조체를 가리키게 되지만, 두 이름 모두 사용할 수 있어. 즉, struct ThreeDime는 여전히 유효하며, ThreeDime라는 이름으로도 같은 구조체를 참조할 수 있는거야.

 하지만, 일반적으로 typedef를 사용하여 재정의한 이름을 주로 사용해. 이는 코드의 가독성을 높이고, 코드를 더 간결하게 작성할 수 있게 도와줘.

<aside>
💡 **예제 11-6에서 이해가 안되는 부분이 있어.**

</aside>

```c
ThreeDime* pA1 = &A1;
```

<aside>
💡 **이 부분을 설명해줘**

</aside>

 먼저 포인터에 대한 기본 개념을 다시 이해해보자. 포인터는 메모리 주소를 저장하는 변수야. 포인터 변수는 특별한 형태의 변수로, 다른 변수의 주소를 저장하며 이를 통해 해당 주소에 저장된 값을 간접적으로 접근하거나 변경할 수 있어.

 예제 11-6을 천천히 살펴보자. struct ThreeDime는 3차원 공간에서의 한 점을 나타내는 구조체를 정의해. 이 구조체는 x, y, z라는 이름을 가진 세 개의 double 타입 변수를 가지고 있어. 이 세 변수는 각각 3차원 공간에서의 x, y, z 좌표를 나타내.

 typedef struct ThreeDime ThreeDime;는 struct ThreeDime을 ThreeDime이라는 새로운 자료형으로 정의해. 이렇게 하면 코드를 작성할 때 struct ThreeDime 대신 ThreeDime으로 간단히 사용할 수 있어.

 그 다음main 함수에서는 ThreeDime 타입의 변수 A1을 선언하고, 이 변수에 {3, 1, 8}이라는 값을 초기화해. 이는 3차원 공간에서의 한 점을 나타내며, x, y, z 좌표는 각각 3, 1, 8이야.

 이제부터 잘 들어야해. ThreeDime* pA1 = &A1; 는 A1 변수의 주소를 가리키는 포인터 pA1을 선언해. 이렇게 하면 pA1을 통해 A1의 값을 간접적으로 접근하고 변경할 수 있어. pA1은 이 포인터의 이름이고, & 연산자는 변수의 메모리 주소를 반환하는 C언어의 주소 연산자야.

 printf 함수는 pA1 포인터를 통해 A1의 x, y, z 좌표 값을 출력해. 여기서 -> 연산자는 포인터를 통해 구조체의 멤버에 접근하는데 사용되는 연산자야.

<aside>
💡 **아하 이해가 됐어. 근데 포인터를 이용해서 구조체 멤버의 값을 변경하는 방법도 있어?**

</aside>

응.

```c
#include <stdio.h>

struct ThreeDime
{
double x;
double y;
double z;
};

typedef struct ThreeDime ThreeDime;

int main(void)
{
ThreeDime A1 = { 3, 1, 8 };
ThreeDime* pA1 = &A1;
printf("변경 전 3차원 점 A1의 x : %.2lf, y : %.2lf, z : %.2lf\n", pA1->x, pA1->y, pA1->z);
pA1->x = 5.0;
pA1->y = 2.0;
pA1->z = 9.0;
printf("변경 후 3차원 점 A1의 x : %.2lf, y : %.2lf, z : %.2lf\n", pA1->x, pA1->y, pA1->z);
return 0;
}
```
![1](https://github.com/hyeyuny/C_pg-3_group-notes-note-1/assets/144858340/e907d9d8-bb45-4b6d-98f5-b109abe12491)
이렇게 말이야. 그러면 `pA1`이 가리키는 구조체의 x, y, z 멤버 값이 각각 5.0, 2.0, 9.0으로 변경돼.

<aside>
💡 **또 질문이 있어. 연산자를 사용하지 않고 구조체 포인터를 통해 멤버에 접근할 수 있어??**

</aside>

응 그 방법은 *연산자와 도트 연산자를 함께 사용하는거야.

```c
(*pA1).x
(*pA1).y
(*pA1).z
```

여기서 *pA1는 pA1 포인터가 가리키는 A1 구조체를 의미하며, . 연산자를 통해 그 구조체의 멤버에 접근해. 그러나 이 방법은 코드가 길어지고 복잡해질수록 가독성이 떨어질 수 있어서, 일반적으로는 -> 연산자를 주로 사용해.
