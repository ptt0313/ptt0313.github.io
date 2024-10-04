---
layout: post
title: Perfect Number
category: Test
---
# 완전수
완전수(完全數)란 자기 자신을 제외한 양의 약수(진약수)를 더했을 때 자기 자신이 되는 양의 정수를 말합니다.

![실행사진](/public/img/PerfectNumber.png)

### 전체 코드
~~~c#
namespace Program
{
    internal class Program
    {
        static void Num(int a)
        {
            int j = 0;
            for (int i = 1; i < a; i++)
            {
                if(a % i == 0)
                {
                    j += i;
                }
            }
            if(a == j)
            {
                Console.Write(a + " 는 완전수입니다.");
            }
            else
            {
                Console.Write(a + " 는 완전수가 아닙니다.");
            }
        }
        static void Main(string[] args)
        {
            Num(8128);
        }
    }
}
~~~