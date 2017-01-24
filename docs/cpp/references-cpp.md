---
title: "引用 (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "声明, 引用"
  - "对象 [C++], 引用"
  - "引用"
  - "引用, 声明"
  - "引用, 到指针"
  - "引用对象, 声明符语法"
ms.assetid: 68156f7f-97a0-4b66-b26d-b25ade5e3bd8
caps.latest.revision: 12
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 引用 (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

与指针相似的是，引用将存储位于内存中其他位置的对象的地址。  与指针不同的是，初始化之后的引用无法引用不同的对象或设置为 null。  存在两种引用：左值引用（引用命名变量）和右值引用（引用[临时对象](../cpp/temporary-objects.md)）。  & 运算符表示左值引用，&& 运算符根据上下文表示右值引用或通用引用（右值引用或左值引用）。  
  
 可以通过以下语法声明引用：  
  
```  
[storage-class-specifiers] [cv-qualifiers] type-specifiers   
[ms-modifier] declarator [= expression];  
```  
  
 可以使用指定引用的任何有效声明符。  除非引用是对函数或数组类型的引用，否则应用以下简化语法：  
  
```  
[storage-class-specifiers] [cv-qualifiers] type-specifiers [& or &&]   
[cv-qualifiers] identifier [= expression];  
```  
  
 使用以下序列声明引用：  
  
 1.  声明说明符：  
  
-   可选存储类说明符。  
  
-   可选 **const** 和\/或 `volatile` 限定符。  
  
-   类型说明符：类型的名称。  
  
-   2.  声明符：  
  
-   可选的 Microsoft 专用修饰符。  有关详细信息，请参阅 [Microsoft 专用修饰符](../cpp/microsoft-specific-modifiers.md)。  
  
-   & 运算符和 && 运算符。  
  
-   可选 **const** 和\/或 `volatile` 限定符。  
  
-   标识符。  
  
 3.  可选初始值设定项。  
  
 指向数组和函数的指针的更复杂的声明符形式也适用于对数组和函数的引用，请参阅[指针](../cpp/pointers-cpp.md)和[声明符](http://msdn.microsoft.com/zh-cn/8a7b9b51-92bd-4ac0-b3fe-0c4abe771838)。  
  
 多个声明符和初始值设定项可能出现在一个声明说明符后面的逗号分隔的列表中。  例如:  
  
```  
int &i;   
int &i, &j;   
```  
  
 引用、指针和对象可以一起声明：  
  
```  
int &ref, *ptr, k;   
```  
  
 引用保留对象的地址，但语法行为与对象一样。  
  
 在下面的程序中，请注意对象的名称 `Today` 和对象的引用 `TodayRef` 可在程序中以相同的方式使用：  
  
## 示例  
  
```  
// references.cpp  
#include <stdio.h>  
struct S {  
   short i;  
};  
  
int main() {  
   S  s;   // Declare the object.  
   S& SRef = s;   // Declare the reference.  
   s.i = 3;  
  
   printf_s("%d\n", s.i);  
   printf_s("%d\n", SRef.i);  
  
   SRef.i = 4;  
   printf_s("%d\n", s.i);  
   printf_s("%d\n", SRef.i);  
}  
```  
  
  **3**  
**3**  
**4**  
**4**   
## 注释  
 本节中的主题：  
  
-   [引用类型函数参数](../cpp/reference-type-function-arguments.md)  
  
-   [引用类型函数返回](../cpp/reference-type-function-returns.md)  
  
-   [对指针的引用](../cpp/references-to-pointers.md)  
  
## 请参阅  
 [初始化引用](../misc/initializing-references.md)