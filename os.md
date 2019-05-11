# OS

## Process Management

### Critical Section

다중 programming 운영체제에서 여러 process가 data를 공유하면서 수행될 때 각 process에서 공유 data를 access하는 program code 부분을 가리키는 말이다.

### Semaphore

공유된 자원의 data를 여러 process가 접근하는 것을 막는 것.

### Mutex

공유된 자원의 data를 여러 thread가 접근하는 것을 막는 것.

### Semaphore vs Mutex

1. Semaphore는 Mutex가 될 수 있지만 Mutex는 Semaphore가 될 수 없다.

	Mutex 는 상태가 0, 1 두 개 뿐인 binary Semaphore이다.

2. Semaphore는 소유할 수 없는 반면, Mutex는 소유가 가능하며 소유주가 이에 대한 책임을 진다.

	Mutex 의 경우 상태가 두개 뿐인 lock 이므로 lock 을 ‘가질’ 수 있다.

3. Mutex의 경우 Mutex를 소유하고 있는 thread가 이 Mutex를 해제할 수 있다. 하지만 Semaphore의 경우 이러한 Semaphore를 소유하지 않는 thread가 Semaphore를 해제할 수 있다.

4. Semaphore는 system 범위에 걸쳐있고 file system상의 file 형태로 존재한다. 반면 Mutex는 process 범위를 가지며 process가 종료될 때 자동으로 clean up된다.
