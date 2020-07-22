#[AWS]AWS EC2(Linux) + Nginx + Certbot(Let's Encrypt) = HTTPS

---

## AWS EC2 세팅

### 인스턴스 생성

1. Launch Instance 클릭

2. Amazon Linux AMI 2018.03.0 으로 생성

   - Linux 2 로 생성시 certbot 이 동작하지 않는 문제가 발생할 수 있다. 해당 인스턴스에 기본적으로 포함되지 않는 package 가 필요하기 때문에 "No package certbot available" 이라는 에러를 마주할 수도 있다. 해결 방법은 epel-release package 를 설치해주면 문제 없이 동작한다. Linux 2 로 생성을 해야 하거나 이미 생성되어 있다면 certbot 설치 전에 아래 명령어를 실행하면 된다.

   ```bash
   sudo yum -y install epel-release
   ```

3. Review and Launch 클릭 (우측 하단)
4. Secutiry Groups 에 cloud 접근과 https 허용을 위해 edit 을 클릭한다.
5. SSH 는 해당 cloud 접근 권한에 대한 설정이기 때문에 내 아이피에서만 접근하도록 설정 하는 것이 좋다.
6. Add Rule 를 두번 클릭해서 HTTP 와 HTTPS 설정을 해준다. 포트는 80 과 443 디폴트 값으로 설정되어 있고 누구나 접근이 가능해야 하기 때문에 0.0.0.0/0 으로 열어준다.
7. Launch!
8. SSH 로 접근시 Key 가 있어야만 가능하기 때문에 원하는 key 이름을 정하고 다운로드 한다.

> 주의: 한번 다운로드 받으면 다시 받을 수 없기 때문에 저장위치를 꼭 기억하자

9. 인스턴스 페이지를 확인하면 새로운 인스턴스가 생성되고 있다. 인스턴스 Name 을 설정해서 실수로 서버를 날려버리는 일을 만들지 말자.

### Elastic IPs (고정 퍼블릭 아이피)

EC2 인스턴스의 퍼블릭 아이피는 해당 인스턴스가 멈추거나 인스턴스의 상태에 따라서 유동적으로 변경되는 아이피이다. 만약 이런 아이피를 가지고 API 서버를 만들거나 도메인에 연결하게 되면 적지 않은 어려움을 겪을 가능성이 굉장히 높다. 

1. 좌측 탭 메뉴에서 Elastic IPs 페이지로 이동한다.
2. Allocate Elastic IP address 클릭
3. 이름없는 퍼블릭 IP 가 생성됐다면 해당 ip 주소를 클릭한다.

> 주의: EIP는 퍼블릭 아이피이기 때문에 한개의 AWS 계정당 5개 까지만 제공된다. 그리고 만약 어떤 인스턴스에도 associate 되지 않는다면 비용이 나가니 만들고 사용하지 않는다면 다시 release 해서 아마존에 돌려주자

4. Associate Elastic IP address 클릭
5. Resource type 을 인스턴스로 설정하고, 연결할 인스턴스를 선택한다.
6. Private IP 를 선택하고 Associate!
7. Tags 를 추가해 해당 EIP 이름을 넣어주면 된다.