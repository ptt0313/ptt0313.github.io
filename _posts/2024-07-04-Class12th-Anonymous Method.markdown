---
layout: post
title: Anonymous Method
tags: [c# grammar]
---

## 무명 메서드

무명 메서드는 이름을 포함하지 않는 메서드입니다.
사용자가 익명 메서드에 매개변수를 전달하려는 경우에 사용합니다.
무명 메서드는 Delegate를 사용하여 정의되며 이 메서드는 변수에 할당할 수 있습니다.

~~~c#
var gameObject = new { grade = 'A', id = 100, name = "Game Object", };
// gameObject.id = 120; 불가능
Console.WriteLine("gameObject의 grade 값 : " + gameObject.grade);
Console.WriteLine("gameObject의 name 값 : " + gameObject.name);
Console.WriteLine("gameObject의 id 값 : " + gameObject.id);
~~~