---
title: "属性 (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "property_cpp"
  - "Property"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__declspec 关键字 [C++], 属性"
  - "属性 __declspec 关键字"
ms.assetid: f3b850ba-bf48-4df7-a1d6-8259d97309ce
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 属性 (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 此特性可应用于类或结构定义中的非静态“虚拟数据成员”。  编译器通过将这些“虚拟数据成员”的引用更改为函数调用来将其作为数据成员处理。  
  
## 语法  
  
```  
  
      __declspec( property( get=get_func_name ) ) declarator  
__declspec( property( put=put_func_name ) ) declarator  
__declspec( property( get=get_func_name, put=put_func_name ) ) declarator  
```  
  
## 备注  
 当编译器在成员选择运算符（“**.**”或“**\-\>**”）的右侧看到使用此特性声明的数据成员时，它会根据此类表达式是左值还是右值，将运算转换为 **get** 或 **put** 函数。  在更复杂的上下文中（如“`+=`”），可通过同时执行 **get** 和 **put** 来执行重写。  
  
 此特性还可用于类或结构定义中的空数组的声明。  例如：  
  
```  
__declspec(property(get=GetX, put=PutX)) int x[];  
```  
  
 上面的语句指示 `x[]` 可用于一个或多个数组索引。  在这种情况下，`i=p->x[a][b]` 将变为 `i=p->GetX(a, b)`，`p->x[a][b] = i` 将变为 `p->PutX(a, b, i);`  
  
 **结束 Microsoft 专用**  
  
## 示例  
  
```  
// declspec_property.cpp  
struct S {  
   int i;  
   void putprop(int j) {   
      i = j;  
   }  
  
   int getprop() {  
      return i;  
   }  
  
   __declspec(property(get = getprop, put = putprop)) int the_prop;  
};  
  
int main() {  
   S s;  
   s.the_prop = 5;  
   return s.the_prop;  
}  
```  
  
## 请参阅  
 [\_\_declspec](../cpp/declspec.md)   
 [C\+\+ 关键字](../cpp/keywords-cpp.md)