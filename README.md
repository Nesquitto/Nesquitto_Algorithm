# Algorithm
CodeSpace로 Algorithm을 공부하고자 기존 레포를 변경했습니다.
230201 기준으로 python 권고사항에 따라서 명명 방식을 통일하고자 합니다.

## Type에 따른 명명 방식(python 권고사항)
| Type | Public | Internal |
| :--- | :--- | :--- |
| Packages | `lower_with_under` |  |
| Modules | `lower_with_under` | `_lower_with_under` |
| Classes | `CapWords` | `_CapWords` |
| Exceptions | `CapWords` |  |
| Functions | `lower_with_under()` | `_lower_with_under()` |
| Global/Class Constants | `CAPS_WITH_UNDER` | `_CAPS_WITH_UNDER` |
| Global/Class Variables | `lower_with_under` | `_lower_with_under` |
| Instance Variables | `lower_with_under` | `_lower_with_under` |
| Method Names | `lower_with_under()` | `_lower_with_under()` |
| Function/Method Parameters | `lower_with_under` |  |
| Local Variables | `lower_with_under` |  |



## 다시 풀어야할 문제
> 1874(221208), 1966(221210), 1654(221211), 17626(230129), 2606*(230129), 1260(230130), 11724(230131), 1541(230131), 1780(230201), 2178(230202)

## 복기할 사항

### ~221018
> 10951
> - 끝내는 조건이 없는 경우 -> try except 사용

### 221029
> 7568
> - 그냥 자신보다 큰 rank인 사람이 몇명인지만 파악하면 되는 문제

> 1920
> - 이진탐색 관련문제, end = mid-1, start = mid+1 식으로 바뀌어야 한다는것

### 221208
> 11651
> - 2개의 기준으로 리스트를 정렬하는 방법
> > sorted(listName, key= lambda l:(l[0], l[1]))
> > (l[0], l[1]) 부분이 핵심 

> 1874
> - 무식하게 리스트를 때려넣으면 안될거같지만 기껏해봐야 10만개이기 때문에 가능하긴 하더라...
> - "수열이 이전 숫자보다 크면 그 숫자까지 입력하고 pop, 이전 숫자보다 작으면 지금까지 push된 리스트의 가장 마지막 숫자가 수열에서 원하는 숫자인지 확인. 만약 아니라면 잘못된 수열." 이라는 규칙을 찾아내면 풀 수 있는 문제이다.

### 221210
> 2805
> - 이진탐색으로 벌목 가능한 최대 높이 찾는 방법
> > 마지막에 print(end)를 하면 가능한 최대높이를 구할 수 있음
> - python3 으로하면 시간초과가 나오니 Pypy3으로 하자
> - 이진탐색은 end-1, start+1로 점점 좁혀나가는거라고 기억하자

> 1966
> - 시간복잡도를 잘 계산해야한다. 최대로 계산했을 때 어느 방향이 가장 쉽고 단순하게 구현할 수 있을지...
> - List의 pop과 del의 시간복잡도는 (n)으로 같기 때문에 무엇을 사용해도 상관은 없다.
> - 조건을 잘 분석하고 분기를 잘 만들어야한다. 생각만으로 풀기에는 한없이 복잡해져가는 풀이가 만들어질 수 있다. 주의!

> 10816
> > print(' '.join(map(str, result))) 부분 확인하기
> 리스트를 공백 없이 출력하는 방법이니 숙지하고 있자

### 221211
> 1654
> - 문제 조건으로 인해 나누는 값에 mid가 들어갈 수 있는데 mid가 0이면 zero division error가 뜬다. 해당 요소를 예외처리 해주어야한다.
> - 이진탐색은 항상 계속 풀어줘야할것 같다. 생각보다 신경써야할 부분이 너무 많다.

> 2108
> round(n): n의 자리에서 반올림한다. default = 0
> Counter: collection에 포함되어있다. 리스트의 값들을 각각의 값들이 몇 번 나왔는지 확인할 수 있다. most_common과 같은 많이 존재한 값들 순으로 정렬하는 함수도 존재한다.
> 시간복잡도가 python3으로 하면 어렵다. pypy3으로 하자

### 221213
> 1764
> - 문제가 두 가지 조건을 모두 만족하는 사람을 출력하는 것이기 때문에, set의 intersection이라는 교집합 함수를 이용하면 편할 것 같았다. 시간초과도 이게 제일 안전할거같았고... 집합을 사용했다는 것을 기억하자

### 230124
> 11047
> - 탐욕 알고리즘 문제이다. 앞의 선택이 이후의 선택에 영향을 주지 않는다는 것이며, 최적 부분 구조 조건은 문제에 대한 최적해가 부분문제에 대해서도 역시 최적해라는 것이다.
> - 그리디에 해당하는 종류의 문제는 많지 않으니 기억해두자.

