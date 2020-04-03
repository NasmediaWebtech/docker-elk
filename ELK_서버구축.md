
### 184 개발서버에 적용

  1. Docker 설치
    - 1. yum으로설치 (버전문제로 2로 설치)
      `$ sudo yum install -y docker docker-registry`
    - 2. Docker에서 제공하는 설치 스크립트로 설치
      `$ sudo wget -qO- https://get.docker.com/ | sh`
  2. docker version 1.13 이 설치됨
    <!-- `$ systemctl enable docker.service` - 부팅시마다 도커실행 -->
    - `$ systemctl start docker.service` - 도커 프로그램 실행
    - `$ systemctl status docekr.service` - 도커 프로그램 확인

    * docker-compose 설치
    ```s
    <!-- 다운 -->
    $ sudo curl -L "https://github.com/docker/compose/releases/download/1.25.4/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose`
    <!-- 권한 -->
    $ sudo chmod +x /usr/local/bin/docker-compose
    ```

  3. github에서 ELK스택 한번에 가져오기
    [ELK Docker-compose](https://github.com/deviantony/docker-elk#how-to-disable-paid-features)
    - `$ git clone https://github.com/deviantony/docker-elk.git`

  4.  
  SELinux를 기본적으로 활성화 한 배포판에서는 docker-elk가 제대로 시작되도록 파일 컨텍스트를 다시 지정하거나 SELinux를 허용 모드로 설정해야합니다, 예를 들어 Redhat 및 CentOS에서 다음은 적절한 컨텍스트를 적용합니다.
  `$ chcon -R system_u:object_r:admin_home_t:s0 docker-elk/`

  5. 설정파일 수정
    1. xpack 설정변경
    2. 계정, 비밀번호 개인에 맞게 변경

  6. 
    * ELK Compose 실행/정지
    `$ sudo docker-compose up`
    `$ sudo docker-compose down`

    * 데이터 싹다 삭제하고 내림 
    `$ sudo docker-compose down -v`