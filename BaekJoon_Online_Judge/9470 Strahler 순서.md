이 문제는 주어진 하천 입력의 Strahler 순서를 알고 싶은 문제이다.
Strahler 순서는 다음과 같이 구할 수 있다.

● 강의 근원인 노드의 순서는 1이다.<br></br>
● 나머지 노드는 그 노드로 들어오는 강의 순서 중 가장 큰 값을 i라고 했을 때,
들어오는 모든 강 중에서 Strahler 순서가 i인 강이 1개이면 순서는 i, 2개 이상이면 순서는 i+1이다.

처음에 이 문제를 보고 다익스트라도 아닐꺼 같고 플로이드 워셜도 아닌거 같고 트리도 아닌거
같았다 문제 그림이 약간 트리 뒤집은거 같긴한데.. 방향이 자식이 부모를 참조하는거 같은
형상이고 무엇보다 6번 노드같이 바로 7번 노드로 건너뛰는 간선이 존재해서 트리는 확실히
아닌거 같았다. 아무튼 문제가 특이해 보여서 호기심이 생겼다.<br></br>
먼저 든 생각은 리프노드? 즉 참조 되는 애들이 없는 애들 부터 큐에 담아서 Strahler순서를 
최신화 해 나가면 되겠다고 생각했다. 여기서 관건이 만약 어떤 노드가 다른 노드를 참조하고 있고,
이 어떤 노드가 큐에서 pop되어 다른 노드를 방문 했을 때 이 다음 방문 노드에 아직 다른
노드들이 참조하고 있으면 qu에 담는 것이 곤란했다. 왜냐하면 다른 참조 노드로 인해 이 노드의
Strahler 순서가 바뀔 수가 있고 이렇게 되면  이 노드의 아래의 이후 방문할 노드에도 영향이 
미친다. 따라서 이 노드는 방문했다고 바로 qu에 넣는 것이 아닌, 모든 참조가 끝나면 이 노드의
Strahler 순서는 변동이 없게 되므로 그제서야 qu에 넣는 방법을 쓰면 될거 같았다. <br></br>따라서 
각 노드별로 자기를 참조하고 있는 노드를 count하는 리스트를 따로 선언했다. 그리고 qu에서
pop된 노드가 참조하고 있는 다음 노드의 참조 count를 -= 1하고 -=1 했을 때 0이 되면
모든 참조가 끝난것이므로, 그제서야 qu에 넣는다 (즉, 중복 방문이 가능하다.).
Strahler 순서를 최신화 하는 방법은 생략한다.(문제에서 말한대로 구현하면 된다.)

이 문제를 풀고나서 알고리즘을 찾아보니 위상정렬이라는 알고리즘으로 푸는 문제였다.
위상정렬이 내 머리에서 나온다는게 엄청 신기했다.<br></br><br></br>


<p align="center"><img src="https://www.acmicpc.net/upload/images/strahler.png" height="300px" width="500px"></p>

<p align="center"><img src="https://upload.wikimedia.org/wikipedia/commons/thumb/e/e6/Flussordnung_%28Strahler%29.svg/525px-Flussordnung_%28Strahler%29.svg.png" height="300px" width="500px"></p>

* 그림 출처<br></br>
https://www.acmicpc.net/problem/9470<br></br>https://en.wikipedia.org/wiki/Strahler_number
