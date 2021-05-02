# 마이크로서비스 패턴(길벗, 2020) - Microservices Patterns

- 실습 관련 내용은 '한국어판 부록'을 참고하세요.
- 높은 사양의 PC가 필요합니다(i7계열의 메모리 16GB 이상 권장).


# 실행 권한 조정

```sh
chmod a+x *.sh gradlew
find . -name '*.sh' -exec chmod a+x {} \;
```

# 빌드

```sh
# 디펜던시 설치
./build-contracts.sh

# 도커 컨테이너에 배포할 jar 만들기
./gradlew assemble
find . -name "ftgo-*.jar"
```

# 도커 컴포즈 실행
get-pip 를 python2.7 용으로 url 수정

```sh
# DOCKER_HOST_IP 설정
. ./set-env.sh

docker-compose up -d

docker ps
```

컨테이너의 상태가 계속 unhealthy 이면, docker 의 cpu, memory 를 4core, 4096MB 으로 늘려준다

# 스웨거 접속
`
소비자 생성: http://localhost:8081/swagger-ui.html
음심점 생성: http://localhost:8084/swagger-ui.html
주문 생성/조회: http://localhost:8082/swagger-ui.html
주문 이력 조회: http://localhost:8086/swagger-ui.html
`

# 도커 컴포즈 종료
```sh
docker-compose down -v
```

# troubleshooting

1. dynamodblocal 실행시 아래의 에러 발생시

    `
    Unsupported major.minor version 52.0
    `

    aws 의 dynamodb-local 도커 이미지를 실행하게 변경 
