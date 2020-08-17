리눅스 가장 기본적인 보안

ssh(22포트) 를 접속할때 비밀번호가 아닌

암호키로 접속하는 방법

해당 유저의 홈폴더에서 ssh-keygen -t rsa -b 4096 입력
그리고 엔터엔터 엔터 계속 누르다보면 .ssh폴더 만들어져있음

그럼 .ssh/id_rsa.pub 파일의 내용을 .ssh/authorized_keys 파일로 복사해주면

그다음부턴 비밀번호 없이 id_rsa 파일로 로그인 가능





그리고 ssh는 비밀번호로는 접속못하게하기위함
vi /etc/ssh/sshd_config

공개키인증
PubkeyAuthentication yes

root 패스워드 로그인 금지하고 공개키 인증으로만 로그인
PermitRootLogin without-password

root로는 아예 SSH로그인을 할 수 없다. (추천사항)
PermitRootLogin no

패스워드로는 아예 로그인 못하게 설정
PasswordAuthentication no

지정한 사용자만 SSH로 로그인 가능하게 설정
AllowUsers mysshuser