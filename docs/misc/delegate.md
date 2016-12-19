---
title: "__delegate | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__delegate_cpp"
  - "__delegate"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "委托，_delegate 关键字"
  - "托管的函数指针"
  - "__delegate 关键字"
ms.assetid: a41d2211-b79b-4509-a4c2-cc91f3d4fc9d
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# __delegate
**注意** 本主题仅适用于 C\+\+ 托管扩展的版本 1。 此语法应仅用于维护版本 1 代码。 请参阅 [委托](../windows/delegate-cpp-component-extensions.md) 有关新语法中使用的等效功能的信息。  
  
 定义可用于使用特定签名封装方法的引用类型。  
  
## 语法  
  
```  
  
__delegate   
function-declarator  
  
```  
  
## 备注  
 委托与 C\+\+ 函数指针基本等效，但存在以下差异：  
  
-   委托只能绑定到 \_\_gc 类中的一个或多个方法。  
  
 当编译器遇到 `__delegate` 关键字时，将生成 \_\_gc 类的定义。 此 \_\_gc 类具有以下特性：  
  
-   它继承自 **System::MulticastDelegate**。  
  
-   它具有一个采用两个参数的构造函数：指向 \_\_gc 类或 **NULL** 的指针（绑定到静态方法时）和指定类型的完全限定方法。  
  
-   它具有一个称为 `Invoke` 的方法，其签名与委托的声明签名匹配。  
  
## 示例  
 在下面的示例中，将声明 \_\_gc 类 \(`MyCalendar`\) 和委托 \(`GetDayOfWeek`\)。 然后，委托将绑定到 `MyCalendar` 的不同方法，并依次调用每个方法：  
  
```  
// keyword__delegate.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
using namespace System;  
  
__delegate int GetDayOfWeek();  
__gc class MyCalendar {  
public:  
   MyCalendar() : m_nDayOfWeek(4) {}  
   int MyGetDayOfWeek() {   
      Console::WriteLine("handler"); return m_nDayOfWeek;   
   }  
   static int MyStaticGetDayOfWeek() {   
      Console::WriteLine("static handler");   
      return 6;  
   }  
private:  
   int m_nDayOfWeek;  
};  
  
int main () {  
   GetDayOfWeek * pGetDayOfWeek;  // declare delegate type  
   int nDayOfWeek;  
  
   // bind delegate to static method  
   pGetDayOfWeek = new GetDayOfWeek(0, &MyCalendar::MyStaticGetDayOfWeek);  
   nDayOfWeek = pGetDayOfWeek->Invoke();  
   Console::WriteLine(nDayOfWeek);  
  
   // bind delegate to instance method  
   MyCalendar * pcal = new MyCalendar();  
   pGetDayOfWeek = static_cast<GetDayOfWeek*>(Delegate::Combine(pGetDayOfWeek,  
      new GetDayOfWeek(pcal, &MyCalendar::MyGetDayOfWeek)));  
   nDayOfWeek = pGetDayOfWeek->Invoke();  
   Console::WriteLine(nDayOfWeek);  
  
   // delegate now bound to two methods; remove instance method  
   pGetDayOfWeek = static_cast<GetDayOfWeek*>(Delegate::Remove(pGetDayOfWeek,  
      new GetDayOfWeek(pcal, &MyCalendar::MyGetDayOfWeek)));  
}  
```  
  
## 示例输出  
  
```  
static handler  
6  
static handler  
handler  
4  
```