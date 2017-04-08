---
layout: post
title:  "유니티 커스터마이징 에디터 - MenuItem"
date:   2017-04-08
---



유니티 에디터 커스터마이징 기능 중 MenuItem에 대해 알아보도록 하자.



#### 클래스 구조

```c#
using UnityEditor; //이 부분만 추가해준다.
using UnityEngine;
public class MenuTest : MonoBehaviour
{
	//아래 내용을 넣어 준다.
}
```



#### 1. 메뉴아이템 추가

가장 기본적인 메뉴아이템 추가 방법이다.

```c#
[MenuItem("MyMenu/Do Something")]
static void DoSomething()
{
  Debug.Log("Doing Something...");
}
```

<figure>
	<img src="{{ '/assets/img-post/unity-editor-menuitem-01.png' | prepend: site.baseurl }}" alt=""> 
	<figcaption>Fig1. - 클릭하면 DoSomething() 함수가 실행된다.</figcaption>
</figure>



#### 2. 활성화 기능

Selection : 에디터에서 객체 선택에 관한 기능을 담당한다.
선택한 객체가 있다면 그 객체의 이름을 출력하는 메뉴아이템을 추가한다.

```c#
[MenuItem("MyMenu/Log Selected Transform Name")]
static void LogSelectedTransformName()
{
  Debug.Log("Selected Transform is on " + Selection.activeTransform.gameObject.name + ".");
}

//isValdiateFuction 옵션을 줄 수 있다.
//아래에서 정의하는 함수의 return값을 bool로 받아서, true일 경우 활성화, false일 경우 비활성화 한다.
[MenuItem("MyMenu/Log Selected Transform Name", isValidateFunction: true)]
static bool ValidateLogSelectedTransformName()
{
  return Selection.activeTransform != null;
}
```

  

isValdiateFuction 옵션을 줄 수 있다.
아래에서 정의하는 함수의 return값을 bool로 받아서, true일 경우 활성화, false일 경우 비활성화 한다.

```c#
[MenuItem("MyMenu/Log Selected Transform Name", isValidateFunction: true)]
static bool ValidateLogSelectedTransformName()
{
  return Selection.activeTransform != null;
}
```



<figure>


<img src="{{ '/assets/img-post/unity-editor-menuitem-02.png' | prepend: site.baseurl }}" alt=""> 
<figcaption>Fig2. - 에디터에서 선택한 객체가 없으면 메뉴가 비활성화 된다.</figcaption>


</figure>



#### 3. 단축키 등록

단축키를 등록할 수 있다. 동시에 등록도 가능.

* % :  Winows의 Ctrl, macOS의 cmd키
* \# : shift
* & : alt
* 숫자나 문자 등을 사용하려면 _(언더바)를 같이 쓰면 된다.
  * ex) G키를 등록하고 싶으면 _g
  * 언더바 앞에 꼭 공백(space)문자가 있어야한다.
* LEFT, RIGHT, UP, DOWN, F1 .. F12, HOME, END, PGUP, PGDN 등의 키도 사용 가능.

```c#
[MenuItem("MyMenu/Do Something with a Shortcut Key %#&g")]
static void DoSomethingWithAShortcutKey()
{
  Debug.Log("Doing something with a Shortcut Key...");
}
```

<figure>


<img src="{{ '/assets/img-post/unity-editor-menuitem-03.png' | prepend: site.baseurl }}" alt=""> 
<figcaption>Fig3. - 단축키 등록</figcaption>


</figure>





#### 4. Context 메뉴

스크립트의 기능을 Inspector의 Context Menu로 추가할 수 있다.

잠깐, 간단한 예시 스크립트를 만들어서 오브젝트에 넣어보자.

UnityEditor 키워드를 사용하지 않아도 가능.

```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class ContextMenuTest : MonoBehaviour {

	[ContextMenu ("Do Something")]
	void DoSomething () {
		Debug.Log ("Perform operation");
	}
}
```

<figure>


<img src="{{ '/assets/img-post/unity-editor-menuitem-04.png' | prepend: site.baseurl }}" alt=""> 
<figcaption>Fig4. - 이걸 Context Menu라고 하나보다.</figcaption>


