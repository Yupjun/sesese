# 쎄쎄쎄 Readme

* 쎄쎄쎄 대회의 목적은 현재의 Sota? 인 알고리즘 A를 이기는 코드를 짜는 것입니다.

## 현재 우승자 : Kinetic (https://github.com/Kinetic27) 
* Winrate : 100% Win rate: 100% (for FKgk B model) 


# 참여 방법
* 수정해주셔야 하는 부분은 아래의 부분입니다.

<pre><code>
# 랜덤으로 시행
def B_start(A_hist,B_hist,my_gi,enemy_gi):
    global playerA
    global playerB
    my_gi = playerB
    enemy_gi = playerA
    
    if(len(A_hist)>100 and my_gi==1 and enemy_gi==1):
        return 'pa'
    val=random.uniform(0, 1)
    if(my_gi==0):
        return ('gi' if (enemy_gi==0) else 'shield')
    elif(my_gi==1):
        return ('gi' if (enemy_gi==0 and val<=0.75) else 'pa')
    elif(my_gi==2):
        return ('gi' if ((enemy_gi>1 and val>0.5) or (enemy_gi==1)) else 'pa')
    else:
        return 'energypa'
</code></pre>

* A_hist에는 이중 리스트 형태로 A가 냈던(현재 A가 상대방입니다) 패를 알려줍니다
예를들어 A_hist[0][0]은 A가 첫번째 게임에서 처음으로 낸 패 입니다.

* B_hist에는 이중리스트 형태로 B가 냈던(현재 B가 자신입니다) 패를 알려줍니다.

예를들어 B_hist[3][5]은 A가 네번째 게임에서 6번째로 낸 패 입니다.

* my_gi는 나의 기이며 int형이고 0부터 시작합니다.

my_gi는 참조만 하시고 절대로 수정하지 마시기 바랍니다.

* enemy_gi는 상대방의 기이며 int형이고 0부터 시작합니다

enemy_gi는 참조만 하시고 절대로 수정하지 마시기 바랍니다.

* 길었지만 결론은 저 함수의 output은 "gi","shield","pa","energypa","teleport"중 하나를 반환하면 됩니다.

* "gi" ,"pa","teleport"는 기 1개 소모 , "energypa"는 기 3개 소모이므로 반드시 반환하기 전에 my_gi의 개수가 
기를 소모할 만큼 있는지 확인 후에 return 해주시기 바랍니다.

* 현재 많은 도전자들이 눈물을 머금고 돌아갔습니다. 분발하시기 바랍니다.
