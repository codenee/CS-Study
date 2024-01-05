# Part 3-1 Windows
- [Part 3-1 Windows](#part-3-1-Windows)
   - [윈도우 커널](#Windows-Kernel)
   - [윈도우 계정과 권한](#윈도우-계정과-권한)
   - [윈도우 인증과 패스워드](#윈도우-인증과-패스워드)
   - [PE 포맷](#PE-포맷)
   - [논페이징 풀, 페이징 풀](#Nonpaged-Pool,Paged-Pool)

</br>

[back](https://github.com/codenee/CS-Study)


## Windows Kernel
* [Windows Kernel 설명](https://code-space.tistory.com/111)


</br>

## 윈도우 계정과 권한
* 기본 사용자와 그룹
  * Administrator : 관리자 권한의 계정으로 사용자가 사용 가능한 계정 중 가장 강력한 권한을 가진다.
  * SYSTEM : 시스템에서 최고 권한을 가진 계정으로 로컬에서 관리자보다 상위 권한을 가진다. 원격 접속이 불가능하며, 사용자가 이 계정을 사용하여 로그인 할 수 없다.
  * Guest : 매우 제한적인 권한을 가진 계정으로, 기본 설정은 사용 불능이다.
  * System > Admin > Authenticated Users > User > Guest
* SID
  * 윈도우의 각 사용자나 그룹에 부여되는 고유한 식별번호
  * whoami, user 명령을 이용해 로그인한 사용자의 SID를 확인할 수 있다.
  * 유닉스/리눅스의 UID, RUID, EUID와 유사한 개념이다.
  * S-1-5-21-1801674531-839522115-1708537768-500
     * S : SID
     * 500 : 관리자 ( Guest = 501, 일반 사용자 = 1000이상)

[Up](#part-3-1-Windows)

</br>

## 윈도우 인증과 패스워드
* LSA (Local Security Authority)
   * 모든 계정의 로그인에 대한 검증 시스템 자원 및 파일 등에 대한 접근 권한 검사
   * 로컬, 원격 모두에 해당
   * 이름과 SID를 매칭하며 SRM이 생성한 감사 로그를 기록하는 역할
   * NT보안의 중심요소이며, 보안 서브 시스템(Security Subsystem)이라 불리기도 함
* SAM (Security Account Manager)
  * 사용자/그룹 계정 정보에 대한 데이터베이스를 관리
  * 사용자의 로그인 입력 정보와 SAM데이터베이스 정보를 비교해 인증 여부를 결정
  * 사용자의 계정과 패스워드의 일치 여부를 확인하여  SRM에 알린다.
* SRM (Security Reference Monitor)
  * SRM은 인증된 사용자에게 SID를 부여
  * SID에 기반하여 파일이나 디렉터리에 대한 접근 권한을 결정하고 이에 대한 감사 메시지를 생성 

[Up](#part-3-1-Windows)

</br>

## PE 포맷
* PE (Portable Executable)은 윈도우 운영체제에서 사용되는 실행 파일을 뜻하며 대표적으로 exe파일이 있다.
* 윈도우 로더가 실행 가능한 코드를 관리하는데 필요한 정보를 캡슐화한 데이터 구조체이다.
* MS에서 다른 운영체제와 이식성을 좋게 하기위해 만든 파일 포맷.
* 실행 파일이 적재되는 가상주소, Import/Export API목록, 코드, 데이터 등의 정보를 관리하기 위해 파일 첫 부분에 여러 가지 구조체로 구성되어 있다.
* PE파일에서 IMAGE_SECTION_HEADER에는 각 섹션의 위치와 크기 등의 정보를 포함한다.
* IMAGE_SECTION_HEADER (PE파일의 세션 헤더)
   * 각 세션 데이터를 메모리에 로딩하고 속성을 설정하는데 필요한 정보를 담고 있다. 섹션은 PE파일이 가상 주소 공간에 로드된 이후 프로그램 실행 코드, 데이터, 리소스 등 프로그램 실행에 필요한 정보를 배치한 영역을 말한다.
   * 주요 섹션 이름과 데이터 유형
        * .text : 프로그램 실행 코드를 담고 있는 섹션
        * .data : 읽기 쓰기가 가능한 데이터 섹션으로 전역변수와 정적변수 등이 위치
        * .rdata : 읽기 전용 데이터 섹션으로 상수형 변수, 문자열 상수 등이 위치
        * .bss : 초기화되지 않은 전역변수가 위치
        * .idata : Import할 DLL과 그 API/함수들에 대한 정보를 담고 있는 섹션
        * .edata : Export할 DLL과 그 API/함수들에 대한 정보를 담고 있는 섹션
        * .rsrc : 다이얼로그, 아이콘, 커서 등의 윈도우 애플리케이션 리소스 관련 데이터를 담고 있는 섹션
          
* 프로그램이 사용하는 API나 어느 메모리주소에 파일이 로딩되는지 알 수 있기 때문에 사용한다.
  
</br>

* 참고
  * 실행 파일을 이해하면 -> 
    운영체제의 메모리 관리 기법을 이해할 수 있음 ->
    운영체제의 프로세스 관리 기법을 이해할 수 있음 ->
    실행 파일을 이해해야 "프로그램 분석"이 가능
  * 운영체제별 형식
     * 윈도우 : PE (Portable Executable)
     * 리눅스 : ELF (Executable and Linkable Format)
     * 맥 : Mach-O (Mach Object file Format)

</br>

* 참고 블로그
[PE구조](https://jeongzero.oopy.io/ea359704-1d23-479f-96b0-ac4014c0cda5) , 
[악성코드 분석 PE](https://rednooby.tistory.com/33)

[Up](#part-3-1-Windows)

</br>

## Nonpaged-Pool,Paged-Pool
* Page
  * 윈도우에서 페이지의 의미는 가상 메모리를 사용하는 최소 크기 단위를 의미.
  * 윈도우에서 페이지라는 단어가 들어가는 용어는 가상화에 관련된 의미로 사용된다.
  * Paged-Pool : 가상화되어 관리되는 공간
  * Nonpaged-Pool : 가상화 되지 않고 관리되는 공간
* Memory Pool
  * 운영체제 및 장치 드라이버가 데이터 구조를 저장하는데 사용하는 메모리 리소스 역할을 한다.
  * Nonpaged-Pool과 Paged-Pool로 구성.
  * 메모리 풀 관리자는 시스템의 가상 주소 공간 영역을 사용하여 커널 모드에서 작동.
    
# Nonpaged-Pool
* 커널 및 장치 드라이버는 시스템이 페이지 폴트를 다룰 수 없는 상황에서도 접근할 수 있는 데이터를 저장하기 위해 항상 실제 메모리에 물리적으로 존재하는 Nonpaged-pool을 사용한다.
* Nonpaged-pool에 저장된 일반적인 시스템 데이터 구조에는 프로세스 및 스레드를 나타내는 커널 및 개체, 뮤텍스, 세마포어 및 이벤트와 같은 동기화 개체, 파일 개체로 표시되는 파일 참조 및 I/O요청 패킷(IRP)이 포함된다.

# Paged-Pool
* 가상화된 메모리를 사용할 수 있다는 점에서 Nonpaged-pool가 다르다.
* Paged-Pool을 사용하는 대표적인 경우는 레지스트리 키 및 기타 레지스트리 데이터 구조에 대한 참조를 저장할때이다.(Paged-Pool의 사용량이 가장 큰 요소는 일반적으로 레지스트리이다)
* 내부적으로 섹션이라고 하는 메모리 매핑된 파일을 나타내는 데이터 구조도 페이징 풀에 저장된다.


* 참고 블로그
  [비페이징풀과 페이징풀](https://brunch.co.kr/@leedongins/78)

[Up](#part-3-1-Windows)

</br>
