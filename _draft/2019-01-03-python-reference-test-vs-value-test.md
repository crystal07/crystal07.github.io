---
layout: posts
title:  "python value test vs reference test"
date:   2019-01-03 19:13:09 +0900
breadcrumbs: true
breadcrumb_home_label : "Home"
breadcrumb_separator  : ">"
categories: python
author_profile: false

---
python에서 프로그래밍을 할때 같은 값인지 비교하기 위해 우리는 `is`와 `==`를 사용할 수 있다. 그렇다면 이 둘의 차이는 무엇일까?

우선적으로 `==`는 **value equality**를 비교하기 위한 것이다. 이 명령어에서 우리는 우리가 인지하는 값을 비교하게 된다.

하지만 `is`명령어는 **reference equality**를 비교하기 위한 것이다. 이 명령어에서 우리는 우리가 인지하는 값이 아닌 실제로  같은 객체인지 아닌지를 비교하게 된다.

그렇다면 우리는 다음과 같은 상황에서 아래와 같은 결과를 예측하게 될 것이다.

~~~~~python
> a = 5
> b = 5
> c = a
> a == b
True
> a is b
False
> a == c
True
> a is c
True
~~~~~

하지만 이 경우에도 일관적이지 않게 `a is b`에서도 `True`와 같은 결과가 나오기도 한다. 이는 python에서 성능을 위해 자주 사용되는 -5 ~ 256 범위의 integer를 미리 singleton instance로 cacheing해두기 때문이라고 한다.

