---
title: "__event | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "__event_cpp"
  - "__event"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__event 关键字 [C++]"
  - "事件 [C++], __event"
ms.assetid: d3019b3e-722e-48df-8536-c05878461f9e
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# __event
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

声明事件。  
  
## 语法  
  
```  
  
      __event   
      method-declarator  
      ;  
__event __interface interface-specifier;  
__event member-declarator;  
```  
  
## 备注  
 关键字 `__event` 可应用于方法声明、接口声明或数据成员声明。  但是，不能使用 `__event` 关键字限定嵌套类的成员。  
  
 根据您的事件源和接收器是本机 C\+\+、COM 还是托管 \(.NET Framework\)，您可使用下列构造作为事件：  
  
|本机 C\+\+|COM|托管 \(.NET Framework\)|  
|--------------|---------|---------------------------|  
|方法|—|方法|  
|—|接口|—|  
|—|—|数据成员|  
  
 在事件接收器中使用 [\_\_hook](../cpp/hook.md) 可将处理程序方法与事件方法关联。  请注意，使用 `__event` 关键字创建一个事件之后，将在调用此事件时调用后来挂钩到它的所有事件处理程序。  
  
 `__event` 方法声明不能具有定义；定义是隐式生成的，因此可将事件方法当做任何普通方法一样调用。  
  
> [!NOTE]
>  模板类或结构不能包含事件。  
  
## 本机事件  
 本机事件是方法。  返回类型通常是 `HRESULT` 或 `void`，但可以是任何整型（包括 `enum`）。  当事件使用整数返回类型时，如果事件处理程序返回非零值，则会定义错误条件，在这种情况下，引发的事件将调用其他委托。  
  
```  
// Examples of native C++ events:  
__event void OnDblClick();  
__event HRESULT OnClick(int* b, char* s);  
```  
  
 有关代码示例，请参阅[本机 C\+\+ 中的事件处理](../cpp/event-handling-in-native-cpp.md)。  
  
## COM 事件  
 COM 事件是接口。  事件源接口中的方法的参数应为 **in** 参数（但这不是强制要求的），因为 **out** 参数在多播时无用。  如果使用 **out** 参数，则将发出 1 级警告。  
  
 返回类型通常是 `HRESULT` 或 `void`，但可以是任何整型（包括 `enum`）。  当事件使用整数返回类型并且事件处理程序返回非零值时，这是错误情况，此时引发的事件将中止对其他委托的调用。  请注意，编译器会自动将一个事件源接口标记为生成的 IDL 中的[源](../windows/source-cpp.md)。  
  
 COM 事件源的 `__event` 之后始终需要 [\_\_interface](../cpp/interface.md) 关键字。  
  
```  
// Example of a COM event:  
__event __interface IEvent1;  
```  
  
 有关代码示例，请参阅 [COM 中的事件处理](../cpp/event-handling-in-com.md)。  
  
## 托管事件  
 有关新语法中的编码事件的信息，请参阅[event](../windows/event-cpp-component-extensions.md)。  
  
 托管事件是数据成员或方法。  当与事件一起使用时，委托的返回类型必须符合[公共语言规范](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md)。  事件处理程序的返回类型必须与委托的返回类型匹配。  有关委托的详细信息，请参阅 [\_\_delegate](../misc/delegate.md)。  如果托管事件是数据成员，则其类型必须是指向委托的指针。  
  
 在 .NET Framework 中，您可以将数据成员视为方法本身（即，其对应委托的 `Invoke` 方法）。  您必须预定义用于声明托管事件数据成员的委托类型。  相反，如果尚未定义对应的托管委托，则托管事件方法将隐式定义它。  例如，您可以将事件值（如 `OnClick`）声明为下面所示的事件：  
  
```  
// Examples of managed events:  
__event ClickEventHandler* OnClick;  // data member as event  
__event void OnClick(String* s);  // method as event  
```  
  
 隐式声明托管事件时，您可以指定添加或移除添加或移除事件处理程序时将调用的 add 和 remove 访问器。  您还可以定义从类外部调用（引发）事件的方法。  
  
## 示例：本机事件  
  
```  
// EventHandling_Native_Event.cpp  
// compile with: /c  
[event_source(native)]  
class CSource {  
public:  
   __event void MyEvent(int nValue);  
};  
```  
  
## 示例：COM 事件  
  
```  
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
  
## 示例：托管事件  
  
```  
// EventHandling_Managed_Event.cpp  
// compile with: /clr:oldSyntax /c  
using namespace System;  
[event_source(managed)]  
public __gc class CPSource {  
  
public:  
   __event void MyEvent(Int16 nValue);  
};  
```  
  
 将特性应用于事件时，您可以指定特性应用于生成的方法还是生成的委托的 Invoke 方法。默认值 \(`event:`\) 用于将特性应用于事件。  
  
```  
// EventHandling_Managed_Event_2.cpp  
// compile with: /clr:oldSyntax /c  
using namespace System;  
[attribute(All, AllowMultiple=true)]  
public __gc class Attr {};  
  
public __delegate void D();  
  
public __gc class X {  
public:  
   [method:Attr] __event D* E;  
   [returnvalue:Attr] __event void noE();  
};  
```  
  
## 请参阅  
 [C\+\+ 关键字](../cpp/keywords-cpp.md)   
 [事件处理](../cpp/event-handling.md)   
 [event\_source](../windows/event-source.md)   
 [event\_receiver](../windows/event-receiver.md)   
 [\_\_hook](../cpp/hook.md)   
 [\_\_unhook](../cpp/unhook.md)   
 [\_\_raise](../cpp/raise.md)