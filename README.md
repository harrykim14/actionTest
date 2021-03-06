# actionTest

GitHub에서 제공하는 Action을 사용해보기

**1. 저장소에 push될 때마다 Hello, World를 출력하기**

![image](https://user-images.githubusercontent.com/67398691/119435026-5e2f6900-bd54-11eb-86ed-b98bf997930f.png)

이미지1) Actions에서 새 액션을 작성하기

- name에는 실행항목의 이름을, run에 실제 작동할 코드를 넣는다
- 여기에서는 hello, world를 출력하고 디렉토리와 파이썬 버전을 출력하도록 함

![image](https://user-images.githubusercontent.com/67398691/119435132-86b76300-bd54-11eb-97ba-1acb35be2aac.png)

이미지2) 실제로 저장소에 변경이 생기면 Actions에서 해당 액션이 구동됨을 확인 할 수 있다

**2. 파이썬 파일을 액션으로 실행해보기**

![image](https://user-images.githubusercontent.com/67398691/119437704-a7ce8280-bd59-11eb-9901-c928d3a01a49.png)
![image](https://user-images.githubusercontent.com/67398691/119437713-a9984600-bd59-11eb-85aa-1851bded3f8f.png)

이미지3,4) 저장소에 파이썬 파일을 생성하고 액션을 수정하기

- 이 때, uses:actions/checkout@v2를 명시하지 않으면 실행되지 않는다

**3. 파이썬 패키지를 설치하기**

![image](https://user-images.githubusercontent.com/67398691/119695142-dbf49100-be88-11eb-9c77-f5ad653e78a0.png)

이미지5) main.yml에 패키지를 인스톨하는 구문을 추가

**4. 설치된 파이썬 패키지를 통해 크롤링 하기**

![image](https://user-images.githubusercontent.com/67398691/119695256-f62e6f00-be88-11eb-866f-18de0230e75c.png)

이미지6) BeautifulSoup 라이브러리를 사용하여 리디북스의 신간 서적 리스트를 긁어오기

![image](https://user-images.githubusercontent.com/67398691/119695423-1ceca580-be89-11eb-80d8-ebfc3ce9052d.png)

![image](https://user-images.githubusercontent.com/67398691/119695436-2118c300-be89-11eb-8d0c-f71c5f337e56.png)

이미지 7,8) Action을 사용해 크롤링한 결과와 실제 페이지

**5. GitHub에서 제공하는 스케쥴 이벤트**
 
 - GitHub은 crontab의 양식에 따라 반복적인 작업을 할 수 있는 기능을 제공하고 있음
 - 이 crontab은 리눅스 계열의 OS에 내장되어 있으며 주기적으로 반복되는 일을 자동으로 실행할 수 있도록 해 줌

```shell
// 1분마다 해당하는 명령어를 실행
* * * * * /test/crawling.py

// 5분마다 해당하는 명령어를 실행
*/5 * * * * /test/crawling.py

// 매일 오전 9시 30분, 오후 9시 30분에 해당하는 명령어를 실행
30 9,21 * * * /test/crawling.py

// 매일 매시간 10분, 20분마다 해당하는 명령어를 실행
10,20 * * * * /test/crawling.py

// 매일 오전 9시에 해당하는 명령어를 실행
0 9 * * 0-6 /test/crawling.py

// 월~금 오전 9시에 해당하는 명령어를 실행
0 9 * * 1-5 /test/crawling.py
```

위 내용을 정리하자면 이런 식으로 스케쥴러의 인자값을 사용할 수 있다
```yaml
   *        *         *        *         *
# 분(0-59) 시간(0-23) 일(1-31) 월(1-12) 요일(0-7)
```

**6. 크롤링한 내용을 파일로 저장하여 저장소에 푸쉬하기**

![fileWrite](https://user-images.githubusercontent.com/67398691/120098068-d17b1580-c16e-11eb-9ce6-5e1a8dcecb3d.JPG)

이미지9) with open 함수를 사용하여 js파일 내 json 형태로 크롤해 온 데이터를 저장

![commit](https://user-images.githubusercontent.com/67398691/120098072-d50e9c80-c16e-11eb-90a1-4307e0bad092.JPG)

이미지10) 커밋을 위해 git 커맨드를 차례로 실행하고 push는 github actions에서 제공하는 github-push-action을 사용하여 

**7. 환경변수 사용해보기**

![image](https://user-images.githubusercontent.com/67398691/120131606-b6a6b080-c203-11eb-9ed9-8debd76e1e91.png)

![image](https://user-images.githubusercontent.com/67398691/120131611-b9090a80-c203-11eb-87c5-ac0d2d069518.png)

이미지11,12) 환경변수를 yml파일에 정의하는 법과 환경변수를 출력해 
