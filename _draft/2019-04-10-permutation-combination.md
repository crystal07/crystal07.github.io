---
layout: posts
title:  "Permutation, Combination Implementation"
date:   2019-04-10 19:13:09 +0900
breadcrumbs: true
breadcrumb_home_label : "Home"
breadcrumb_separator  : ">"
categories: algorithm, permutation, combination
author_profile: false
---

```html
<script type="text/javascript" async
  src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-MML-AM_CHTML">
</script>
```

**순열(permutation)**과 **조합(combination)**, 이들은 사실 중고등학교 시절부터 계속 봐왔기에 당연하고 익숙하게 받아들이는 개념이였다. 하지만 막상 이를 code로 구현하려니 생각이 잘 나지 않더라. 그래서 이번 기회에 한번 이를 구현해보고자 한다.

먼저 순열은 서로 다른 **n**개에서 **r**개를 뽑아 일렬로 배열한 것을 말하며 이는 **nPr**로 표현된다.