</figure>

다음은 사용자가 정의한 스크립트 외에 기본 스크립트에 Context Menu로 등록하는 방법이다.

다시 MenuTest 스크립트로 돌아가서 Rigidbody의 mass를 두 배 증가시키는 Context menu를 만들어보자.

```c#
[MenuItem("CONTEXT/Rigidbody/Double Mass")]
static void DoubleMass(MenuCommand command)
{
  Rigidbody body = (Rigidbody)command.context;
  body.mass = body.mass * 2;
  Debug.Log("Doubled Rigidbody's Mass to " + body.mass + " from Context Menu.");
}
```

<figure>

<img src="{{ '/assets/img-post/unity-editor-menuitem-05.png' | prepend: site.baseurl }}" alt=""> 
<figcaption>Fig5. - 기본 컴포넌트인 Rigidbody에도 커스텀 Context Menu를 만들 수 있다.</figcaption>


</figure>





#### 5. 커스텀 오브젝트 생성

사용자가 직접 정의한 오브젝트를 생성하는 메뉴를 추가할 수 있다.

프리팹 외에 반복적으로 똑같은 기능의 오브젝트를 만들 때 유용할 듯 싶다.

```c#
[MenuItem("GameObject/MyCategory/Custom Game Object", false)]
static void CreateCustomGameObject(MenuCommand menuCommand)
{
  // 1. Custom GameObject 이름으로 새 Object를 만든다.
  GameObject go = new GameObject("Custom Game Object");
  
  // 2. Hierachy 윈도우에서 어떤 오브젝트를 선택하여 생성시에는 그 오브젝트의 하위 계층으로 생성된다.
  // 그밖의 경우에는 아무일도 일어나지 않는다.
  GameObjectUtility.SetParentAndAlign(go, menuCommand.context as GameObject);
  
  // 3. 생성된 오브젝트를 Undo 시스템에 등록한다.
  Undo.RegisterCreatedObjectUndo(go, "Create " + go.name);
  
  // 4. 생성한 오브젝트를 선택한다.
  Selection.activeObject = go;
}
```

<figure>

<img src="{{ '/assets/img-post/unity-editor-menuitem-06.png' | prepend: site.baseurl }}" alt=""> 
<figcaption>Fig6. - 단축키가 등록된 모습.</figcaption>

</figure>



#### 6. priority 설정

MenuItem의 2번째 argument는 priority다.

메뉴 아이템마다 우선순위를 부여해서 상단에서부터 순서를 조절 할 수 있다.

그리고 **상대적으로** priority가 11이상 차이나는 구간은 구역을 나누어 시각적으로 쉽게 구분 할 수 있다.

```c#
[MenuItem("MyMenu/Priority1", false, priority:1)]
static void Priority1()
{
  Debug.Log("Doing Something...");
}

[MenuItem("MyMenu/Priority5", false, priority:5)]
static void Priority5()
{
  Debug.Log("Doing Something...");
}

[MenuItem("MyMenu/Priority10", false, priority:10)]
static void Priority10()
{
  Debug.Log("Doing Something...");
}

[MenuItem("MyMenu/Priority21", false, priority:21)]
static void Priority21()
{
  Debug.Log("Doing Something...");
}

[MenuItem("MyMenu/Priority30", false, priority:31)]
static void Priority31()
{
  Debug.Log("Doing Something...");
}

[MenuItem("MyMenu/Priority41", false, priority:41)]
static void Priority41()
{
  Debug.Log("Doing Something...");
}

[MenuItem("MyMenu/Priority42", false, priority:42)]
static void Priority42()
{
  Debug.Log("Doing Something...");
}

[MenuItem("MyMenu/Priority53", false, priority:53)]
static void Priority53()
{
  Debug.Log("Doing Something...");
}
```

<figure>
<img src="{{ '/assets/img-post/unity-editor-menuitem-07.png' | prepend: site.baseurl }}" alt=""> 
<figcaption>Fig7. - 상대적으로 우선순위가 11이상 차이나는 지점을 기준으로 구역을 나눈다.</figcaption>


</figure>