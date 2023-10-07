# 5week

### <수업 내용 중 정리>

- switch~case문은 조건식을 먼저 평가한 뒤 그 식의 값이 case상수와 일치하는 쪽으로 분기하여 해당 명령문을 수행하는 선택문으로, 뒤에 반드시 수식이나 값을 넣어야 한다.

### <질의응답>

<aside>
💡 Q. 다중 if문을 사용한 예와 사용하지 않은 예의 차이는 뭘까?

</aside>

다중 if문을 사용했을 때, 다중 if문을 사용하지 않았을 때보다 조건문의 구조가 명확하게 드러나므로 이해하기 쉽고 조건을 유연하게 조정하기 쉬워

<aside>
💡 switch~case문을 대체할 수 있는 다른 패턴이나 방식이 있을까?

</aside>

if-else if문이 대체할 수 있는 것 같아. 예제에 나왔던 코드를 수정해서 실행해보자.

![5-1](https://github.com/hyeyuny/C_pg-3_group-notes-note-1/assets/144858340/d64e43c1-5266-4f86-82d3-fc67a400f763)

위의 사진은 switch-case문을 사용한 코드고,

![5-2](https://github.com/hyeyuny/C_pg-3_group-notes-note-1/assets/144858340/4501dbfc-80cd-4717-96fd-3eea39b3c3a5)

위의 사진은 if-else if문을 사용한 코드야

![5-3](https://github.com/hyeyuny/C_pg-3_group-notes-note-1/assets/144858340/f22093f8-d7b1-4601-b6ee-68f9ea83fff5)

두 개의 코드를 실행해봤더니 출력 화면이 똑같으므로 switch~case문과 if-else if문은 대체가 가능해

<aside>
💡 역시 대체가 가능하구나! 근데 switch~case문에서 각 case 블록의 마지막에 왜 break문을 사용하는 것이 일반적인 걸까?

</aside>

그건 각 case 블록의 끝에 break문을 사용하여 해당 case에서의 코드 실행을 중지하고 switch문을 빠져나가기 위함이야.

<aside>
💡 그러면 만약에 break문을 사용하지 않는다면 어떻게 될까?

</aside>

나는 실행이 안 될 것 같다고 생각해. break문이 없으면 코드를 실행했을 때 switch문을 빠져나가지 못하니까 실패한 빌드라고 뜨지 않을까?

<aside>
💡 우리 한번 실행을 해보자

![5-4](https://github.com/hyeyuny/C_pg-3_group-notes-note-1/assets/144858340/b5d4da1d-fec2-4a93-8ebf-3673962b1f4a)

![5-5](https://github.com/hyeyuny/C_pg-3_group-notes-note-1/assets/144858340/5c7a4b0c-e628-4147-8e62-7e8d1ecdd3d0)

</aside>

실행을 해봤더니 빌드는 되지만 우리가 원하는 값 뿐만 아니라 원하지 않았던 다음 case의 값까지 다 출력이 되는구나. switch~case문을 쓸 때는 꼭 break문을 써야겠다.
