---
layout: post
title: Dictionary
tags: [c# grammar]
---

# Dictionary

c#에서 Dictionary는 Key와 Value값을 저장하는 데 사용되는 제네릭 컬렉션입니다.
작동방식은 비제네릭 해시테이블과 매우 유사합니다.

1. Dictionary 클래스는 다음을 구현합니다.
    - IDictionary<TKey,TValue> 인터페이스
    - IReadOnlyCollection<KeyValuePair<TKey,TValue>> 인터페이스
    - IReadOnlyDictionary<TKey,TValue> 인터페이스
    - IDictionary 인터페이스
1. 키는 null이 될 수 없지만 값은 null이 될 수 있습니다.
1. Dictionary에서 키는 중복되지 않아야 합니다. 중복키를 사용시 컴파일러 에러가 발생합니다.
1. 동일한 유형의 요소만 저장할 수 있습니다.
1. 크기는 Dictionary가 보유할 수 있는 요소의 수입니다.

| 프로퍼티 | 설명 | 
|----|---|
| Comparer | 키가 같은지 확인하는데 사용됩니다. | 
| Count | Dictionary의 키/값의 쌍을 가져옵니다. |
| Item[TKey] | 지정된 Key와 연결된 값을 가져옵니다. |
| Keys | Dictionary<TKey,TValue>의 키가 포함된 컬렉션을 가져옵니다. |
| Value | Dictionary<TKey,TValue>의 값이 포함된 컬렉션을 가져옵니다.|


___
> 참고 자료 : https://www.geeksforgeeks.org/c-sharp-dictionary-class/