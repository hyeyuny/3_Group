# 13week

### <정리>

**fscanf()함수의 형식**

fscanf(FILE*포인터, 변환기호, 변수 목록);

변환기호: scanf()함수에서 사용한 변환기호

변수 목록: 파일에서 읽어온 자료가 저장될 변수 또는 변수의 주소

반환 값: 함수가 정상적으로 실행되면 파일에서 읽어들인 항목 수를 반환

### <질의응답>

```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>
#include <stdlib.h>

struct students {
char name[40];
char address[40];
int age;
};

typedef struct students student;
int main(void) {
FILE* fp1;
student st1 = { "홍길동", "서울", 30 }, st2;

if ((fp1 = fopen("basic.txt", "w")) == NULL) {
	printf("no file");
	exit(1);
}

fprintf(fp1, "%s %s %d\\n", st1.name, st1.address, st1.age);
fclose(fp1);

if ((fp1=fopen("basic.txt", "r")) == NULL) {
	printf("no file");
	exit(1);
}

fscanf(fp1, "%s %s %d\\n", st2.name, st2.address, &st2.age);
printf("name: %s, address: %s, age: %d\\n\\n", st2.name, st2.address, st2.age);

fclose(fp1);
return 0;
}
```

위 코드에서 이해가 안 되는 부분이 있어. 'basic.txt'를 읽기 모드('r')로 다시 열어, 'st2'에 파일의 내용을 읽어 들이고, 읽어 들인 'st2'의 정보를 출력하는 부분인데 'st1'의 정보를 출력하는 거 아니야?

<aside>
💡 응 맞아.  그런데 'st1'의 정보를 'basic.txt' 파일에 저장한 후에 이 정보를 다시 읽어서 'st2'에 저장하는 거야. 이후 'st2'의 정보를 출력하면, 원래 'st1'에 있던 정보가 출력되는 거야. 즉, 이 코드는 'st1'의 정보를 파일에 저장하고, 그 저장된 정보를 'st2'로 불러와 출력하는 과정을 보여주는 거지. 따라서 'st1'의 정보를 출력하는 것이 아니라, 'st1'의 정보를 파일에 저장한 후 그것을 'st2'에 불러와서 출력하는 거야. 이해가 됐어?

</aside>

혹시 st2로 불러오는 과정을 설명해줄 수 있어?

<aside>
💡 그래. 먼저, 'basic.txt'라는 파일을 읽기 모드('r')로 열어줘. 만약 파일 열기에 실패하면 "no file"이라는 메시지를 출력하고 프로그램을 종료해.

</aside>

```c
if ((fp1=fopen("basic.txt", "r")) == NULL) {
	printf("no file");
	exit(1);
}
```

<aside>
💡 파일이 정상적으로 열렸다면, 'fscanf' 함수를 사용하여 파일의 내용을 읽어 들여. 'fscanf'는 파일에서 데이터를 읽어와 변수에 저장하는 함수야.

</aside>

```c
fscanf(fp1, "%s %s %d", st2.name, st2.address, &st2.age);
```

<aside>
💡 위 코드에서 "%s %s %d"는 각각 문자열, 문자열, 정수를 의미하며, 이 순서대로 'st2.name', 'st2.address', 'st2.age'에 데이터를 저장하게 돼. 이렇게 해서 'st1'의 정보가 'basic.txt' 파일에 저장된 후 그 정보가 다시 'st2'에 저장되는 거야.

</aside>

<aside>
💡 마지막으로, 'printf' 함수를 이용해 'st2'의 정보를 출력하고, 'fclose' 함수를 이용해 파일을 닫아.

</aside>

```c
printf("name: %s, address: %s, age: %d\n", st2.name, st2.address, st2.age);
fclose(fp1);
```

<aside>
💡 이렇게 파일에서 정보를 읽어와 'st2'에 저장하고, 그 정보를 출력하는 과정이 'st2'로 불러오는 과정이야. 이해됐어?

</aside>

응 이해됐어. 내가 fscanf 함수에 대해 잘 몰랐었네. 다시 한번 정리해야겠다.

근데 위의 코드를 다른 방법으로 쓸 수 있는 방법이 있을까? 내 생각엔 fwrite 함수와 fread함수로 바꿔서 쓰면 우리가 원하던 결과를 똑같이 얻을 수 있을 것 같아

```c
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>
#include <stdlib.h>

struct students {
char name[40];
char address[40];
int age;
};

typedef struct students student;

int main(void) {
FILE* fp1;
student st1 = { "홍길동", "서울", 30 }, st2;
if ((fp1 = fopen("basic.txt", "wb")) == NULL) {
    printf("no file");
    exit(1);
}

fwrite(&st1, sizeof(student), 1, fp1);
if (fclose(fp1) != 0) {
    printf("no file");
exit(1);
}

if ((fp1 = fopen("basic.txt", "rb")) == NULL) {
    printf("no file");
    exit(1);
}

fread(&st2, sizeof(student), 1, fp1);
printf("name: %s, address: %s, age: %d", [st2.name](http://st2.name/), st2.address, st2.age);

if (fclose(fp1) != 0) {
    printf("no file");
}
return 0;
}
```

<aside>
💡 이렇게 말이야

</aside>

흠, 그럼 이걸 실행해볼래?

![1.png](13week%2029db0b6a2a784f17a01f1db18d1c77dd/1.png)

![2.png](13week%2029db0b6a2a784f17a01f1db18d1c77dd/2.png)

<aside>
💡 실행결과는 같지만 메모장엔 우리가 원하는 결과가 작성되지 않았어. 왜 그런거야?

</aside>

'fwrite()'와 'fread()' 함수는 데이터를 그대로, 즉 바이너리 형태로 저장하고 읽어오는 함수야. 이런 방식으로 저장된 데이터를 메모장 같은 텍스트 편집기로 열면, 데이터가 이상하게 보일 수 있어. 왜냐하면 바이너리 데이터는 일반적으로 글자로 표현되지 않기 때문이야.

예를 들어, 숫자 30이 'fwrite()'로 저장되면, 컴퓨터는 이를 이진 데이터로 바꿔서 저장해. 그런데 이 이진 데이터를 메모장에서 열어보면, 이진 데이터에 해당하는 글자로 변환되어 보이게 돼. 그런데 대부분의 이진 데이터는 실제 글자와 일치하지 않으므로, 이상한 글자나 물음표로 보일 수 있지. 위의 결과처럼 말이야.

이런 현상을 피하려면, 'fprintf()'나 'fscanf()' 같은 함수를 사용해서 데이터를 글자 형태로 저장하고 읽어오면 돼. 위에서 다룬 내용이지?

그럼에도 불구하고, 바이너리 형태로 데이터를 저장하고 읽어와야 할 필요가 있다면, 바이너리 파일을 볼 수 있는 별도의 프로그램을 사용하거나, 프로그램 안에서 바로 파일의 내용을 읽어와서 출력하는 코드를 작성해서 사용하면 돼.