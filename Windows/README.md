# Part 3-1 Windows
- [Part 3-1 Windows](#part-3-1-Windows)
   - [윈도우 커널](#Windows-Kernel)
   - [윈도우 계정과 권한](#윈도우-계정과-권한)
   - [윈도우 인증과 패스워드](#윈도우-인증과-패스워드)

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
