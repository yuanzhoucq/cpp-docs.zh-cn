---
title: 事件 （c + + 组件扩展） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event
- event_cpp
dev_langs:
- C++
helpviewer_keywords:
- event keyword [C++]
ms.assetid: c4998e42-883c-4419-bbf4-36cdc979dd27
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7859b8b58bbd8765c38daea46efea5859ba61d67
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33881206"
---
# <a name="event--c-component-extensions"></a>event（C++ 组件扩展）
`event`关键字声明*事件*，这是一条通知到已注册的订阅服务器 (*事件处理程序*) 的相关事情已发生。  
  
## <a name="all-runtimes"></a>所有运行时  
 C + + /CX 支持声明*事件成员*或*事件块*。 事件成员是用于声明事件块的速记属性。 默认情况下，事件成员声明 `add()`、`remove()` 和 `raise()` 函数，而这些函数将在事件块中显式声明。 若要自定义事件成员中的函数，请改为声明一个事件块，然后替代所需的函数。  
  
 **语法**  
  
```  
  
// event data member  
modifiereventdelegate^ event_name;     
  
// event block  
modifiereventdelegate^ event_name   
{  
   modifierreturn_valueadd(delegate^ name);  
   modifier void remove(delegate^ name);  
   modifier void raise(parameters);  
}  
```  
  
 **参数**  
  
 *修饰符*  
 修饰符可用于事件声明或事件访问器方法。  可能的值为 `static` 和 `virtual`。  
  
 *delegate*  
 [委托](../windows/delegate-cpp-component-extensions.md)，事件处理程序必须与匹配的签名。  
  
 *event_name*  
 事件的名称。  
  
 *return_value*  
 事件访问器方法的返回值。  若要具有可验证性，返回类型必须是 `void`。  
  
 *参数*  
 （可选）参数`raise`方法，与匹配的签名*委托*参数。  
  
 **备注**  
  
 事件是委托与成员函数（事件处理程序）之间的关联，用于对事件的触发作出响应并允许客户端从任何类注册符合基础委托签名和返回类型的方法。  
  
 有两种类型的事件声明：  
  
 *事件数据成员*  
 编译器会自动以委托类型成员的形式为事件创建存储空间，并创建内部 `add()`、`remove()` 和 `raise()` 成员函数。 必须在类中声明事件数据成员。 委托的返回类型必须与事件处理程序的返回类型匹配。  
  
 *事件块*  
 事件块可显式声明并自定义 `add()`、`remove()` 和 `raise()` 方法的行为。  
  
 可以使用 `operators+=` 和 `operator-=` 来添加和删除事件处理程序，或者显式调用 `add()` 和 `remove()` 方法。  
  
 `event` 是上下文相关的关键字;请参阅[上下文相关的关键字](../windows/context-sensitive-keywords-cpp-component-extensions.md)有关详细信息。  
  
## <a name="windows-runtime"></a>Windows 运行时  
  
