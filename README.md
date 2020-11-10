# COMP312-OperatingSystem-2020
운영체제의 핵심 기능과 알고리즘에 대한 사례를 배운다. 특히 프로세스 및 스레드 관리, 메모리 관리, I/O 장치 관리 및 파일 시스템등을 다룬다.    
또한, 리눅스 운영체제를 익히고 리눅스 기반으로 실습을 진행한다. 






### 1. Multi-Thread
> 1. int number[100]를 공유 변수로 설정한다. 초기값을 모두 0으로 한다.  
> 2. Process는 10개의 thread 연속적으로 생성한다.(for loop 이용). 
> 3. 각 thread는 다음과 같은 일을 한다.  
> thread i ( 0 <= i <= 9 ) : random() 함수를 이용해서 0에서 99 사이의 수 X 를 생성하고, number[X] 값을 1 증가 시킨다 (각 thread는 동일한 과정을 100,000번 수행). 동시에 thread I 에서 발생한 각 수의 발생 빈도 와 각 수의 발생 빈도의 합 을 구한다.   
> 4. 10개의 thread가 종료되면 process는 number[100]에 있는 각 수의 발생 빈도 와 이들의 총합 을 파일에 출력한다. 10개 thread에서 구한 결과 값 (각 수의 발생 빈도 와 각 수의 발생 빈도의 합 )을 각 thread별로 출력한다. 그리고 10개 thread에서 집계한 각 수의 발생 빈도를 각 수 별로 더해서 그 결과를 출력하고, 이들이 총합도 출력한다.  
> 5. random number를 생성하기 위한 seed는 시간을 이용한다 (즉, random() 함수의 매번 수행 시 다른 seed를 사용한다).  
> 6. 모든 결과는 result.dat 파일로 출력한다.  
> 7. 위과정을3번이상수행하고그결과를비교한다.  



### 2. 병렬 파일 저장
: 2 processes를 생성해서 한 process는 file server 역할을 하고, 다른 한 프로세 서는 client 역할을 한다. server는 client가 요청한 일을 수행하고, client는 사용 자의 명령을 받아서 server에게 전달한다.
> 1. Client는 disk에 저장된 특정 파일(20M 정도의 파일)을 file server에게 n개 의 새로운 파일에 나누어 저장하도록 요청을 한다.
> 2. 저장 요청은 사용자가 client에게 직접 요청하도록 한다.
> 3. 예) store temp.dat paratemp.dat –5 (temp.dat 파일을 5개의 새로운 파 일에 저장하고 병렬로 저장된 파일의 이름을 paratemp.dat로 기억한다.)
> 4. File server는 파일의 크기를 확인해서 n개의 블록으로 나누고, 각 블록을 disk에 새로운 파일명으로 저장한다. 이때, n개의 블록은 n개의 thread에 의 해 각각 병렬로 저장된다.
> 5. File server는 자신이 저장한 파일에 대한 정보를 지속적을 보관해서 향후 읽 기 요청 시에 적절한 대응을 하도록 해 준다. 프로그램을 새로 수행시키더라 도 이미 저장된 파일을 읽을 수 있도록 해야 한다.
> 6. File server는 별도의 메타데이터 파일을 관리한다. 메타데이터 파일의 내용은 저장 된 파일들에 대한 정보, 즉 통합된 파일명, 전체 파일 크기, 나누어진 파일 수, 나누어 진 파일 이름 등 이다. 나누어진 파일 이름은 겹치지 않게 생성해야 한다.
> 7. 사용자가 읽기를 요청을 하면 그 파일이 병렬로 저장된 파일일 경우는 읽어서 지정 된 파일에 저장을 하고, 없는 경우는 “파일이 없음” 메시지를 출력한다.
> 8. 예) read paratemp.dat restore.dat (paratemp.dat를 읽어서 restore.dat에 저장 한다.)
> 9. File server에 저장된 파일의 리스트를 출력하여 client에서 저장된 파일의 목록을 확 인 할 수 있다.
> 10. 파일명은 특정 directory의 파일의 지정이 가능해야 됨
> 11. 작성 프로그램, 프로그램의 실행 과정에 대한 상세 설명(각 함수 별, 혹은 line-by-line 별), 수행 결과, 프로그래밍 수행 과정에서 생긴 일들 및 최종 결과에 대한 느낌의 감상 문을 작성해서 제출하세요.

두번째 실습은 끝까지 다 완수하지는 못했지만, 전체 흐름을 간단한 코드로 구현했다.













  
    
    
