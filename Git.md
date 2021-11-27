## reset과 revert의 차이

우선 둘 다 과거의 커밋을 건드리는 작업이다.  
그리고 차이점을 간단히 요약하자면, reset은 과거의 특정 commit으로 되돌아가는 과정이고,  
revert는 commit을 현재에 두면서 과거의 특정 부분들만 없애려는 과정이라고 볼 수 있다.

<br>

reset의 경우, 과거 commit으로 돌아가고 이후 commit 기록들은 사라진다.  
--soft 옵션을 활용할 경우 기존 파일들을 모두 보존하지만  
--mixed 옵션을 사용하면 unstaged 상태의 파일들은 보존할 수 없게 되고,  
--hard 옵션을 사용하면 과거 commit 이후 모든 파일들이 취소된다.

<br>

반면에 revert는 과거에서 특정 부분들만 없애고 revert 했다는 이력을 남긴다.  
reset으로는 remote repository에 이미 push되어 있던 commit들을 조작할 수 없으니,  
이 때 revert를 사용해주면 용이하다.

<br>

아니면 reset을 하고 강제 push할 수도 있지만 협업에 있어서는 revert를 사용하는 방법을 더 권장한다.
