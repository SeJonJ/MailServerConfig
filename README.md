## Dovecot + Postfix + mysql 연동을 위한 설정 파일 및 세팅 방법

보다 자세한 구축 방법은 https://terianp.tistory.com/ 에서 
[메일 서버 구축하기 dovecot, postfix] 내용 확인 부탁드립니다.

0. 메일 서버 관리 계정 설정 정보는 다음과 같습니다.
- vir_mailbox
- dovecot, /var/mail/ 디렉토리에 대한 권한을 갖고 있어야 합니다.

1. dovecot

- dovecot 은 dovecot 폴더 안 파일들을 확인하시며 세팅하시면 됩니다.

- SSL 적용을 한다는 가정하에 만들었습니다. 만약 SSL 사용을 안하신다면 10-auth.conf , 10-ssl.conf 파일 확인하여 수정 하셔야합니다.

- 기본적으로 고쳐야하는 파일은 아래와 같습니다. 만약 에러가 나거나 하는 경우만 다른 파일을 확인하시면 될 것 같습니다.

1) /etc/dovecot

dovecot.conf
dovecot-sql.conf.ext

2) /etc/dovecot/con.f

10-auth.conf
10-mail.conf
10-master.conf
auth-sql.conf.ext


2. postfix

- postfix 에서 고쳐야하는 파일은 아래와 같습니다. postfix 는 dovecot 과는 다르게 에러가 나면 거의 90% main.cf 와 master.cf 문제입니다. 이에 해당 두 파일만 확인하셔도 충분합니다.

1) master.cf , main.cf

- virtual 설정을 위해서 관련 해당 디렉토리나 혹은 다른 곳 안에 virtual_domains_maps.cf 와 virtual_mailbox_maps.cf 가 필수로 존재해야합니다. 본인은 /etc/postfix/mysql 안에 넣어두었습니다.

3. Mysql

- sql query 문을 넣어두었습니다. 잘 확인하시어 DB와 table 추가만 하시면 됩니다. 

