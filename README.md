# actionTest

GitHub에서 제공하는 Action을 사용해보기

1. 저장소에 push될 때마다 Hello, World를 출력하기

![image](https://user-images.githubusercontent.com/67398691/119435026-5e2f6900-bd54-11eb-86ed-b98bf997930f.png)

이미지1) Actions에서 새 액션을 작성하기

- name에는 실행항목의 이름을, run에 실제 작동할 코드를 넣는다
- 여기에서는 hello, world를 출력하고 디렉토리와 파이썬 버전을 출력하도록 함

![image](https://user-images.githubusercontent.com/67398691/119435132-86b76300-bd54-11eb-97ba-1acb35be2aac.png)

이미지2) 실제로 저장소에 변경이 생기면 Actions에서 해당 액션이 구동됨을 확인 할 수 있다

2. 파이썬 파일을 액션으로 실행해보기

![image](https://user-images.githubusercontent.com/67398691/119437704-a7ce8280-bd59-11eb-9901-c928d3a01a49.png)
![image](https://user-images.githubusercontent.com/67398691/119437713-a9984600-bd59-11eb-85aa-1851bded3f8f.png)

이미지3,4) 저장소에 파이썬 파일을 생성하고 액션을 수정하기

- 이 때, uses:actions/checkout@v2를 명시하지 않으면 실행되지 않는다

3. 파이썬 패키지를 설치하기

![image](https://user-images.githubusercontent.com/67398691/119695142-dbf49100-be88-11eb-9c77-f5ad653e78a0.png)

이미지5) main.yml에 패키지를 인스톨하는 구문을 추가

4. 설치된 파이썬 패키지를 통해 크롤링 하기

![image](https://user-images.githubusercontent.com/67398691/119695256-f62e6f00-be88-11eb-866f-18de0230e75c.png)

이미지6) BeautifulSoup 라이브러리를 사용하여 리디북스의 신간 서적 리스트를 긁어오기

![image](https://user-images.githubusercontent.com/67398691/119695423-1ceca580-be89-11eb-80d8-ebfc3ce9052d.png)

![image](https://user-images.githubusercontent.com/67398691/119695436-2118c300-be89-11eb-8d0c-f71c5f337e56.png)

이미지 7,8) Action을 사용해 크롤링한 결과와 실제 페이지

