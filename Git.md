## reset과 revert의 차이는 뭔가요?

우선 둘 다 공통적으로, 과거의 커밋을 건드리는 작업입니다.  
그리고 차이점을 간단히 요약하자면, reset은 과거의 특정 commit으로 되돌아가는 과정이고,  
revert는 commit을 현재에 두면서 과거의 특정 부분들만 없애려는 과정이라고 볼 수 있습니다.

reset의 경우, 과거 commit으로 돌아가고 이후 commit 기록들은 사라집니다.  
옵션을 추가적으로 사용해줄 수도 있는데요.  
--soft 옵션을 활용할 경우 기존 파일들을 모두 보존하지만  
--mixed 옵션을 사용하면 unstaged 상태의 파일들은 보존할 수 없게 되고,  
--hard 옵션을 사용하면 과거 commit 이후 모든 파일들이 취소됩니다.

반면에 revert는 과거에서 특정 부분들만 없애고 revert 했다는 이력을 남깁니다.  
reset으로는 remote repository에 이미 push되어 있던 commit들을 조작할 수 없으니,  
이 때 revert를 사용해주면 용이합니다.  
아니면 reset을 하고 강제 push할 수도 있지만 통상적인 협업 과정에서는 revert를 사용하는 방법을  
더 권장하고 있습니다.

※ Reference : [Reset, Revert 차이 간략정리](https://youngest-programming.tistory.com/220)

<br>

## Git을 활용한 협업 과정 중 충돌이 발생하면 어떻게 해결하나요?

충돌을 해결하기 위한 방법에는 여러 가지 방법이 있을 수 있습니다.  
local main 브랜치로 pull 받아서 충돌을 직접 해결한 후 한 번의 merge로 해결할 수도 있을 것이고,  
아니면 remote main의 최신 상태를 base로 해서 내 작업 브랜치를 rebase하는 방법을 사용할 수도 있을 것입니다.  
저 같은 경우에는 rebase를 활용해서 충돌을 해결하고자 하는 편입니다.  
많은 사람이 협업하는 경우에 커밋 이력을 좀 더 깔끔하게 관리할 수 있으며,  
마치 remote의 최신 상태에서 내 작업이 이어지는 식으로 정리되기 때문에 훨씬 더 보기 편하다고 생각합니다.

※ Reference : [conflict 시 해결하는 방법](https://velog.io/@ha0kim/GIT-conflict-%EC%8B%9C-%ED%95%B4%EA%B2%B0%ED%95%98%EB%8A%94-%EB%B0%A9%EB%B2%95)
