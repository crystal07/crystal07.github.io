---
layout: posts
title:  "palindrome algorithm"
date:   2019-01-03 19:13:09 +0900
breadcrumbs: true
breadcrumb_home_label : "Home"
breadcrumb_separator  : ">"
categories: algorithm
author_profile: false

---

단어들 중에는 거꾸로 읽어도 동일한 단어, 예를 들면 `level` 같은 단어들이 존재한다. 우리는 이런 경우들을 `회문(palindrome)`이라 말한다.

그렇다면 우리는 단어가 주어졌을 때 이가 회문을 이루는지, 아닌지 어떻게 판별할 수 있을까?

이는 다음과 같은 recursive한 방법을 통해 해결할 수 있다.

~~~python
def is_palindrome(word, index_1, index_2) :
    if (index_1 == index_2) :
        return True
    if (word[index_1] != word[index_2]) :
        return False
    
    if index_1 < index_2 :
        return is_palindrome(word, index_1 + 1, index_2 - 1)
    else :
        return True

word = input()
print("Yes" if is_palindrome(word, 0, len(word) - 1) else "No")
~~~

하지만 재귀 함수를 따로 짜는게 귀찮다면 python에서는 다음과 같은 방법으로도 해결은 가능하다.

~~~python
word = input()
middle = int(len(word) / 2)
if len(word) % 2 == 0 :
    left_word = word[:middle]
    right_word = word[middle:]
else :
    left_word = word[:middle]
    right_word = word[middle + 1:]

print("Yes" if left_word[::-1] == right_word else "No")
~~~