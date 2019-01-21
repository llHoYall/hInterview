# Memory

## BSS (Block Started by Symbol)

초기화 되지 않은 변수, 0으로 초기화된 변수, null로 초기화한 pointer 변수 등이 저장되는 memory 공간이다.

Data 영역은 초기값을 넣어주는 공간 만큼 용량을 차지하지만, BSS 영역은 값을 넣어줄 필요가 없다. 즉 memory상 공간만 잡아놓고 실제 초기화는 하지 않는다. 어느 정도의 공간의 크기를 저장할 것이라는 정보만 저장한다. 이후 run-time에 memory를 확보한다.

## Region

RO, RW 영역은 ROM에 적재되어 있다가 boot time에 RAM으로 올라가고, ZI 영역은 ROM에 적재되어 있지 않다가 boot time에 RAM을 ZI 크기만큼 0으로 초기화를 한 후 올라간다.
