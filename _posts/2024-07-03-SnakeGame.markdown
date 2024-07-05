---
layout: post
title: SnakeGame
category: game
---
## c#콘솔 뱀게임

___
<iframe width="450" height="350" src="https://www.youtube.com/embed/KyoBg08fqio" title="C# Console 뱀게임" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
---


### 1. 이동

먼저 처음 시작할 좌표에 머리를 만들어 줬습니다.

~~~c#
public class Character
{
    int x = 10;
    int y = 8;

    public int X
    {
        get {return x};
        set {x = value};
    }
    public int Y
    {
        get {return y};
        set {y = value}; 
    }
}
Console.SetCursorPosition(character.X, character.Y);
Console.Write("●");
~~~

switch문을 사용하여 enum Direction을 받아오고 Console.KeyAvailable을 사용하여
가져온 Direction을 이동시마다 사용되도록 합니다.
X축 이동과 Y축 이동의 길이를 맞추기 위해 움직일때 마다 (x * 2) , y 의 좌표를 가지게 합니다.

~~~c#
enum Direction
{
    Up,
    Left,
    Right,
    Down
}
if (Console.KeyAvailable)
{ 
key = Console.ReadKey();
    switch (key.Key)
    {
        case ConsoleKey.UpArrow:
            direction = Direction.Up;
            break;
        case ConsoleKey.LeftArrow:
            direction = Direction.Left;
            break;
        case ConsoleKey.RightArrow:
            direction = Direction.Right;
            break;
        case ConsoleKey.DownArrow:
            direction = Direction.Down;
            break;
    }
}
switch (direction)
{
    case Direction.Up:
        character.Y--;
        break;
    case Direction.Left:
        character.X -= 2;
        break;
    case Direction.Right:
        character.X += 2;
        break;
    case Direction.Down:
        character.Y++;
        break;
}
~~~

### 2. 꼬리생성

꼬리는 머리가 이동할때마다 계속 따라와야합니다.
머리가 움직일때마다 원래 머리가 있던 좌표에 생성되게하고
맨 마지막 꼬리를 없애주면 꼬리가 따라오는듯한 움직임을 구현할 수 있습니다.
자료구조 Queue의 특성을 이용하여 먼저 생성된 꼬리의 삭제를 이동시 마다 반복시킵니다.