### 230126
> 2579
> - dp 문제다. 어느정도 감이 남아있기는 한데... 런타임 에러를 많이 만들었다! 값을 경계값을 넣을 때 직접 실행을 해보도록 하자! 흐아아ㅏ아

> 11723
> - set 구현하는 문제이지만, 이미 set이 구현되어있기 때문에 해당 함수를 이용하여 문제를 풀었다. 주의해야할 점은 set의 remove는 삭제하려는 값이 있어야지만 삭제가 되고, 없다면 keyError를 반환한다는 것이다. 이 KeyError를 딕셔너리의 Key로 헷갈려서 삽질할 수도 있으니 해당 remove 함수는 기억하고 있자.

### 230129
> 17626
> - dp 문제로 볼 수 있다고 한다. 잘 이해는 안가지만 암튼 그렇다고 하니 이후에 풀 때에는 그렇게 풀어보자. 한번 더 봐도 이해하기 어렵다. 아 ㅋㅋ
> - 처음 풀 때에는 브루트포스로 풀었는데, 예외조건을 몇가지 걸어주고나니 시간초과 없이 잘 동작하는것을 확인할 수 있었다. 범위가 나름 좁아서 모두 해도 가능은 하다.

> 2606
> - 정말정말 오랜만에 풀어보는거같은 그래프문제이다. 뭔가 bfs로 야매로 푼거같지만 어쨋든 풀었으니 된게 아닐까...?
> - 처음에 했을 때 시간초과가 뜬것을 시작으로... 삽질이 시작되었다. 처음에는 모든 간선을 계속 돌아보면서 확인하도록 했는데, 시간초과가 뜨길래 어 간선 확인 횟수가 너무 많은가? 라는 생각을 하게 되었고, 결론적으로 맞는 생각이었지만... 이걸 줄인 방법이 옳지 못한 방법이었다고 생각한다.
> - 해결하기 위한 첫 번째 방법으로 체크하면서 필요없어지는 간선은 그때그때 remove로 삭제해주었는데, 이 방법의 문제점은 for문을 통해서 리스트를 탐색하고 있는데 이때 remove로 삭제를 해버리면 이후에 탐색할 간선이 한칸씩 앞으로 당겨지기 때문에, 다음 탐색은 원래 순서의 다음이 아닌, 다다음 순서로 가게 된다는것이었다. (삭제된 인덱스로 원래 순서의 다음이 들어오기 때문에...)
> - 그래서 이걸 다음으로 해결하기 위한 또 다른 방법을 생각했는데, 한번 탐색을 돌리면서 삭제할 구간의 인덱스를 저장하고 전부 돌린 이후에 인덱스를 참고해 삭제한다. 라는 방법인데... 이것도 깊게 생각하지 않아 문제가 있었다. 첫 번째 방법에서 발생한 간선이 당겨지는 문제는 해결했지만, 삭제할 인덱스의 모음들이 있는 상태에서 하나씩 삭제해 나가면 삭제할 때마다 뒤의 데이터가 한 칸씩 당겨진다는걸 깜빡해버린 것이다. 이 때문에 인덱스 범위 초과 에러가 발생했다.
> - 마지막으로 이걸 그냥 해결해버리려고 삭제할 인덱스 모음을 큰 순서대로 정렬해서 큰것부터 삭제를 해버렸다. 이게 깔끔한 해결책은 아니지만 일단 문제를 풀었으니 한 고비를 넘겼다... 라고 생각을 해야겠다. 이후에 한번 더 풀날이 온다면 그때는 그래프 이론을 어느정도 더 많이 체득하여 쉽게쉽게 푸는 내가 되었으면 좋겠다.

### 230130
> 1260
> - dfs bfs 구현문제, 순서대로 출력하는거라 sort를 할건지 어디서 할건지에 대한 생각이 필요한게 약간 변수이긴 하지만, 몇번 더 풀어보면서 dfs bfs 구현방법을 확실하게 각인시키는게 중요하다고 봄.

### 230131
> 11724
> - def로 풀었다. 시간초과의 지옥에 빠진 문제이다. 시간초과가 계속 날 경우에 확인할 방법은 일단 내가 사용한 함수중에 시간복잡도가 긴 것이 있는지 확인하고 아무리 봐도 없는거같으면 불필요한 과정이 들어간 것이라고 생각해야한다. 이번 문제또한 계속 시간초과가 나길래 뭐가문제지? 생각했는데, 나름대로 제한조건을 걸어서 최대한 효율적으로 작성했다고 생각했는데, while문 안에서 이미 방문한 노드가 stack에 또 들어갈 것이라는 생각을 못해서 해당 노드가 수없이 들어가서 시간을 늘려서 초과가 났었다. 이후에 다시 한번 풀고 시간복잡도 제대로 잡자.

