# 마이크로서비스 패턴(길벗, 2020) - Microservices Patterns

- 실습 관련 내용은 '한국어판 부록'을 참고하세요.
- 높은 사양의 PC가 필요합니다(i7계열의 메모리 16GB 이상 권장).


# 실행 권한 조정

```sh
chmod a+x *.sh gradlew
```

# 빌드

```sh
# 디펜던시 설치
./build-contracts.sh

# 도커 컨테이너에 배포할 jar 만들기
./gradlew assemble
find . -name ftgo-*.jar
```

# 도커 컴포즈 실행
get-pip 를 python2.7 용으로 url 수정

```sh
# DOCKER_HOST_IP 설정
. ./set-env.sh

docker-compose up -d
```