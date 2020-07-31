---
title: __event
ms.date: 11/04/2016
f1_keywords:
- __event_cpp
- __event
helpviewer_keywords:
- __event keyword [C++]
- events [C++], __event
ms.assetid: d3019b3e-722e-48df-8536-c05878461f9e
ms.openlocfilehash: 2adbadecacb41a8e92cd36f55da9b376b4e1b006
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227512"
---
# <a name="__event"></a>__event

声明事件。

## <a name="syntax"></a>语法

```
__event method-declarator;
__event __interface interface-specifier;
__event member-declarator;
```

## <a name="remarks"></a>备注

关键字 **`__event`** 可应用于方法声明、接口声明或数据成员声明。 但是，不能使用 **`__event`** 关键字限定嵌套类的成员。

根据您的事件源和接收器是本机 C++、COM 还是托管 (.NET Framework)，您可使用下列构造作为事件：

|本机 C++|COM|托管 (.NET Framework)|
|------------------|---------|--------------------------------|
|方法|—|method|
|—|interface|—|
|—|—|数据成员 (data member)|

在事件接收器中使用[__hook](../cpp/hook.md)将处理程序方法与事件方法相关联。 请注意，在使用关键字创建事件后 **`__event`** ，在调用事件时，随后将调用与该事件挂钩的所有事件处理程序。

**`__event`** 方法声明不能有定义; 隐式生成定义，因此可以像调用任何普通方法一样调用事件方法。

> [!NOTE]
> 模板类或结构不能包含事件。

## <a name="native-events"></a>本机事件

本机事件是方法。 返回类型通常为 HRESULT 或 **`void`** ，但可以是任何整型类型，包括 **`enum`** 。 当事件使用整数返回类型时，如果事件处理程序返回非零值，则会定义错误条件，在这种情况下，引发的事件将调用其他委托。

```cpp
// Examples of native C++ events:
__event void OnDblClick();
__event HRESULT OnClick(int* b, char* s);
```

有关示例代码，请参阅[本机 c + + 中的事件处理](../cpp/event-handling-in-native-cpp.md)。

## <a name="com-events"></a>COM 事件

COM 事件是接口。 事件源接口中的方法的参数应*在参数中*（但这不是严格强制的），因为*out*参数在多播时不起作用。 如果使用*out*参数，将发出1级警告。

返回类型通常为 HRESULT 或 **`void`** ，但可以是任何整型类型，包括 **`enum`** 。 当事件使用整数返回类型并且事件处理程序返回非零值时，这是错误情况，此时引发的事件将中止对其他委托的调用。 请注意，编译器会将事件源接口自动标记为生成的 IDL 中的[源](../windows/attributes/source-cpp.md)。

对于 COM 事件源，始终需要[__interface](../cpp/interface.md)关键字 **`__event`** 。

```cpp
// Example of a COM event:
__event __interface IEvent1;
```

有关代码示例，请参阅[COM 中的事件处理](../cpp/event-handling-in-com.md)。

## <a name="managed-events"></a>托管事件

有关新语法中的事件编码的信息，请参阅[事件](../extensions/event-cpp-component-extensions.md)。

托管事件是数据成员或方法。 当与事件一起使用时，委托的返回类型必须符合[公共语言规范](/dotnet/standard/language-independence-and-language-independent-components)。 事件处理程序的返回类型必须与委托的返回类型匹配。 有关委托的详细信息，请参阅[委托和事件](../dotnet/delegates-and-events.md)。 如果托管事件是数据成员，则其类型必须是指向委托的指针。

在 .NET Framework 中，您可以将数据成员视为方法本身（即，其对应委托的 `Invoke` 方法）。 您必须预定义用于声明托管事件数据成员的委托类型。 相反，如果尚未定义对应的托管委托，则托管事件方法将隐式定义它。 例如，您可以将事件值（如 `OnClick`）声明为下面所示的事件：

```cpp
// Examples of managed events:
__event ClickEventHandler* OnClick;  // data member as event
__event void OnClick(String* s);  // method as event
```

隐式声明托管事件时，你可以指定添加或移除添加或移除事件处理程序时将调用的 add 和 remove 访问器。 您还可以定义从类外部调用（引发）事件的方法。

## <a name="example-native-events"></a>示例：本机事件

```cpp
// EventHandling_Native_Event.cpp
// compile with: /c
[event_source(native)]
class CSource {
public:
   __event void MyEvent(int nValue);
};
```

## <a name="example-com-events"></a>示例：COM 事件

```cpp
// EventHandling_COM_Event.cpp
// compile with: /c
#define _ATL_ATTRIBUTES 1
#include <atlbase.h>
#include <atlcom.h>

[ module(dll, name="EventSource", uuid="6E46B59E-89C3-4c15-A6D8-B8A1CEC98830") ];

[ dual, uuid("00000000-0000-0000-0000-000000000002") ]
__interface IEventSource {
   [id(1)] HRESULT MyEvent();
};
[ coclass, uuid("00000000-0000-0000-0000-000000000003"),  event_source(com) ]
class CSource : public IEventSource {
public:
   __event __interface IEventSource;
   HRESULT FireEvent() {
      __raise MyEvent();
      return S_OK;
   }
};
```

## <a name="see-also"></a>另请参阅

[关键字](../cpp/keywords-cpp.md)<br/>
[事件处理](../cpp/event-handling.md)<br/>
[event_source](../windows/attributes/event-source.md)<br/>
[event_receiver](../windows/attributes/event-receiver.md)<br/>
[__hook](../cpp/hook.md)<br/>
[__unhook](../cpp/unhook.md)<br/>
[__raise](../cpp/raise.md)
