---
layout: post
title: ASCII
category: c# grammar
---

## ASCII 코드

미국 국가표준 협회에서 표준화한 정보 교환용 7 bit 부호체계입니다.

문자 인코딩
복잡한 신호를 0과 1의 디지털 신호로 변환하는 방식입니다.

~~~c#
char alphabet = 'A';


for (int i = 0; i < 26; i++)
{
    Console.Write((char)('A' + i) + " ");
}

Console.WriteLine();

Console.WriteLine("alphabet 변수의 값 : " + (int)alphabet);
~~~