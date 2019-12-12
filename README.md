# Oauth2 examples

Tutorials related to this project:

1. [Spring boot oauth2 auth server](https://howtodoinjava.com/spring5/security5/oauth2-auth-server/)

Steps to run this project to get accesssToken:

1.
After application is up hit the below endpoint in the browser and enter the userName = humptydumpty and password=123456 and click appprove in the next page.
http://localhost:8080/oauth/authorize?client_id=clientapp&response_type=code&scope=read_profile_info

2. you will be redirected to below enpoint
http://localhost:8081/login?code=szHzhi

3. now take the code in query parameter of above url and update in the below postman collection API  to get the accessToken
curl -X POST \
  http://localhost:8080/oauth/token \
  -H 'authorization: Basic Y2xpZW50YXBwOjEyMzQ1Ng==' \
  -H 'cache-control: no-cache' \
  -H 'content-type: application/x-www-form-urlencoded' \
  -H 'postman-token: 92d19e71-1590-7407-4824-bf612b3a83d3' \
  -d 'code=szHzhi&grant_type=authorization_code&redirect_uri=http%3A%2F%2Flocalhost%3A8081%2Flogin'
  
  4.
  Now u can use the accessToken in the below API to access the resource
  curl -X GET \
  http://localhost:8080/api/users/me \
  -H 'authorization: Bearer e39b6a44-9b51-47f3-bf7e-88f16aa3b5c9' \
  -H 'cache-control: no-cache' \
  -H 'postman-token: cae87fec-fc07-22b9-7cb5-00ca32d4597d'
