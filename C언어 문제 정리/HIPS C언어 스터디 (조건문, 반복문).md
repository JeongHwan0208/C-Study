# HIPS C언어 스터디 (조건문, 반복문)

## 조건문

### 두수 비교하기

두 정수 A와 B가 주어졌을 때, A와 B를 비교하는 프로그램을 작성하시오.

```c
# include <stdio.h>

int main(void) {
	int A, B;

	scanf("%d", &A);
	scanf("%d", &B);

	if (A > B) printf(">");
	else if (A < B) printf("<");
	else if (A == B) printf("==");
	return 0;
}
```

### 시험 성적

시험 점수를 입력받아 90 ~ 100점은 A, 80 ~ 89점은 B, 70 ~ 79점은 C, 60 ~ 69점은 D, 나머지 점수는 F를 출력하는 프로그램을 작성하시오.

```C
#include <stdio.h>

int main(void) {
    int num = 0;

    scanf("%d", &num);

    if (num >= 90 && num <= 100) printf("A");
    else if (num >= 80 && num < 90) printf("B");
    else if (num >= 70 && num < 80) printf("C");
    else if (num >= 60 && num < 70) printf("D");
    else printf("F");

    return 0;
}
```

### 윤년

연도가 주어졌을 때, 윤년이면 1, 아니면 0을 출력하는 프로그램을 작성하시오.

윤년은 연도가 4의 배수이면서, 100의 배수가 아닐 때 또는 400의 배수일 때이다.

```C
#include <stdio.h>

int main(void) {
    int year;

    scanf("%d", &year);

    if ((year % 4 == 0 && year % 100 != 0) || (year % 4 == 0 && year % 400 == 0)) {
        printf("1");
    }
    else printf("0");
    return 0;
}
```

### 사분면 고르기

흔한 수학 문제 중 하나는 주어진 점이 어느 사분면에 속하는지 알아내는 것이다. 사분면은 아래 그림처럼 1부터 4까지 번호를 갖는다. "Quadrant n"은 "제n사분면"이라는 뜻이다.

