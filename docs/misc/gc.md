---
title: "__gc | Microsoft Docs"
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
  - "__gc"
  - "__gc_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__gc 类型"
  - "管理类 [c + +]"
  - "托管类"
ms.assetid: 63b1e7ab-d1c8-4582-aa89-21bfddf694a9
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# __gc
> [!NOTE]
>  本主题仅适用于 C\+\+ 托管扩展的版本 1。 此语法应仅用于维护版本 1 代码。 请参阅 [类和结构 \(托管\)](../windows/classes-and-structs-cpp-component-extensions.md) 有关新语法中使用的等效功能的信息。  
  
 声明 \_\_gc 类型。  
  
## 语法  
  
```  
  
__gc  
array-specifier  
__gc   
class-specifier  
__gc   
struct-specifier  
__gc  
interface-specifier  
__gc  
pointer-specifier  
__gc new  
  
```  
  
## 备注  
 \_\_gc 类型是 C\+\+ 语言扩展，它通过提供互操作性和垃圾回收等功能来简化 .NET Framework 编程。  
  
> [!NOTE]
>  除非成员函数是纯虚函数，否则必须定义 \_\_gc 抽象类的每个成员函数。  
  
 在 C\+\+ 托管扩展中，C\# 类和 C\# 结构的等效项如下所示：  
  
|C\+\+ 托管扩展|C\#|更多相关信息|  
|----------------|---------|------------|  
|\_\_gc 结构或 \_\_gc 类|类|[class](../Topic/class%20\(C%23%20Reference\).md) 关键字|  
|\_\_value 结构或 \_\_value 类|struct|[struct](../Topic/struct%20\(C%23%20Reference\).md) 关键字|  
  
## 示例  
 在下面的示例中，将托管类 \(`X`\) 与通过托管指针操作的公共数据成员一起声明。  
  
```  
// keyword__gc.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
using namespace System;  
  
__gc class X {  
public:  
   int i;  
   int ReturnInt() { return 5; }  
};  
  
int main() {  
   // X is a __gc class, so px is a __gc pointer  
   X* px;  
   px = new X;   // creates a managed object of type X  
   Console::WriteLine(px->i);  
  
   px->i = 4;   // modifies X::i through px  
   Console::WriteLine(px->i);  
  
   int n = px->ReturnInt();   // calls X::ReturnInt through px  
   Console::WriteLine(n);  
}  
```  
  
## 输出  
  
```  
0  
4  
5  
```