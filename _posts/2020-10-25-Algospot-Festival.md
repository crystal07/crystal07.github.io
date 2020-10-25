---
date: 2020-10-25
title: "[Algorithm][Algospot] Lock Festival"
categories:
- Algorithm
tags:
- Algorithm
- Algospot
- 알고리즘 문제해결 전략
---

# Overview
- 문제 : [Lock Festival](https://algospot.com/judge/problem/read/FESTIVAL)
- 목표 : 최소한 연속되는 L일 이상의 공연을 할 때 평균 비용이 최소화 되는 공연일자를 찾는 것

# Code
~~~ c++
#include <stdio.h>

#define BIGGER(x, y) x > y ? true : false

int price[1000];
int n, l;

double get_min_average_cost() {

    double min_cost = 1000001;

    for (int i = 0; i < n; i++) {
        double cost = price[i];
        int count = 1;

        if (count >= l && BIGGER(min_cost, cost)) {
            min_cost = cost;
        }

        for (int j = i + 1; j < n; j++) {
            cost += price[j];
            count++;

            double new_average = cost / count;
            if (count >= l && BIGGER(min_cost, new_average)) {
                min_cost = new_average;
            }
        }
    }

    return min_cost;
}

int main()
{
    int c;
    scanf("%d", &c);
      
    for (int test = 0; test < c; test++) {
        scanf("%d %d", &n, &l);
        
        int tmp;
        for (int i = 0; i < n; i++) {
            scanf("%d", &price[i]);
        }

        printf("%.8f\n", get_min_average_cost());
    }

    return 0;
}
~~~

# Retrospect
1. 처음에 문제를 풀 때 한번만 평균값이 높아져도 전체적인 평균값이 올라갈 것이라고 착각하였으나 한번 평균값이 올라가더라고 다음날의 비용이 저렴하다면 다시 평균값이 낮아질 수 있음을 간과함.

2. double/float 정밀도 에러
    - `g++ -O3` compile option을 사용하는 경우 최적화 옵션 중 하나가 실수형 데이터를 레지스터에 저장 (x86 아키텍쳐에서는 80 bit 레지스터 사용) → 평균값을 저장할 때 정밀도 손실 가능성
    - 최적화를 하지 않는 경우도 4 byte의 float를 가까운 값으로 표현하므로 정밀도 에러
    - float 보다는 double 사용 권장
    - [https://algospot.com/forum/read/2178/](https://algospot.com/forum/read/2178/) 참조
