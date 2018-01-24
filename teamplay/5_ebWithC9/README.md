## Chapter 5. Elastic BeanStalk With C9
1. `pip install awsebcli --upgrade --user`
2. `eb init --platform node.js --region ap-northeast-2`
3. `eb create --sample node-express-env`
4. `.ebextensions` 디렉토리 만들고 `nodecommand`  파일 만들고 아래 내용 붙여넣기
```
option_settings:
  aws:elasticbeanstalk:container:nodejs:
    NodeCommand: "npm start"
```
5. `eb deploy` -> s3에 올리고 -> deploy
6. [Elastic BeanStalk](https://ap-northeast-2.console.aws.amazon.com/elasticbeanstalk/home?region=ap-northeast-2#/welcome) 접속 -> URL 들어가보기
7. 구성 -> 용량 -> 조정 트리거 -> CPU Utilization -> 단위 % -> 기간, 위반기간 1, 상위 임계값 50%, 하위 임계값 10%
8. `sudo yum install httpd-tools` -> AB Test Tool 설치 
	1. `ab -n 500000 -c 200 http://node-express-env.5w8ypy45cy.ap-northeast-2.elasticbeanstalk.com/` -> 

실습이 완료되면 다음모듈인 [Chapter 6. 삭제 가이드](../6_removeGuide/README.md) 으로 이동하십시오