---
layout: post
category : lessons
tagline: c언어 포인터
tags : C Language, Pointer, lessons
---
{% include JB/setup %}

## 포인터

### 포인터의 개념
---
**포인터 변수(pointer variable)**는 다른 변수의 주소를 가지고 있는 변수이다.

(*포인터변수또한 변수라는 점을 기억!*)

포인터는 다른 변수를 가리킨다고도 말할 수 있다.

주소는 컴퓨터에 따라 다를 수 있으므로 포인터 변수는 대개 정확한 숫자보다는 그냥 화살표로 그려진다.
모든 변수는 주소는 메모리 주소를 가지고 있다!

컴퓨터 메모리는 바이트로 구성되어 있고 각 바이트마다 순차적으로 주소가 매겨져 있다.

![포인터는 변수를 가리킨다.]({{ site.url }}/assets/Pointer/K-2.jpg)

위의 그림에서 p는 a라는 변수를 가리키는 포인터 변수이다.

그림에 해당되는 C언어 문장은 다음과 같다.

{% highlight c linenos %}
int main(void) {
	char a = 'A';
	char *p;
	p = &a;
}
{% endhighlight %}

먼저 char형의 변수 a가 정의되고 p는 char형을 가리키는 포인터로 정의된다.

p가 a를 가리키게 하려면 a의 주소를 p에 대입한다.

변수의 주소는 & 연산자를 변수에 적용시켜서 추출할 수 있다.

포인터 변수가 가리키는 메모리의 내용을 추출하거나 변경하려면 * 연산자를 사용한다.

앞의 문장들에 이어서 다음과 같은 문장을 실행시키면 그림과 같이 변수 a의 내용이 바뀌게 된다.

{% highlight c linenos %}
	*p = 'B';
{% endhighlight %}


![포인터를 통한 변수 값의 변경]({{ site.url }}/assets/Pointer/K-3.jpg)

이들 예제 문장에서는 *p와 변수 a가 동일한 메모리 위치를 참조함을 유의해야 한다.

즉 *p와 변수 a는 전적으로 동일하다.

즉 이들의 값만 같은 것이 아니고 동일한 객체를 가리키기 때문에 *p의 값을 변경하게 되면 변수 a의 값도 바뀌게 된다.

###포인터와 관련된 연산자

---

 포인터에서 가장 중요한 연산자는 &와 *이다. 그림과 같이 & 연산자는 변수로부터 변수의 주소를 추출해내는 연산자이다.

어떤 변수에도 적용할 수 있다.

![& 연산자와 * 연산자]({{ site.url }}/assets/Pointer/K-4.jpg)

그림과 같이 *연산자는 포인터가 가리키는 변수의 내용을 추출하는 연산자이다.

###다양한 포인터
---
포인터는 다음과 같이 여러 가지 타입의 대상에 대하여 선언 될 수 있다.

{% highlight c linenos %}
void *p;  	//p는 아무것도 가리키지 않는 포인터
int *pi;	//p는 정수 변수를 가리키는 포인터
float *pf;	//pf는 실수 변수를 가리키는 포인터
char *pc;	//pc는 문자 변수를 가리키는 포인터
int **pp;	//pp는 포인터를 가리키는 포인터
struct test *ps;	//ps는 test의 구조체를 가리키는 포인터
void (*f)(int);	//f는 int를 매개 변수로 갖고 반환 값을 갖지않는 함수를 가리키는 포인터.
{% endhighlight %}


void *p는 아무것도 가리키지 않는 포인터를 의미한다.

void 포인터는 필요할 때마다 다른 포인터로 바꾸어서 사용하는 것이 가능하다.


{% highlight c linenos %}
	pi = (int *)p;	//p를 정수 포인터로 변경하여 pi로 대입.
{% endhighlight %}

####포인터를 함수의 매개 변수로 사용하는 프로그램

{% highlight c linenos %}
//두 개의 변수의 값을 교환

void swap(int *px, int *py)
{
	int tmp;

	tmp = *px;
	*px = *py;
	*py = tmp;
}


int main(void)
{
	int  a = 1, b = 2;

	printf("swap을 호출하기 전: a = %d, b = %d\n", a, b);
	swap(&a, &b);
	printf("swap을 호출한 다음: a = %d, b = %d\n", a, b);

    return 0;
}
{% endhighlight %}

####프로그램 결과

	swap을 호출하기 전 : a = 1, b = 1
	swap을 호출한 다음 : a = 2, b = 2

---

### 포인터의 포인터
포인터도 하나의 변수이므로 포인터의 포인터도 선언이 가능하다.

실제로 앞으로 다룰 몇 개의 자료 구조에서 함수에 포인터의 포인터를 전달할 것이다.

다음의 문장은 문자 포인터에 대한 포인터를 선언하고 연결한다.


{% highlight c linenos %}
char *a;  //문자변수 선언
char *p; //문자 포인터 선언
char **pp; //문자 포인터의 포인터 선언
a = 'A';
p = &a; //변수 a와 포인터 p를 연결
pp = &p; //포인터 p와 포인터의 포인터 pp를 연결
{% endhighlight %}


![& 포인터의 포인터]({{ site.url }}/assets/Pointer/K-7.jpg)

---

###포인터에 대한 연산
 포인터에 대한 연산은 보통의 연산과 다른 의미를 지닌다.

정수의 포인터에 값을 더하거나 빼보자.

다음과 같이 정수의 포인터 pi를 생성하고 정수 변수를 가리키도록 하자.

pi+1, pi-1의 값은 어떻게 될까?

주소 값이 하나 감소되고 증가하는 것이 아니라 pi-1은 pi가 가리키는 객체 하나 뒤에 있는 객체를 가리키고 pi+1은 pi가 가리키는 객체 하나 앞에있는 객체를 가리킨다.

즉 앞의 코드에서는 pi+1은 A[4]를 pi-1은 A[2]를 가리킨다.

포인터에 대한 사칙 연산은 일반적인 사칙 연산과 다른 의미를 가진다.

![& 포인터에 대한 연산]({{ site.url }}/assets/Pointer/K-8.jpg)

---

###포인터 설명 동영상

<iframe width="420" height="315" src="http://www.youtube.com/embed/mnXkiAKbUPg" frameborder="0" allowfullscreen></iframe>

---

###포인터 관련 이론 문제

{% highlight c linenos %}
	int i = 10;
    int *p;
    
    p=&i;
    *p=8;
{% endhighlight %}
다음 간단한 프로그램에서 i의 값은 얼마인가?

<input type="radio" name="chk_info" value="1">11
<input type="radio" name="chk_info" value="2">10
<input type="radio" name="chk_info" value="3">9
<input type="radio" name="chk_info" value="4">8


###포인터 관련 실습 문제

	두개의 int형 포인터(max, min)와 길이가 5인 int형 배열을 선언한 다음, 총 5개의 정수를 사용자로부터 입력받는다. 그리고 나서 두 개의 포인터와 배열을 함수 maxMin의 인자로 전달한다. 함수 호출이 완료되고나면 max와 min은 배열의 최대값과 최소값을 가리키고 있어야 한다. 이러한 기능을 지니는 함수 maxMin을 정의하고, 이에 적절한 main 함수도 구현해 보자. main 함수의 마지막에서는 포인터 max와 min이 가리키는 메모리가 지니고 있는 값을 출력하기로 하자.

<textarea rows="100" cols="100" name="contents"></textarea>