![Alternative Text](https://i.namu.wiki/i/D1oW_IYncpCg5fV3YqX8dKUjfhl2sq6N6VtFZHxTwnb4qDL_A9chdG1_i8DWgVtCmgzfnRCZvAbCrPI0ESFi4vvePZV_QvJociJuimqErKxEWfRXcDm7vWMOmjutWXBQPA7ygxqmZ8umRaVfxm6tWQ.webp)

~~~c#
public void AddTail(int x, int y)
{
    tail.Enqueue((x, y));
    if (map.map[x,y] != 3)
    {
        map.map[x, y] = 2;
    }
}
tail.AddTail(character.Y, character.X / 2);

public void RemoveTail()
{
    if (tail.Count > 0)
    {
        (int x,int y) = tail.Dequeue();
        map.map[x, y] = 0;
    }
}
tail.RemoveTail();
~~~

### 3. 맵타일

맵은 2차원배열을 사용하여 벽과 맵,꼬리,별을 표시하도록 했습니다.
게임로직이 반복될때마다 맵을 새로그리며 게임 화면을 업데이트해줍니다.
~~~c#
public class Map
{

    public int[,] map = new int[12, 12]
    {
        { 1,1,1,1,1,1,1,1,1,1,1,1 },
        { 1,0,0,0,0,0,0,0,0,0,0,1 },
        { 1,0,0,0,0,0,0,0,0,0,0,1 },
        { 1,0,0,0,0,0,0,0,0,0,0,1 },
        { 1,0,0,0,0,0,0,0,0,0,0,1 },
        { 1,0,0,0,0,0,0,0,0,0,0,1 },
        { 1,0,0,0,0,0,0,0,0,0,0,1 },
        { 1,0,0,0,0,0,0,0,0,0,0,1 },
        { 1,0,0,0,0,0,0,0,0,0,0,1 },
        { 1,0,0,0,0,0,0,0,0,0,0,1 },
        { 1,0,0,0,0,0,0,0,0,0,0,1 },
        { 1,1,1,1,1,1,1,1,1,1,1,1 }
    };
    public void CreateMap()
    {
        for (int i = 0; i < map.GetLength(0); i++)
        {
            for (int j = 0; j < map.GetLength(1); j++)
            {
                
                if (map[i, j] == 1)
                {
                    Console.Write("■");
                }
                else if (map[i, j] == 0)
                {
                    Console.Write("  ");
                }
                else if (map[i, j] == 2)
                {
                    Console.Write("○");
                }
                else if (map[i, j] == 3)
                {
                    Console.Write("★");
                }
            }
            Console.WriteLine();
        }
    }
}
~~~
### 4. 별 생성

별을 먹을때 마다 새로운 별을 만들어야 합니다.
이때 별이 벽과 꼬리와 겹친 위치에 나와선 안되기때문에
while문을 통해 랜덤한 좌표가 빈공간에 별을 생성할때까지 반복을 해줍니다.
~~~c#
Random random = new Random();
while(true)
{
    int rx = random.Next(1, 11);
    int ry = random.Next(1, 11);
    if (map.map[rx, ry] == 0 && map.map[rx, ry] != 2)
    {
        map.map[rx, ry] = 3;
        break;
    }
}
~~~

### 5. 충돌 판정

머리와 오브젝트의 충돌 판정은 2차원배열을 통해 만들었습니다.
현재 위치의 캐릭터와 2차원 배열의 좌표값을 비교하여
해당 2차원 배열에 있는 숫자를 통해 충돌판정을 구현합니다.
~~~c#
// 캐릭터가 아이템을 먹을 시 해당 좌표값 0으로 설정
if (map.map[character.Y, character.X / 2] == 3)
{
    map.map[character.Y, character.X / 2] = 0;
    break;
}
// 캐릭터가 벽과 부딪힐 경우 게임종료
else if (map.map[character.Y, character.X / 2] == 1)
{
    Console.Clear();
    Console.WriteLine("Defeat");
    Environment.Exit(0);
}
// 캐릭터가 본인의 꼬리와 부딪힐 경우 게임종료
else if (map.map[character.Y, character.X / 2] == 2)
{
    Console.Clear();
    Console.WriteLine("Defeat");
    Environment.Exit(0);
}
~~~


### 6. 게임 로직 코드

~~~c#
static void Main(string[] args)
{
    Console.SetWindowSize(30, 15);
    Console.BackgroundColor = ConsoleColor.DarkGreen;
    Console.ForegroundColor = ConsoleColor.White;
    
    Map map = new Map();
    Character character = new Character();
    Tail tail = new Tail(map);
    ConsoleKeyInfo key;
    Direction direction = new Direction();
    Random random = new Random();
    for (int n = 0; n < 100; n++)
    {   

        if (n == 99)
        {
            Console.Clear();
            Console.WriteLine("VICTORY");
            Environment.Exit(0);
        }

        // 랜덤한 좌표로 아이템 생성
        
        while(true)
        {
            int rx = random.Next(1, 11);
            int ry = random.Next(1, 11);
            if (map.map[rx, ry] == 0 && map.map[rx, ry] != 2)
            {
                map.map[rx, ry] = 3;
                break;
            }
        }
        
        
        //게임 반복 로직
        while (true)
        {
            Console.Clear();
            // 2차원 배열 맵 생성
            map.CreateMap();
            // 캐릭터의 좌표에 뱀 생성
            Console.SetCursorPosition(character.X, character.Y);
            Console.Write("●");
            // 게임 속도조절
            Thread.Sleep(100);
            // 뱀 이동시 꼬리추가
            tail.AddTail(character.Y, character.X / 2);
            // 키 입력값 변수선언
            if (Console.KeyAvailable)
            { 
            key = Console.ReadKey();
                switch (key.Key)
                {
                    case ConsoleKey.UpArrow:
                        direction = Direction.Up;
                        break;
                    case ConsoleKey.LeftArrow:
                        direction = Direction.Left;
                        break;
                    case ConsoleKey.RightArrow:
                        direction = Direction.Right;
                        break;
                    case ConsoleKey.DownArrow:
                        direction = Direction.Down;
                        break;
                }
            }
            // 키입력 변수 반환
            switch (direction)
            {
                case Direction.Up:
                    character.Y--;
                    break;
                case Direction.Left:
                    character.X -= 2;
                    break;
                case Direction.Right:
                    character.X += 2;
                    break;
                case Direction.Down:
                    character.Y++;
                    break;
            }

            // 캐릭터가 아이템을 먹을 시 해당 좌표값 0으로 설정, 꼬리 삭제 건너뛰기
            if (map.map[character.Y, character.X / 2] == 3)
            {
                map.map[character.Y, character.X / 2] = 0;
                break;
            }
            // 캐릭터가 벽과 부딪힐 경우 게임종료
            else if (map.map[character.Y, character.X / 2] == 1)
            {
                Console.Clear();
                Console.WriteLine("Defeat");
                Environment.Exit(0);
            }
            // 캐릭터가 본인의 꼬리와 부딪힐 경우 게임종료
            else if (map.map[character.Y, character.X / 2] == 2)
            {
                Console.Clear();
                Console.WriteLine("Defeat");
                Environment.Exit(0);
            }
            // 뱀 이동후 꼬리삭제
            tail.RemoveTail();
        }
    }
}
~~~