> 1541
> - 반례를 몇개 찾아가면서 풀었는데, 이게 제대로 된 풀이는 아닌것 같다. 뭔가 더 현명하고 깔꼼하고 펀하고 쿨하고 섹시한게 있을거같은데... 지금은 생각이 안난다. 나중에 한번 더 풀어보고 다시 생각해보자.

> 18870
> - 진짜 무식하고 더럽게 풀긴 했는데, 이것도 아슬아슬하지만 시간초과에 안걸리더라..?
> - 셋으로 중복 제거하고, 중복없는 값들을 크기비교해서 딕셔너리에 값으로 순위 정렬하고 원래 리스트를 돌면서 딕셔너리의 값을 불러오는게 생각하기 쉬운 방법이었던것 같다. 나빼고 다 그렇게 품... ㄷㄷ 근데 뭐 나도 이거 시간복잡도 계산해서 어 될거같은데 생각해서 된거니까 이것도 옳은 풀이지 음음

### 230201
> 2630
> - 오랜만에 재귀로 문제를 풀어보니 함수의 인자로 어느것을 보내줘야할지 감이 잘 안잡혔다. 더군다나 2차원 배열의 slicing도 numpy가 없으면 안된다는것도 까먹고 있었었고... 재귀를 계속 풀어보다보면 익숙해지고 빨라지겠지만 재귀에 대한 감이 거의 사라졌다는걸 깨달은 날이었다.

> 1780
> - 2630의 심화버전인데... 시간초과에서 너무나도 많이 해맸다. 음~ 결국은 확 줄일 수 있는 방법을 찾긴 했는데... 바꾸기 전 코드를 주석으로 달았으니 다시 풀 때 확인해봐도 된다. 너무 철저하게 확인을 하려 한 나머지 당연한것도 확인을 해버렸으니 시간초과가 날 수밖에...

### 230202
> 2178
> - 와 진짜 처음부터 잘못 생각하고 있었다. dfs가 깊게 들어가니까 최단거리를 짧게 잡겠지? 하면서 했었는데, 최단거리를 구하는것은 bfs였던 것이다! dfs를 구현 다 하고 어 왜 시간초과가 뜨지? 하면서 생각해본 순간의 내가 깨달은 내용이다.
> - 나름 쉬운 문제였는데, 이런 문제를 풀어본적이 정말 오랜만이라 약간 테크니컬하게 푸는 방법을 까먹었었다. 다음에 다시 이런 문제를 풀게되면 꼭 상기시켜보자.

### 230203
> 1931
> - 그리디 알고리즘의 진짜 기본적이고 대표적인 문제... 라는걸 이름만 보고도 딱 알았다.
> - 근데 문제를 풀다가 반례를 하나 못찾아서... 몇번 틀렸는데! 으아ㅏ아ㅏ
> - 끝나는 시간이 같을 경우에 정렬 관련해서 문제가 발생할 수 있다는 것을 깨달았다. 이럴수도 있구나...! 그래서 두 종류의 키를 기반으로 정렬하는 방법을 사용했고 해당 방법을 다시 머리에 새길 수 있었다.

> 1697
> - 와 DP로 풀 수 있을 줄 알았는데, 최단거리에는 BFS도 있었다. 어쩐지 DP로 풀기에는 수식이 안나오더라니... BFS면 되는구나... 오류는 그냥 무식하게 인덱스 초과라 인덱스를 200000까지 늘리도록 해서 메모리로 찍어 눌렀다. 최대로 접근하는 인덱스는 찾아보면 나오겠지만 그건 너무 귀찮고 메모리는 충분하기 때문에 그냥 했다. 음음

> 11403_fail
> - 와 한시간을 잡았는데, 무슨 문제인지는 모르겠지만 70퍼에서 더이상 올릴 수가 없다... 24시 전까지 끝내려고 했는데, 이렇게 못끝낼줄은... 흐아아아ㅏㅏ아ㅏ
> - 푸는 방식을 처음부터 다시 생각해봐야 할 것 같다. 진짜 그냥 이러면 되겠지 식의 마인드로 풀다보니 이런 문제가 발생한 것 같다. 11403_fail이라고 이름을 변경하고 내일은 11403을 새로 만들어서 새로 풀어봐야겠다. 한시간을 봤는데, 못풀어서 기분이 별로지만... 내일의 나는 풀 수 있다!
> - DFS로 해야할지, BFS로 해야할지부터 생각해나가야겠다.