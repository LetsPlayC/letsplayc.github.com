---
layout: page
title: Lets Play C!
tagline: C언어 공부를 위한 학습 블로그
---
{% include JB/setup %}
## Posts List

<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>

Read [c(프로그래밍 언어) - 위키백과](https://ko.wikipedia.org/wiki/C_%28%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8D_%EC%96%B8%EC%96%B4%29)

---

## C (프로그래밍 언어)

C는 1972년 켄 톰슨과 데니스 리치가 벨 연구소에서 일할 당시 새로 개발된 유닉스 운영 체제에서 사용하기 위해 개발한 프로그래밍 언어이다. 유닉스 시스템의 바탕 프로그램은 모두 C로 쓰여졌고, 많은 운영 체제의 커널도 또한 C로 만들어졌다. 오늘날 많이 쓰이는 C++는 C에서 객체 지향형 언어로 발전된 것이다. 또 다른 다양한 최신 언어들도 그 뿌리를 C에 두고 있다.

---

###역사
    
    * 1963년 - ALGOL 60에서 CPL이 파생
    * 1969년 - BCPL 개발
    * 1970년 - B언어 개발
    * 1972년 - 벨 연구소 (Bell Laboratories) 에 있는 Dennis Ritchie가 B의 후속으로 C 개발
    * 1983년 - 미국 국가 표준 협회(ANSI, American National Standards Institute) 에서 짐 브로디(Jim Brodie) 주축으로 X3J11 위원회 소집
    * 1983년 12월 14일 - ANSI X3.159-1989 라는 공식명칭으로 C언어 표준 지정
    * 1999년 - C99 표준안이 ISO/IEC 9899:1999라는 명칭으로 출간됨
    * 2000년 5월 - ANSI의 표준으로 C99가 채택됨
    * 2011년 - 12월 8일 C11 표준안이 ISO/IEC 9899:2011라는 명칭으로 출간됨
    


C언어는 최근까지도 향상되고 있는 언어이다.

---

### 헬로 월드 프로그램

{% highlight c linenos %}
#include <stdio.h>

int main() {	
	printf("Hello World!!!!!");

	return 0;
}
{% endhighlight %}

### C언어는 절차 지향적

{% highlight c linenos %}
#include <stdio.h>

int main() {
	int x = 7;
	int y = 10;
    
	if(x >= 5)
		x = x + y;
        
	z = x;
   
	return 0;
}
{% endhighlight %}

다음은 위 프로그램을 시각화 한 것이다.

보다시피 C언어는 처음문장에서 시작하여 흐름을 따라 마지막 문장까지 실행시키는 절차지향적 프로그램 언어이다.

<body>
<iframe width="800" height="500" frameborder="0" src="http://pythontutor.com/iframe-embed.html#code=x+%3D+7%0Ay+%3D+10%0A%09%0Aif+x+%3E%3D+5%3A%0A++++x+%3D+x+%2B+y%0A%09++++%0Az+%3D+x&origin=opt-frontend.js&cumulative=false&heapPrimitives=false&drawParentPointers=false&textReferences=false&showOnlyOutputs=false&py=3&rawInputLstJSON=%5B%5D&curInstr=0&codeDivWidth=350&codeDivHeight=400"> </iframe>
</body>
