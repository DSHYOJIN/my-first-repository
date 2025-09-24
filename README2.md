# AIFFEL Campus Online Code Peer Review Templete
- 코더 : 김효진.
- 리뷰어 : 임성현.


# PRT(Peer Review Template)
- [x]  **1. 주어진 문제를 해결하는 완성된 코드가 제출되었나요?**
    - 문제에서 요구하는 최종 결과물이 첨부되었는지 확인
        - 중요! 해당 조건을 만족하는 부분을 캡쳐해 근거로 첨부
        - import random

class Account:
    bank = "모두은행"
    cnt = 0
# > original
## > 내가
## 배운점: 전역변수를 사용함으로써 좀 더 객체 지향 프로그램이 되었음
## 부모-자식 class 상속받을 때 귀찮게 많이 안써도 됨. cnt 로 연결되어있어서 ㄱㅊ
## bal = 0 이라고 해줌으로써 숫자가 들어올 수 있게!
    def __init__(self, name, bal=0):
        self.name = name
        self.bal = bal
        self.num = f"{random.randint(100,999)}-{random.randint(10,99)}-{random.randint(100000,999999)}" ##여기서 나는 오류가 났던 게 :3 / :2 / :6 번 반복하고 싶다고 써서 수백가지의 숫자가 나옴..
        self.in_cnt = 0 # 몇 번 입금했나.
        self.hist = []  # 입출금 기록

        Account.cnt += 1  # 계좌 개수.

    def dep(self, amt): #입금
        if amt < 1:
            return
        self.bal += amt
        self.in_cnt += 1
        self.hist.append(("입금", amt, self.bal)) ## amt

        if self.in_cnt % 5 == 0:
            interest = int(self.bal * 0.01)
            self.bal += interest
            self.hist.append(("이자지급", interest, self.bal))


    def wd(self, amt):
        if amt <= self.bal:
            self.bal -= amt
            self.hist.append(("출금", amt, self.bal))

        else:
            print('잔고가 부족해요') # 굳이 append안함. 조건에 없어서.
            self.hist.append(("출금실패", amt, self.bal))
            self.active = False


    @classmethod
    def get_account_num(cls):
        return cls.cnt

    def history(self):
        for i, h in enumerate(self.hist, 1):
            print(f"{i}회: {h[0]} 금액:{h[1]} 잔액:{h[2]}") ## 계좌내역!!

    def reset_account(self):
        self.bal = 0
        self.in_cnt = 0
        self.hist = []
    
- [x]  **2. 전체 코드에서 가장 핵심적이거나 가장 복잡하고 이해하기 어려운 부분에 작성된 
주석 또는 doc string을 보고 해당 코드가 잘 이해되었나요?**
    - 해당 코드 블럭을 왜 핵심적이라고 생각하는지 확인
    - 해당 코드 블럭에 doc string/annotation이 달려 있는지 확인
    - 해당 코드의 기능, 존재 이유, 작동 원리 등을 기술했는지 확인
    - @classmethod
    def get_account_num(cls):
        return cls.cnt

    def history(self):
        for i, h in enumerate(self.hist, 1):
            print(f"{i}회: {h[0]} 금액:{h[1]} 잔액:{h[2]}") ## 계좌내역!!

    def reset_account(self):
        self.bal = 0
        self.in_cnt = 0
        self.hist = []

    - 주석을 보고 코드 이해가 잘 되었는지 확인
        - 중요! 잘 작성되었다고 생각되는 부분을 캡쳐해 근거로 첨부
        
- [x]  **3. 에러가 난 부분을 디버깅하여 문제를 해결한 기록을 남겼거나
새로운 시도 또는 추가 실험을 수행해봤나요?**
    - 문제 원인 및 해결 과정을 잘 기록하였는지 확인
    - 프로젝트 평가 기준에 더해 추가적으로 수행한 나만의 시도, 
    실험이 기록되어 있는지 확인
def __init__(self, name, bal=0):
        self.name = name
        self.bal = bal
        self.num = f"{random.randint(100,999)}-{random.randint(10,99)}-{random.randint(100000,999999)}" ##여기서 나는 오류가 났던 게 :3 / :2 / :6 번 반복하고 싶다고 써서 수백가지의 숫자가 나옴..
        self.in_cnt = 0 # 몇 번 입금했나.
        self.hist = []  # 입출금 기록

        - 중요! 잘 작성되었다고 생각되는 부분을 캡쳐해 근거로 첨부
        
- [x]  **4. 회고를 잘 작성했나요?**
    - 주어진 문제를 해결하는 완성된 코드 내지 프로젝트 결과물에 대해
    배운점과 아쉬운점, 느낀점 등이 기록되어 있는지 확인
    - 전체 코드 실행 플로우를 그래프로 그려서 이해를 돕고 있는지 확인
    - # > original
## > 내가
## 배운점: 전역변수를 사용함으로써 좀 더 객체 지향 프로그램이 되었음
## 부모-자식 class 상속받을 때 귀찮게 많이 안써도 됨. cnt 로 연결되어있어서 ㄱㅊ
## bal = 0 이라고 해줌으로써 숫자가 들어올 수 있게!
        - 중요! 잘 작성되었다고 생각되는 부분을 캡쳐해 근거로 첨부
        
- [x]  **5. 코드가 간결하고 효율적인가요?**
    - 파이썬 스타일 가이드 (PEP8) 를 준수하였는지 확인
    - 코드 중복을 최소화하고 범용적으로 사용할 수 있도록 함수화/모듈화했는지 확인
        - 중요! 잘 작성되었다고 생각되는 부분을 캡쳐해 근거로 첨부


# 회고(참고 링크 및 코드 개선)
```
# 리뷰어의 회고를 작성합니다.
# 코드 리뷰 시 참고한 링크가 있다면 링크와 간략한 설명을 첨부합니다.
# 코드 리뷰를 통해 개선한 코드가 있다면 코드와 간략한 설명을 첨부합니다.
