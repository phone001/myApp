# AWS
## 포트 포워딩
## 프록시 설정 nginx
## CI/CD gitHubActions

## aws ec2 프로젝트 업로드
> git init 초기화하고 
> git remote add origin [주소]
> git pull origin master
> 유저 권한 인증
> 유저 이름 : 깃허브 이름
> 유저 비밀번호는 깃허브 프로필 누르면 설정-> 개발자 세팅 -> personal access token -> classic
> 이름과 유효시간, 권한을 설정
> 해당 토큰은 한번만 보여줌

## nodejs를 가상 서버에 설치 
> sudo apt-get update 
> sudo apt-get install -y build-essential(기본 프로그램 설치)
> sudo apt-get install curl 
> curl -sL https://deb.nodesource.com/setup_20.x | sudo -E bash --(노드의 설치파일을 다운 )
> sudo apt-get install -y nodejs

### 포트 포워딩
> 네트워크에서 외부의 포트로 요청을 보내면 재매핑해서 다른 포트로 요청을 받을 수 있도록 
> 공유기나 가상 서버에 적용을 할 수 있다.
> 80번포트로 요청을 보냈지만 3000포트로 재매핑해서 응답을 주는 것
```sh
# 추가
sudo iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 80 -j REDIRECT --to-port 3000;

# 확인
sudo iptables -t nat -L --line-numbers


#삭제
sudo iptables -t nat -D PREROUTING 1
```