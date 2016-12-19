---
title: "__try_cast | Microsoft Docs"
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
  - "__try_cast"
  - "__try_cast_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__try_cast 关键字"
  - "强制转换失败"
  - "例外情况之外，不成功强制转换"
  - "引发异常，不成功强制转换"
ms.assetid: e9e5da3a-f5b9-4915-b30a-a432e8574d03
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# __try_cast
**注意** 本主题仅适用于 C\+\+ 托管扩展的版本 1。 此语法应仅用于维护版本 1 代码。 请参阅 [safe\_cast](../windows/safe-cast-cpp-component-extensions.md) 有关新语法中使用的等效功能的信息。  
  
 执行指定的强制转换，如果强制转换失败，则引发异常。  
  
## 语法  
  
```  
  
__try_cast <  
 type-id  
 >  
(  
expression   
)  
  
```  
  
## 备注  
 `__try_cast` 关键字（行为上与 [dynamic\_cast](../cpp/dynamic-cast-operator.md) 类似）支持在指定强制转换操作失败时自动引发异常（类型为 **System::InvalidCastException**）。  
  
 `__try_cast` 关键字可在应用程序测试阶段使用，即自动提醒您可能出现的强制转换失败。  
  
 当移植 c \+ \+ 托管扩展中，替换 `__try_cast` 使用调用 [safe\_cast](../windows/safe-cast-cpp-component-extensions.md)。  
  
 `__try_cast` 无法用于指向值类型 （[\_\_value](../misc/value.md)\) 的指针的强制转换，因为它不能在运行时检查类型。  
  
## 示例  
 在以下示例中，尝试了将指针（类型为 `Derived`）强制转换为另一个指针（类型为 `MoreDerived`）。 如果强制转换失败，catch 块将捕获并报告该错误：  
  
```  
// keyword__try_cast.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
using namespace System;  
  
__gc struct Base {};   
__gc struct Derived : Base {};  
__gc struct MoreDerived : Derived {};  
  
int main() {  
   Base*bp = new Derived;  
   try {  
       MoreDerived* mdp = __try_cast<MoreDerived*>(bp);  
   }  
   catch(System::InvalidCastException*) {  
       Console::WriteLine("Could not cast 'bp' to MoreDerived*");  
   }  
}  
```  
  
## 输出  
  
```  
Could not cast 'bp' to MoreDerived*  
```