![조건문 1](https://github.com/JeongHwan0208/C-Study/blob/main/C%EC%96%B8%EC%96%B4%20%EB%AC%B8%EC%A0%9C%20%EC%A0%95%EB%A6%AC/img/%EC%A1%B0%EA%B1%B4%EB%AC%B8%201.png)

```C
#include <stdio.h>

int main(void) {
    int x;
    int y;

    scanf("%d", &x);
    scanf("%d", &y);

    if (x > 0 && y > 0) printf("1");
    else if (x < 0 && y>0) printf("2");
    else if (x > 0 && y < 0) printf("4");
    else if (x < 0 && y < 0) printf("3");
    return 0;
}
```

### 알람 시계

상근이는 매일 아침 알람을 듣고 일어난다. 알람을 듣고 바로 일어나면 다행이겠지만, 항상 조금만 더 자려는 마음 때문에 매일 학교를 지각하고 있다.

상근이는 모든 방법을 동원해보았지만, 조금만 더 자려는 마음은 그 어떤 것도 없앨 수가 없었다.

이런 상근이를 불쌍하게 보던 창영이는 자신이 사용하는 방법을 추천해 주었다.

바로 "45분 일찍 알람 설정하기"이다.

이 방법은 단순하다. 원래 설정되어 있는 알람을 45분 앞서는 시간으로 바꾸는 것이다. 어차피 알람 소리를 들으면, 알람을 끄고 조금 더 잘 것이기 때문이다. 이 방법을 사용하면, 매일 아침 더 잤다는 기분을 느낄 수 있고, 학교도 지각하지 않게 된다.

현재 상근이가 설정한 알람 시각이 주어졌을 때, 창영이의 방법을 사용한다면, 이를 언제로 고쳐야 하는지 구하는 프로그램을 작성하시오.

```C
#include <stdio.h>

int main(void) {
	int H;
	int M;
	
	scanf("%d %d",&H,&M);

	if (M < 45) {
		if (H == 0) {
			int L = 45 - M;
			M = 0;
			M = 60 - L;
			H = 23;
			printf("%d %d", H, M);
		}
		else {
			int L = 45 - M;
			M = 0;
			M = 60 - L;
			H -= 1;
			printf("%d %d", H, M);
		}
	}
	else {
		M -= 45;
		printf("%d %d",H,M);
	}
	return 0;
}
```

### 오븐 시계

KOI 전자에서는 건강에 좋고 맛있는 훈제오리구이 요리를 간편하게 만드는 인공지능 오븐을 개발하려고 한다. 인공지능 오븐을 사용하는 방법은 적당한 양의 오리 훈제 재료를 인공지능 오븐에 넣으면 된다. 그러면 인공지능 오븐은 오븐구이가 끝나는 시간을 분 단위로 자동적으로 계산한다.

또한, KOI 전자의 인공지능 오븐 앞면에는 사용자에게 훈제오리구이 요리가 끝나는 시각을 알려 주는 디지털 시계가 있다.

훈제오리구이를 시작하는 시각과 오븐구이를 하는 데 필요한 시간이 분단위로 주어졌을 때, 오븐구이가 끝나는 시각을 계산하는 프로그램을 작성하시오.

```C
#include <stdio.h>

int main(void) {
    int H;
    int M;
    int C;
    scanf("%d %d", &H, &M);
    scanf("%d", &C);

    M = M + C; 

    if (M >= 60) {
        H = H + M / 60; 
        M = M % 60;    
    }

  
    H = H % 24;

    printf("%d %d", H, M);
    return 0;
}
```

### 주사위 세개

1에서부터 6까지의 눈을 가진 3개의 주사위를 던져서 다음과 같은 규칙에 따라 상금을 받는 게임이 있다. 

1. 같은 눈이 3개가 나오면 10,000원+(같은 눈)×1,000원의 상금을 받게 된다. 
2. 같은 눈이 2개만 나오는 경우에는 1,000원+(같은 눈)×100원의 상금을 받게 된다. 
3. 모두 다른 눈이 나오는 경우에는 (그 중 가장 큰 눈)×100원의 상금을 받게 된다.  

3개 주사위의 나온 눈이 주어질 때, 상금을 계산하는 프로그램을 작성 하시오.

```C
#include <stdio.h>

int main(void) {
    int A, B, C;
    
    scanf("%d %d %d", &A, &B, &C);

    if (A == B && B == C && A==C) {
        printf("%d", 10000 + (A  * 1000));
    }
    else if((A==B&&((A!=C)||(B!=C))) || (C == B && ((C != A) || (B != A))) || (A == C && ((A != B) || (C != B)))) {
        if (A == B) printf("%d", 1000 + (A * 100));
        else if (A == C) printf("%d", 1000 + (A * 100));
        else if (C == B) printf("%d", 1000 + (C * 100));
    }
    else if (A != B && B != C && A != C) {
        if (A > B && A > C) printf("%d", A * 100);
        else if (B > A && B > C) printf("%d", B * 100);
        else if (C > A && C > B) printf("%d", C * 100);
    }
    return 0;
}
```

## 반복문

### 구구단

N을 입력받은 뒤, 구구단 N단을 출력하는 프로그램을 작성하시오. 출력 형식에 맞춰서 출력하면 된다.

```C
#include <stdio.h>

int main(void) {
    int A;
    
    scanf("%d", &A);

    for (int i=1; i < 10; i++) {
        printf("%d * %d = %d\n", A, i, A * i);
    }
    return 0;
}
```

### A + B - 3

두 정수 A와 B를 입력받은 다음, A+B를 출력하는 프로그램을 작성하시오.

첫째 줄에 테스트 케이스의 개수 T가 주어진다.

각 테스트 케이스는 한 줄로 이루어져 있으며, 각 줄에 A와 B가 주어진다. (0 < A, B < 10)

```C
#include <stdio.h>

int main(void) {
    int A,B,C;
    
    scanf("%d", &A);

    for (int i=0; i < A; i++) {
        scanf("%d %d", &B,&C);
        printf("%d\n", B + C);
    }
    return 0;
}
```

### 합

n이 주어졌을 때, 1부터 n까지 합을 구하는 프로그램을 작성하시오.

```C
#include <stdio.h>

int main(void) {
    int n;
    int sum = 0;
    
    scanf("%d", &n);

    for (int i = 1; i <= n; i++) {
        sum += i;
    }
    printf("%d", sum);
    return 0;
}
```

### 영수증

준원이는 저번 주에 살면서 처음으로 코스트코를 가 봤다. 정말 멋졌다. 그런데, 몇 개 담지도 않았는데 수상하게 높은 금액이 나오는 것이다! 준원이는 영수증을 보면서 정확하게 계산된 것이 맞는지 확인해보려 한다.

영수증에 적힌,

- 구매한 각 물건의 가격과 개수
- 구매한 물건들의 총 금액

을 보고, 구매한 물건의 가격과 개수로 계산한 총 금액이 영수증에 적힌 총 금액과 일치하는지 검사해보자.

```C
#include <stdio.h>

int main(void) {
    int X, N, a, b;
    int sum = 0;
    scanf("%d", &X);
    scanf("%d", &N);

    for (int i = 0; i < N; i++) {
        scanf("%d %d", &a, &b);
        sum += a * b;
    }
    if (X == sum) printf("Yes");
    else printf("No");

    return 0;
}
```

### 코딩은 체육과목 입니다.

혜아는 책에 있는 정수 자료형과 관련된 내용을 기억해 냈다. 책에는 `long int`는 4$4$바이트 정수까지 저장할 수 있는 정수 자료형이고 `long long int`는 8$8$바이트 정수까지 저장할 수 있는 정수 자료형이라고 적혀 있었다. 혜아는 이런 생각이 들었다. “`int` 앞에 `long`을 하나씩 더 붙일 때마다 4$4$바이트씩 저장할 수 있는 공간이 늘어나는 걸까? 분명 `long long long int`는 12$12$바이트, `long long long long int`는 16$16$바이트까지 저장할 수 있는 정수 자료형일 거야!” 그렇게 혜아는 당황하는 면접관의 얼굴을 뒤로한 채 칠판에 정수 자료형을 써 내려가기 시작했다.

혜아가 N바이트 정수까지 저장할 수 있다고 생각해서 칠판에 쓴 정수 자료형의 이름은 무엇일까?

```C
#include <stdio.h>

int main(void) {
    int N;
   
    scanf("%d", &N);
    
    if (N % 4 == 0) {
        for (int i = 0; i < (N / 4) -1; i++) {
            printf("long ");
        }
        printf("long int");
    }
    return 0;
}
```

### 빠른 A+B

첫 줄에 테스트케이스의 개수 T가 주어진다. T는 최대 1,000,000이다. 다음 T줄에는 각각 두 정수 A와 B가 주어진다. A와 B는 1 이상, 1,000 이하이다.

```C
#include <stdio.h>

int main(void) {
    int A, B, C;

    scanf("%d", &A);

    for (int i = 0; i < A; i++) {
        scanf("%d %d", &B, &C);
        printf("%d\n", B + C);
    }
    return 0;
}
```

### A + B - 7

두 정수 A와 B를 입력받은 다음, A+B를 출력하는 프로그램을 작성하시오.

첫째 줄에 테스트 케이스의 개수 T가 주어진다.

각 테스트 케이스는 한 줄로 이루어져 있으며, 각 줄에 A와 B가 주어진다. (0 < A, B < 10)

```C
#include <stdio.h>

int main(void) {
    int A, B, C;

    scanf("%d", &A);

    for (int i = 1; i <= A; i++) {
        scanf("%d %d", &B, &C);
        printf("Case #%d: %d\n",i, B + C);
    }
    return 0;
}
```

### A + B - 8

두 정수 A와 B를 입력받은 다음, A+B를 출력하는 프로그램을 작성하시오.

첫째 줄에 테스트 케이스의 개수 T가 주어진다.

각 테스트 케이스는 한 줄로 이루어져 있으며, 각 줄에 A와 B가 주어진다. (0 < A, B < 10)

각 테스트 케이스마다 "Case #x: A + B = C" 형식으로 출력한다. x는 테스트 케이스 번호이고 1부터 시작하며, C는 A+B이다.

```C
#include <stdio.h>

int main(void) {
    int A, B, C;

    scanf("%d", &A);

    for (int i = 1; i <= A; i++) {
        scanf("%d %d", &B, &C);
        printf("Case #%d: %d + %d = %d\n",i,B,C, B + C);
    }
    return 0;
}
```

### 별 찍기 - 1

첫째 줄에는 별 1개, 둘째 줄에는 별 2개, N번째 줄에는 별 N개를 찍는 문제

```C
#include <stdio.h>

int main(void) {
    int N;
     scanf("%d", &N);
    for (int i = 1; i <= N; i++) {
        for (int j = 1; j <= i; j++) {
            printf("*");
        }
        printf("\n");
    }

    return 0;
}
```

### 별 찍기 - 2

첫째 줄에는 별 1개, 둘째 줄에는 별 2개, N번째 줄에는 별 N개를 찍는 문제

하지만, 오른쪽을 기준으로 정렬한 별(예제 참고)을 출력하시오.

```C
#include <stdio.h>

int main(void) {
    int N;

    scanf("%d", &N);

    for (int i = 1; i <= N; i++) {
        for (int j = 1; j <= N - i; j++) {
            printf(" ");
        }
        for (int j = 1; j <= i; j++) {
            printf("*");
        }
        printf("\n");
    }
    return 0;
}
```

### A + B - 5

두 정수 A와 B를 입력받은 다음, A+B를 출력하는 프로그램을 작성하시오.

입력은 여러 개의 테스트 케이스로 이루어져 있다.

각 테스트 케이스는 한 줄로 이루어져 있으며, 각 줄에 A와 B가 주어진다. (0 < A, B < 10)

입력의 마지막에는 0 두 개가 들어온다.

```C
#include <stdio.h>

int main(void) {
    int A, B;

    for (;;) {
        scanf("%d %d", &A, &B);
        if (A == 0 && B == 0) break;
        printf("%d\n", A + B);
    }
    return 0;
}
```

### A + B - 4

두 정수 A와 B를 입력받은 다음, A+B를 출력하는 프로그램을 작성하시오.

입력은 여러 개의 테스트 케이스로 이루어져 있다.

각 테스트 케이스는 한 줄로 이루어져 있으며, 각 줄에 A와 B가 주어진다. (0 < A, B < 10)

입력이 끝날 때까지 A+B를 출력하는 문제. EOF에 대해 알아 보세요.

```C
#include <stdio.h>

int main() {
   int a, b, res;
   while (1) {
      res = scanf("%d %d", &a, &b);
      if (res == -1) {
         break;
      }
      printf("%d\n", a + b);
   }
   return 0;
}
```

