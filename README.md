# 221017-java-db-integration

# java와 DB연동하기
## 1. gradle 빌드
![](https://velog.velcdn.com/images/lyj1023/post/5c1d32a0-8f4c-470c-8de0-662e9899730d/image.png)
- Gradle빌드로 프로젝트를 생성한다.

## 2. mysql dependency 추가
![](https://velog.velcdn.com/images/lyj1023/post/6c50b957-e766-44c0-8288-d1e912d87e06/image.png)
- build.gradl의 dependencies에 mysql dependency를 추가해줘야 한다.

![](https://velog.velcdn.com/images/lyj1023/post/25fcd92a-2f81-438b-b114-ee8058a81712/image.png)
- 링크: [mysql dependency](https://mvnrepository.com/artifact/mysql/mysql-connector-java) 
- 위 링크에 들어가 최신 버젼을 클릭한 후 Gradle카테고리에 있는 텍스트를 복사한다.

![](https://velog.velcdn.com/images/lyj1023/post/e6603441-e697-49ab-bd92-d2281f2bc0e6/image.png)
- 그 후 다시 build.gradl파일에 들어가 dependencies에 복사했던 텍스트를 붙여넣기한다.

## 3. mysql table 생성
- mysql workbench에서 다음과 같이 table을 생성한다.
![](https://velog.velcdn.com/images/lyj1023/post/a015c022-6838-4871-9961-0dd1ac63f19f/image.png)

## 4. add()메소드(insert)

- add()메소드: DB에 INSERT INTO를 한다.
- prepareStatement에 sql Query문을 작성하고 setString에 값을 넣어준다.
>- 주의! 절대 깃허브에 host,user,password를 직접 입력하지 말것!  
>꼭 Edit Configurations을 이용해야 한다. 그대로 올리면 해킹당할수 있음.

## 5. Edit Configurations 설정
- Environment Variable 을 로컬에서 jvm으로 전달하는 방법이다.

![](https://velog.velcdn.com/images/lyj1023/post/17cf60d0-eb26-4e7f-9e0a-0250cef9bc48/image.png)

- Edit - Configurations로 간다.

![](https://velog.velcdn.com/images/lyj1023/post/9efc9556-91a4-42cf-8d75-396c143b95ef/image.png)
- 빨간 동그라미 클릭

![](https://velog.velcdn.com/images/lyj1023/post/d7d51e1e-5542-4ed1-846b-c833cec47b87/image.png)
- DB_HOST, DB_PASSWORD, DB_USER를 추가한다.
- DB_HOST = jdbc:mysql://`aws퍼블릭 IPv4 DNS주소`:3306/`DB 스키마이름`
- DB_PASSWORD = mysql실행할때 설정했던 password를 입력한다.
- DB_USER = root

## 6. status

- 몇개의 raw가 들어갔는지 출력해준다.

## 7. SystemEnv 클래스 생성

- DB_USER, DB_HOST, DB_PASSWORD 등의 정보가 잘 넘어왔는지 확인하는 클래스 이다.

## 8. get()메소드(select)


- User의 정보를 외부에서 입력받기 위해 User클래스를 선언했다.
- UserDao2클래스에 SELECT FROM문을 출력하는 get()메소드를 만들었다.