### <a name="remarks"></a>备注  
 有关详细信息，请参阅[事件 (C + + /cli CX)](http://msdn.microsoft.com/library/windows/apps/hh755799.aspx)。  
  
 如果想要添加，然后删除事件处理程序，则必须保存添加操作返回的 EventRegistrationToken 结构。 然后在删除操作中，必须使用已保存的 EventRegistrationToken 结构来标识要删除的事件处理程序。  
  
### <a name="requirements"></a>要求  
 编译器选项： **/ZW**  
  
## <a name="common-language-runtime"></a>公共语言运行时 
 `event` 关键字允许声明事件。 事件是类在相关事件发生时提供通知的一种方式。  
  
 **语法**  
  
```  
  
// event data member  
modifiereventdelegate^ event_name;   
  
// event block  
modifiereventdelegate^ event_name   
{  
   modifierreturn_valueadd(delegate^ name);  
   modifier void remove(delegate^ name);  
   modifier void raise(parameters);  
}  
```  
  
 **参数**  
  
 *修饰符*  
 修饰符可用于事件声明或事件访问器方法。  可能的值为 `static` 和 `virtual`。  
  
 *delegate*  
 [委托](../windows/delegate-cpp-component-extensions.md)，事件处理程序必须与匹配的签名。  
  
 *event_name*  
 事件的名称。  
  
 *return_value*  
 事件访问器方法的返回值。  若要具有可验证性，返回类型必须是 `void`。  
  
 *参数*  
 （可选）参数`raise`方法，与匹配的签名*委托*参数。  
  
 **备注**  
  
 事件是委托与成员函数（事件处理程序）之间的关联，用于对事件的触发作出响应并允许客户端从任何类注册符合基础委托签名和返回类型的方法。  
  
 委托可以有一个或多个关联方法，当代码指示事件发生时将调用这些方法。 程序中的事件可供面向 .NET Framework 公共语言运行时的其他程序使用。  
  
 有两种类型的事件声明：  
  
 *事件数据成员*  
 委托类型成员形式的事件存储空间由数据成员事件的编译器创建。  必须在类中声明事件数据成员。 这也称为普通事件（请参阅下面的代码示例。）  
  
 *事件块*  
 事件块允许通过实现添加、删除和引发方法来自定义添加、删除和引发方法的行为。 添加、删除和引发方法的签名必须与委托的签名匹配。  事件块事件不是数据成员，且任何用作数据成员的情况都将生成编译器错误。 
  
 事件处理程序的返回类型必须与委托的返回类型匹配。  
  
 在 .NET Framework 中，您可以将数据成员视为方法本身（即，其对应委托的 `Invoke` 方法）。 您必须预定义用于声明托管事件数据成员的委托类型。 相反，如果尚未定义对应的托管委托，则托管事件方法将隐式定义它。  有关示例，请参阅本主题末尾处的代码示例。  
  
 声明托管事件时，可以指定在使用运算符 += 和 -= 添加或删除事件处理程序时将调用的 add 和 remove 访问器。 添加、删除和引发方法可以显式调用。  
  
 必须遵循以下步骤在 Visual C++ 中创建并使用事件：  
  
1.  创建或标识委托。 如果要定义自己的事件，还必须确保有一个委托与 `event` 关键字一起使用。 例如，如果该事件在 .NET Framework 中进行了预定义，则该事件的使用者只需知道委托的名称。  
  
2.  创建包括以下内容的类：  
  
    -   从委托创建的事件。  
  
    -   （可选）验证使用 `event` 关键字声明的委托实例是否存在的方法。 否则，此逻辑必须放在激发事件的代码中。  
  
    -   调用此事件的方法。 这些方法可以替代一些基类功能。  
  
     此类将定义该事件。  
  
3.  定义一个或多个将方法连接到该事件的类。 其中每个类会将一个或多个方法与基类中的事件相关联。  
  
4.  使用事件：  
  
    -   创建包含事件声明的类的对象。  
  
    -   创建包含事件定义的类的对象。  
  
 有关详细信息 C + + /cli CLI 事件，请参阅  
  
-   [接口中的事件](../dotnet/how-to-use-events-in-cpp-cli.md)  
  
### <a name="requirements"></a>要求  
 编译器选项： **/clr**  
  
### <a name="examples"></a>示例  
 **示例**  
  
 下面的代码示例演示如何声明委托对、事件和事件处理程序；订阅（添加）事件处理程序；调用事件处理程序；然后取消订阅（删除）事件处理程序。  
  
```  
// mcppv2_events.cpp  
// compile with: /clr  
using namespace System;  
  
// declare delegates  
delegate void ClickEventHandler(int, double);  
delegate void DblClickEventHandler(String^);  
  
// class that defines events  
ref class EventSource {  
public:  
   event ClickEventHandler^ OnClick;   // declare the event OnClick  
   event DblClickEventHandler^ OnDblClick;   // declare OnDblClick  
  
   void FireEvents() {  
      // raises events  
      OnClick(7, 3.14159);  
      OnDblClick("Hello");  
   }  
};  
  
// class that defines methods that will called when event occurs  
ref class EventReceiver {  
public:  
   void OnMyClick(int i, double d) {  
      Console::WriteLine("OnClick: {0}, {1}", i, d);  
   }  
  
   void OnMyDblClick(String^ str) {  
      Console::WriteLine("OnDblClick: {0}", str);  
   }  
};  
  
int main() {  
   EventSource ^ MyEventSource = gcnew EventSource();  
   EventReceiver^ MyEventReceiver = gcnew EventReceiver();  
  
   // hook handler to event  
   MyEventSource->OnClick += gcnew ClickEventHandler(MyEventReceiver, &EventReceiver::OnMyClick);  
   MyEventSource->OnDblClick += gcnew DblClickEventHandler(MyEventReceiver, &EventReceiver::OnMyDblClick);  
  
   // invoke events  
   MyEventSource->FireEvents();  
  
   // unhook handler to event  
   MyEventSource->OnClick -= gcnew ClickEventHandler(MyEventReceiver, &EventReceiver::OnMyClick);  
   MyEventSource->OnDblClick -= gcnew DblClickEventHandler(MyEventReceiver, &EventReceiver::OnMyDblClick);  
}  
```  
  
 **输出**  
  
```Output  
OnClick: 7, 3.14159  
  
OnDblClick: Hello  
```  
  
 **示例**  
  
 下面的代码示例演示了用于生成普通事件的 `raise` 方法的逻辑：如果该事件具有一个或多个订阅服务器，则隐式调用 `raise` 方法或显式调用委托。 如果该委托的返回类型不是 `void`，并且没有事件订阅服务器，则 `raise` 方法将返回该委托类型的默认值。 如果没有事件订阅服务器，则调用 `raise` 方法仅返回而不会引发异常。 如果该委托的返回类型不是 `void`，则将返回该委托类型。  
  
```  
// trivial_events.cpp  
// compile with: /clr /c  
using namespace System;  
public delegate int Del();  
public ref struct C {  
   int i;  
   event Del^ MyEvent;  
  
   void FireEvent() {  
      i = MyEvent();  
   }  
};  
  
ref struct EventReceiver {  
   int OnMyClick() { return 0; }  
};  
  
int main() {  
   C c;  
   c.i = 687;  
  
   c.FireEvent();  
   Console::WriteLine(c.i);  
   c.i = 688;  
  
   EventReceiver^ MyEventReceiver = gcnew EventReceiver();  
   c.MyEvent += gcnew Del(MyEventReceiver, &EventReceiver::OnMyClick);  
   Console::WriteLine(c.i);     
}  
```  
  
 **输出**  
  
```Output  
0  
  
688  
```  
  
## <a name="see-also"></a>请参阅  
 [适用于运行时平台的组件扩展](../windows/component-extensions-for-runtime-platforms.md)